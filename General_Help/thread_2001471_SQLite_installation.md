---
title: "SQLite installation"
date: 2012-06-10
forum: General Help
---

### Post by Deaf Smith on 2012-06-10
Guys,

I did the sudo to install Sqllite but.. how do I get it to run or show an icon on the desktop so I can use it.

Thanks,

Deaf

---

### Post by papibe on 2012-06-10
Hi Deaf Smith.

The package called 'sqlite' is for a command line interface. Is that what your are looking for? If so, open a terminal and run:
```
sqlite
```

I would recommend taking a look at a graphical alternative called: sqlitebrowser. To install it:
```
sudo apt-get install sqlitebrowser
```
Then, it would be available on the dashboard (or the menu on previous version of Ubuntu).

Does that help?  Tell us how it goes.
Regards.

---

### Post by Deaf Smith on 2012-06-11
papibe,
 
I'll try it tonight (I'm at work now and here it's all a MS shop!) 
 
I would much perfer a GUI style interface than just a command line.
 
There are several people here with me that want to learn SQL as the new software we are getting will do away with all the old COBOL (yes cobol!) 1/2 of the shop is MVS/CICS and the other half servers. Some here have never really done much work on servers. We will be training on Crystal Report Writer and part of it will be SQL.
 
I have Ubuntu on my desktop at home and on my home training PC (a HP 'alternate OS' pc with 64 bit) I have Fredora 14 so I can train on Red Hat. Plus my old 32 bit system is here beside me and it has CentoOS.
 
Self taught I am!
 
Thanks again,
 
Deaf

---

### Post by oldfred on 2012-06-11
I have used sqlitebrowser and also like sqliteman. But you need to know some sql to use them.

Years ago when I was working, Company converted all history to an MS SQL server and wanted us to use Crystal Reports. But I had been using MS Access as my replacement for dBase. Part of that was a desire to learn SQL and MS Access let you create the query and then you could change modes and see the SQL. I did have issues with the differences between MS Access SQL, MS SQL Server SQL and the AS/400 SQL, but learned enough to have some knowledge of each.  

Old version of Crystal Reports created nice reports but made it difficult to change a parameter if you wanted to reuse report. I used to run a lot of monthly reports and I was able to use MS Access as the front end to the SQL server and create a query, copy SQL into the code behind a form and dynamically change date range so report ran automatically.

Have not found that same functionality in Linux but am teaching myself python, gpt & qt, and pdf or HTML for reporting. But now retired I have no push to finalize how to do all that now.

---

### Post by The Cog on 2012-06-11
The command-line client is sqlite3, not sqlite.

There is a plug-in for firefox called sqlite-manager that gives a quite good GUI for editing sqlite files. Its only connection to firefox is that it uses the firefox rendering engine - it's not a web based app. You find it in the firefox tools menu after installing.

---

### Post by Deaf Smith on 2012-06-11
Ok, I ran  the command 'sudo apt-get install sqlitebrowser' and it installed.

So how do  I get the GUI to come up (or for that matter for sqlite3?) I see no icon on the desktop.

I do see I have the SQLite Manager working fine on Firefox. Looks like the SQLite at work!

Will that do all I need?

I got SQLite to work on my PC at work (MS version) today and did some database creating and loading (for those who know what I'm talking about I made a ICD9 and ICD10 table to convert ICD9 to ICD10 descriptions.)

 I'll learn alot there tomorrow and do more here at home!

Thanks,

Deaf

---

### Post by papibe on 2012-06-11
> **Deaf Smith said:**
> So how do  I get the GUI to come up?

In Ubuntu 11+ search for sql on the dashboard.

In 10.04 it will be on 'Applications -> Programming -> SQLite database browser'.

From almost any distro using the terminal:
```
sqlitebrowser
```

I hope it helps.
Regards.

---

