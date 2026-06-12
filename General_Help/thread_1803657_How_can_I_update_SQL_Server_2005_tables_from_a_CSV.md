---
title: "How can I update SQL Server 2005 tables from a CSV?"
date: 2011-07-13
forum: General Help
---

### Post by Maheriano on 2011-07-13
I have a website where users can enter reviews on products and it all goes into a SQL Server 2005 database. I need to write a quick and dirty script that a business user can use to pull all unmoderated reviews into an external file, moderate them, then update the database with the new values in the file.

I'm basically taking the rows out of the table, updating some cells and uploading it again. I can do this now but it adds all rows as new rows, I need to update existing rows. I've already tried BCP and BULK INSERT, neither have capability to update it seems.

---

