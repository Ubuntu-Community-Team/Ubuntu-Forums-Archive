---
title: "What is cron and how to use it in scripting for storeBackup ??"
date: 2010-10-13
forum: General Help
---

### Post by Robert R on 2010-10-13
Hi I have previously looked at store backup and can now write the  commands at a terminal to make backups to my external hard disk. I would  like to know how to create a "script" if that is the correct  terminology and also how to run it..

like a .bat file in windows i dont know what its called in linux. 
 
I heard mention of **cron **in the forums but do i need this to accomplish the above tasks
?

---

### Post by andrewc6l on 2010-10-13
cron is a utility which lets you run programs at certain times. If you just want to write a script that you can invoke (similar to a DOS batch file), here is a good tutorial:

[http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)

You will probably need to put "sudo" in front of the chmod command in the tutorial... it assumes you're running as root.

---

### Post by Robert R on 2010-10-13
> If you just want to write a script that you can invoke (similar to a DOS batch file), here is a good tutorial:

Thanks this does seem helpful but i mean more specific to the storeBackup program, or am i missing the point. I have some of the script already written just needs a little modification. 
What i need to know is what format to save it in so it will run automatically when i double click or open it from the terminal??

---

### Post by andrewc6l on 2010-10-15
If you have an existing script called myscript, then you can:
```
sudo chmod 755 myscript

```
This will allow everyone to read/execute it, but only you to edit it. You might instead want to use 750 (which will allow only users in the same group to read/execute) or 700 (which will allow only you to edit/execute).

Your script should begin with something like:
#!/bin/sh -
or possibly another valid program, depending on what kind of script it is. At any rate, the file after the ! needs to be on your system and executable.

Once that's done, you can execute the script from the command line... and I would expect from most GUI file system browsers as well.

---

### Post by Robert R on 2010-10-20
OK Thanks i understand but one more question. when i save the script (which would start off *** a text file ) what format do i save it in.??

---

### Post by andrewc6l on 2010-10-22
Linux scripts are just plain text files. As long as you don't use non-ASCII characters, you can just save as text. Extensions are also irrelevant under Linux - just name it whatever you want.

---

### Post by matt_symes on 2010-10-22
Hi

Maybe this will help as well

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Kind regards

---

### Post by trikster_x on 2010-10-22
When you create a script, although they will run fine as a normal text file, it is always a good idea to give it the **.sh** extension, so you don't get an old script mixed up with a normal text file when you try to open it.  Just make sure you run in terminal

```
chmod -774 /path/to/your/script
```

or right click on the file, open the properties, and check run as executable in the permissions tab.

[http://www.unixgeeks.org/security/newbie/unix/cron-1.html]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html")
[http://adminschoice.com/crontab-quick-reference]("http://adminschoice.com/crontab-quick-reference")
[https://help.ubuntu.com/community/CronHowto]("https://help.ubuntu.com/community/CronHowto")

These are all good sites for reference on how to use crontab.  crontab is probably the best option for scheduling scripts.

---

### Post by Robert R on 2010-10-22
Thanks for all the info so far its coming along pretty ok. 
Ill post it for other ppls reference when its done. 
I'm new to ubuntu though so might take a while but thanks again for the info guys . :)

---

