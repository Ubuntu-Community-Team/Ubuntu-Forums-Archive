---
title: "Process Automatic Killing"
date: 2009-08-10
forum: General Help
---

### Post by premabodh on 2009-08-10
Hi All,

I have a JAVA application that runs fine. Now this application needed to be run every 5 minutes so I wrote a Shell Script and added to gnome schedular with an interval of 5 minutes.

The schedular is running fine and everything seems to be working perfectly.

Now the problem is that the schedular starts the process and does not kill the process and what happens is that after 1 hour I can see around 20 Java processes running and in overnight consumes the system processes. Since the Java application has database connections it ends up opening too many connections for database and blocks database access for other applications on same database and further schedular processes. We need to manually kill the older processes.

If I run this Java Application from within an IDE (Eclipse) the application runs fine and exits normally.

If I run schedular manually then also the process hangs and gives a message "Press Enter to exit"


Please let me know any workaround for this solution.

Thanks and Regards,
Vikash Anand.

:popcorn:

---

### Post by arky on 2009-08-10
Make sure you put in a 'kill -9 <pid>' at the end of the script. Or use killall <program-name>

---

### Post by premabodh on 2009-08-10
Hi arky,

Thanks for reply.

I cannot put killall <program-name> in the script as there are many other Java processes running. killall will also kill all other remaining processes (Java processes). 

Is there a way to get the process Id when the program is executed. Normally we do ps -A and kill process manually by using command "kill -9 <process number>".

Can something be done in script to know the process id and upon finish of java application we kill the process.:confused:

Thanks,
Vikash Anand.

---

### Post by arky on 2009-08-10
Look at 'exec' section Advanced Bash Programming guide. 

Create a child shell and later kill all processes under that shell.

Post your script so that others might understand what you are trying to do.

---

### Post by premabodh on 2009-08-10
Hi,

I have found the solution to the problem. What needs to be done is adding following line at the end of Shell Script code.

exit 0

Thanks,
Vikash
:guitar:

---

