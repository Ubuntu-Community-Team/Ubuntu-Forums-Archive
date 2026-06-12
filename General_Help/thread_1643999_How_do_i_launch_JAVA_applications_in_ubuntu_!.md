---
title: "How do i launch JAVA applications in ubuntu ?!"
date: 2010-12-12
forum: General Help
---

### Post by pavelexpertov on 2010-12-12
I tried to launch java files (.jar) by choosing a program Openjdk Java 6 runtime. Then it gives me an error that the file is not marked as executable. I know how to solve problem with wine by making a launcher with a command and path....but i dont know a command for java progrm... HELP!!!

---

### Post by Foxheadz on 2010-12-12
right click on the file click on properties
go to the permission tab and check the executable box

---

### Post by The Cog on 2010-12-12
I think the normal thing to do is to launch the jar file with a command like:
**java -jar filename.jar**
You might be able to convince nautilus to open it with something like
**java -jar %f** when you double-click a jar file by tinkering with the file's Open With settings.

P.S.
I don't think the jar file needs to be marked executable. It's not strictly executable at all as far as Linux is concerned, it's a data file containing java class files.

---

### Post by pavelexpertov on 2010-12-20
Thanx guys for help, but the first method worked perfectly :)but thanx for commands as well. However, how do u mange to put something under ur reply a little message?

---

### Post by Verbeck on 2010-12-20
> **pavelexpertov said:**
> Thanx guys for help, but the first method worked perfectly :)but thanx for commands as well. However, how do u mange to put something under ur reply a little message?
[http://ubuntuforums.org/profile.php?do=editsignature](http://ubuntuforums.org/profile.php?do=editsignature)

---

### Post by E.Fil on 2011-01-11
Hi,

I have a similar situation. There is this java app that I wanted to start from a launcher in the desktop. From the command line I can start it by running an .sh script that contains the following line

```
java -Xmx1024M -classpath "JavaUtils.jar:sqljdbc4.jar:log4j-1.2.15.jar:EFilCommons.jar:rsyntaxtextarea.jar:pg74.216.jdbc3.jar:ojdbc14.jar:hsqldb_1_8.jar:mysql-connector-java-5.1.13-bin.jar" ju.JavaUtils

```

I can't get the laucher to work on this app, neither by pointing the launcher to the .sh script or by inserting the entire command in the "command" option of the launcher. I double click the launcher and nothing happens.

Am I missing something here?

Thanks

---

### Post by veggen on 2011-01-11
What error are you getting? If it's ClassNotFoundException, then your classpath is bad. Try specifying the absolute paths e.g \path\to\JavaUtils.jar or if your launcher points to the sh script, try adding a pwd statement at the top of it to see what the current path is when you launch it and adjust the classpath accordingly.

---

### Post by E.Fil on 2011-01-11
Hi,

I don't get any error. No command line shows up or anything else for that matter...

I changed the .sh script as follows:

```
pwd > /ju.log;java -Xmx1024M -classpath "JavaUtils.jar:sqljdbc4.jar:log4j-1.2.15.jar:EFilCommons.jar:rsyntaxtextarea.jar:pg74.216.jdbc3.jar:ojdbc14.jar:hsqldb_1_8.jar:mysql-connector-java-5.1.13-bin.jar" ju.JavaUtils >> /ju.log

```

this should have created the /ju.log file with the output, but no file is created...

---

### Post by E.Fil on 2011-01-11
Hi,

I fixed it. In my previous message the file did not get created because there was no permission for it.

I then started getting class not found exceptions and the pwd command was pointing to the user's home folder.

At first I just assumed that the laucher would launch it's target from whatever directory the target was in (it made sense to me...).

I changed the .sh script as follows (added the cd command to move to the correct path) and it works now.
```
cd /opt/JavaUtils_dist; java -Xmx1024M -classpath "JavaUtils.jar:sqljdbc4.jar:log4j-1.2.15.jar:EFilCommons.jar:rsyntaxtextarea.jar:pg74.216.jdbc3.jar:ojdbc14.jar:hsqldb_1_8.jar:mysql-connector-java-5.1.13-bin.jar" ju.JavaUtils >> ju.log

```

Thank you for your help :D
E.Fil

---

