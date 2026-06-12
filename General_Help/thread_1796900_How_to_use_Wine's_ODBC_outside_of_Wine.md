---
title: "How to use Wine's ODBC outside of Wine"
date: 2011-07-04
forum: General Help
---

### Post by gunksta on 2011-07-04
I want to access data stored in .mdb files and and .accdb (Access) via ODBC on Linux. I am well aware that Linux lacks ODBC drivers for these files, unless I want to pay hundreds of dollars for the proprietary JDBC drivers. They work well, but I don't have the budget for these drivers. And, I think there is an alternative.

I installed Wine and using winetricks, I installed Microsoft's MDAC and JET binaries and few other things. Using this tweaked version of Wine, I was able to install Microsoft Office, including Access 2007. I can now use Wine to access the data in .mdb and .accdb files using Access, MDB Viewer and I can create ODBC connections to Access files.

What I would like to do is to link an ODBC connection, created using Wine to Ubuntu's ODBC system. Unfortunately, the Linux ODBC system is left unaware of the Wine drivers. Is there some way to get these two ODBC systems to talk? When I create a ODBC connection using Wine's ODBC tools, I can create connections to SQLite, which is interesting because I have the ODBC drivers for SQLite installed on Ubuntu, but not Wine. It appears that Wine can make use of Linux ODBC drivers, but I want to do the opposite.

Thoughts are appreciated.

---

### Post by SeijiSensei on 2011-07-04
Have you tried the [UnixODBC]("http://www.unixodbc.org/") drivers in the repositories?  I've only gone from Windows to Linux with ODBC, so I haven't given this a try, but a quick Google search suggests some people have gotten UnixODBC to work with Access.

---

### Post by gunksta on 2011-07-04
The EasySoft drivers listed on the unixodbc page work great. They also cost over 400 pounds. I can buy Office 2010 for that much and use Access directly via Wine. 

Thanks for the comment, but I'd prefer to find a way to use the Windows drivers, which work great via Wine, to connect to Linux.

---

