Dashboard: In the dashboard template, I wanted to display Hi User because I wanted to give the user a warm welcome to the page. Right underneath, I displayed the user's North Star using <h1>. Although I tried using Bootstrap's grid functionality, I found that the top-to-bottom layout is much more intuitive in this case. I chose to implement a select dropdown so that users could choose from a list of available categories that they have made.
All of the users "Categories" are listed below the "Enter Task" feature as headings, with each task listed underneath its respective category. I made this design decision because it seems the most intuitive and effective way to illustrate how "North Star" is really just a tree of priorities that trickle down into branches as Constellation goal categories and tasks as leaves. To do this, I created a nested for loop that first iterates through the categories of the user and then iterates though the tasks of each category and prints out that task and it's creation date. I implemented the backend of the nested for loop feature by creating a for loop in app.py that iterates through each category in a user's categories and inserts the category's tasks, taking that category's id and the user id in the query. These tasks of each category are stored in a list of dictionaries. This way, the template is able to access the data and iterate through it.

Constellation: In constellations, I utilized Bootstrap's grid capabilities because this page has less of a necessity to portray the flow of creations as top down but rather left to right. I want the user experience to feel like you're setting a goal into motion. Therefore, I set the constellation creation form and the Constellation view on separate columns of the same div row. I referred to https://www.youtube.com/watch?v=Wqu-d_b3K-0&t=372s to figure out how to do this.

Task View: In task view, I implemented a simple jinja for loop table and used Bootstrap's dynamic table feature. This table shows the creation date and all tasks regardless of category because I would like the user to see their progression of priorities over time.

Category Removal and Task Removal: These were each designed as simple forms with a drop down select and a button to remove the category/task. In both category removal and task removal, I first used a db.execute to find the id of the user's category/task being deleted using the inputted category/task from the select dropdown in the template. Then, to delete the category/task, I ran a DELETE SQL query that deleted the category/task row using the id we found earlier. I chose to DELETE by id and not category_name or task because there can be multiple categories and tasks of the same name. In Category Remover, I made sure to also delete tasks with the same category id as the category that's being deleted. That way, there won't be any dangling tasks in the dashboard.
I originally tried to implement a more complex removal function with delete buttons inside each row of Task View, but I was unable to implement it. The code for that failed attempt is including in the comments of task_view() in app.py. In the future, I would like to debug my old implementation, or find a way to use node.js, Javascript, and events to implement delete buttons and check marks.