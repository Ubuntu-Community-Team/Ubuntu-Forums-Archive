---
title: "SQL Server on XP-SP3 installed on Virtual Machine"
date: 2010-06-20
forum: General Help
---

### Post by multisystem on 2010-06-20
I have Ubuntu 10.04, and XP-SP3 installed on VirtualBox.

I've installed SQL Server 2005, but when I open it, It asks me for Server Name that is missing. Server Name is usually provided automatically when I installed MSSQL on another machines, but it's missing when I installed it on VirtualBox.

Anyway, I have written it manually. It's usually "ComputerName/SQLEXPRESS", but this error occurred.

```

An error has occurred while establishing a connection to the server. When connecting to SQL Server 2005, this failure may be caused by the fact that under the default settings SQL Server does not allow remote connections. (provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (Microsoft SQL Server, Error: 53)

```I've searched a lot, but all workarounds don't solve this problem.

Untill I found a thread talking about disabling firewall on host machine.

Is that true? 
If yes, please tell me how.
If no, please help me with this problem.

Very sorry for long thread.
Thanks very much

---

### Post by multisystem on 2010-06-20
Please any help :(

---

### Post by Roly25 on 2010-06-20
Have you tried Installing MS SQL Server 2005 Express natively on your Ubuntu machine using Wine or Crossover Office.  It would run more efficiently than using a Virtual Machine and Windows XP.  Code Weavers offer a 30 day trial of Crossover Office on there website?

Roland

---

### Post by multisystem on 2010-06-20
The problem is that I need to create database to connect it to C#.

Since I can't run Visual Studio efficiently on Ubuntu, I prefer to use SQL Server on XP instead.

---

### Post by multisystem on 2010-06-20
Solved :D

The solution
[http://blog.sqlauthority.com/2007/06/10/sql-server-fix-error-an-error-has-occurred-while-establishing-a-connect-to-the-server-solution-with-images/](http://blog.sqlauthority.com/2007/06/10/sql-server-fix-error-an-error-has-occurred-while-establishing-a-connect-to-the-server-solution-with-images/)

the problem is not with firewall

Thanks very much

---

