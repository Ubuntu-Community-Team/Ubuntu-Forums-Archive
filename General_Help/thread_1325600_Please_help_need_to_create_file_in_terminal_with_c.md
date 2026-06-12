---
title: "Please help need to create file in terminal with content..."
date: 2009-11-13
forum: General Help
---

### Post by ortaa23 on 2009-11-13
I need to do this for a bug workaround


Create file  /etc/pm/config.d/local with content:
 SUSPEND_MODULES="via_rhine"
 and try suspend/resume.


Ok, so I can create a file following the instructions here:


[http://linuxservertutorials.blogspot.com/2008/11/ubuntu-create-file-in-command-line.html](http://linuxservertutorials.blogspot.com/2008/11/ubuntu-create-file-in-command-line.html)


But then how do I give it content?? 



And finally, how do I suspend/resume? pm-suspend in Terminal? Then?


Thanks in advance.

---

### Post by Kelvin Gardiner on 2009-11-13
Linux as a number of command line text editors. I think the easiest to use is nano.

Have a look here: [https://help.ubuntu.com/community/Nano](https://help.ubuntu.com/community/Nano)

A file can be opened or created and open by typing nano FileName

---

### Post by ortaa23 on 2009-11-13
Hello thanks for replying.

So I type nano FileName in Terminal, Nano opens up with File: FileName. I write the content in the box, then Ctrl+o to save. Correct?

What does suspend/resume mean?

---

### Post by mo.reina on 2009-11-13
quick way to do it.  in the terminal type:

```
echo "SUSPEND_MODULES="via_rhine" > /etc/pm/config.d/local
```

---

### Post by audiomick on 2009-11-13
Hallo. This looks like a language problem

This
> **ortaa23 said:**
> 
Create file  /etc/pm/config.d/local with content:
 SUSPEND_MODULES="via_rhine"
 and try suspend/resume.

Means "create at file (presumably a text file created with gedit or whatever is your favorite) which is called 

local

and is in the folder

/etc/pm/config.d


thus the full path

/etc/pm/config.d/local

The text to be written in the text file "local" is:

SUSPEND_MODULES="via-rhine"


So you don't have to "give the file content" ;)

What it is all about is, as far as I can see, replacing or providing a new configuration file for something.

The suspend/resume thing is to stop the service or program that is giving you trouble, then start it again. This would cause the program to go and get the new config file when it starts up again. I don't know the commands for that of the top of my head. If you can't find them, just restart the computer....

---

### Post by ortaa23 on 2009-11-13
You are quite right, sir. I am new to this game.

Does mo.reina's instruction still apply?

Thanks.

---

### Post by ortaa23 on 2009-11-13
Sorry I am really tired and have been trying to fix this problem since 5 days ago. So my problem-fixing mind is a little strained.

I tried typing in "/etc/pm/config.d/local" into nano to open it but it did not find the file 

What does this mean? 

mo.reina's suggested command didn't seem to work.

Any help greatly appreciated.

---

### Post by ciscosurfer on 2009-11-13
> **ortaa23 said:**
> Sorry I am really tired and have been trying to fix this problem since 5 days ago. So my problem-fixing mind is a little strained.

I tried typing in "/etc/pm/config.d/local" into nano to open it but it did not find the file 

What does this mean? 

mo.reina's suggested command didn't seem to work.

Any help greatly appreciated.The **/etc/pm/config.d** directory is owned by root and mo.reina's use of quoting is slightly off as well. Use **sudo** to create the file, like this:```
sudo nano /etc/pm/config.d/local
```Copy or type the desired text into the newly created file, write out the file (save it), done.

---

### Post by mo.reina on 2009-11-13
sorry type, missed the ".  the command below should do it.  also, you'll need to become the superuser to do this:

```
sudo su
echo "SUSPEND_MODULES="via_rhine"" > /etc/pm/config.d/local
```

to check if the file is there, type 
```
cat /etc/pm/config.d/local
```

this is the output when i do the above commands on my system:

```
mo@mo-laptop:~$ sudo su
root@mo-laptop:/home/mo# echo "SUSPEND_MODULES="via_rhine"" > /etc/pm/config.d/local
root@mo-laptop:/home/mo# cat /etc/pm/config.d/local 
SUSPEND_MODULES=via_rhine
root@mo-laptop:/home/mo# 

```

*note: becoming the superuser is not recommended unless absolutely necessary.  i tried using sudo but it wouldn't let me write to the folder, so in this case, unless you change the permissions on the folder, you'll have to do it.

---

### Post by mo.reina on 2009-11-13
dude i must have missed my coffee this morning.  this is the correct code
```
echo "SUSPEND_MODULES=**\"via_rhine\"**" > /etc/pm/config.d/local
```

---

### Post by ortaa23 on 2009-11-13
Trying your corrected code...

---

### Post by ortaa23 on 2009-11-13
[FONT=Arial,Helvetica][SIZE=3]Hi there I just tried both your commands and the outputs were the same as yours on both occasions. After restarting the 'fix' hasn't worked. So either the command was still wrong or there's something unfixable about my computer. Since I am becoming increasingly pessimistic about this, I imagine that the latter is more likely.
[/SIZE][/FONT]

---

