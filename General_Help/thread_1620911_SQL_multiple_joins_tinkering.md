---
title: "SQL multiple joins tinkering"
date: 2010-11-13
forum: General Help
---

### Post by J V on 2010-11-13
I have 3 tables I'm attempting to join, I want to get a list of employees and projects, including listing any employees with no projects, or any projects with no-one working on them... 

For clarity, I don't want it to return anything from "Assignment", it's just used to align the employees with the projects.

I setup a test DB /w phpmyadmin to try this out...
```
Employee1:
EMP_LNAME
EMP_FNAME
EMP_CODE
Assignment:
EMP_CODE
PROJ_CODE
Project:
PROJ_CODE
PROJ_NAME
```In this, the RIGHT JOIN works, so I see the project without anyone assigned to it, but the LEFT JOIN doesn't work, so I can't see the employee that has no project assigned...```
SELECT EMP_LNAME, EMP_FNAME, Project.PROJ_NAME
FROM Employee1
LEFT JOIN Assignment ON Employee1.EMP_CODE = Assignment.EMP_CODE
RIGHT JOIN Project ON Assignment.PROJ_CODE = Project.PROJ_CODE
ORDER BY Employee1.EMP_LNAME
```

---

