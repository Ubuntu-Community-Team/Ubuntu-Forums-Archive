---
title: "MoneyDance"
date: 2006-04-28
forum: General Help
---

### Post by cssutto on 2006-04-28
I have downloaded moneydance and have the file in two forms on my desktop, but I don't know enough to be able to install it.

one is a tar.gz and the other .sh.

I would apapreciate any help.

Is there a way to use the package manager (Synaptic, Ubuntu 5.10) to download packages from this type web site?

CSSJR

---

### Post by yager on 2006-04-29
[QUOTE=cssutto]I have downloaded moneydance and have the file in two forms on my desktop, but I don't know enough to be able to install it.

one is a tar.gz and the other .sh.

I would apapreciate any help.

Is there a way to use the package manager (Synaptic, Ubuntu 5.10) to download packages from this type web site?

CSSJR[/QUOTE]

Okay, I downloaded the .sh file and successfully installed it.  Here were the steps.

After downloading to my Desktop, I opened up a terminal window.

```
ubuntu:~/Desktop$ chmod +x moneydance_linux_x86.sh
ubuntu:~/Desktop$ sudo moneydance_linux_x86.sh

```

This then ran the installer routine and put the program into the /opt/moneydance directory.

To execute the program, watch for a capital letter at the start of the program name.
 ```
ubuntu:/$ Moneydance

```
I could not find if it had added itself to the menu structure so you may need to create the menu yourself.

---

### Post by cssutto on 2006-04-29
This is what I got for the first command:

d:~$ ubuntu:~/Desktop$ chmod +x moneydance_linux_x86.sh
bash: ubuntu:~/Desktop$: No such file or directory

And it is on my desktop for all to see and in properties it show that it is 3.0M so it should all be there.

CSSJR

---

### Post by The J on 2006-04-29
I believe when you run a command, you always have to specify the directory of the command as well (unless it's in /usr/bin).  So to run Moneydance, you'd run **./Moneydance**.  Note that the ./ means "current working directory".

---

### Post by lotheac on 2006-04-29
[QUOTE=cssutto]This is what I got for the first command:

d:~$ ubuntu:~/Desktop$ chmod +x moneydance_linux_x86.sh
bash: ubuntu:~/Desktop$: No such file or directory

And it is on my desktop for all to see and in properties it show that it is 3.0M so it should all be there.

CSSJR[/QUOTE]

You're only supposed to type in the part after the "$" sign. What's before it tells you the hostname "ubuntu" and which directory you need to be in (~/Desktop here, to change there you can use "cd ~/Desktop"). The ~ character means the current user's home directory.

[quote=The J]I believe when you run a command, you always have to specify the directory of the command as well (unless it's in /usr/bin). So to run Moneydance, you'd run ./Moneydance. Note that the ./ means "current working directory".[/quote]

You need not specify the binary's location if it or a symlink to it is in your PATH (defined in /etc/environment and/or ~/.bashrc). As this program had an installer, it has probably placed the necessary links in a directory in your PATH, so you wouldn't do "./Moneydance".

---

### Post by cssutto on 2006-04-29
The "d;" was not entered on the command line.

In copying the line to show what I had entered, I accidentally copied the last letter of the machine name, the last word of which is "thinkpad".

So the command line actually began with ubuntu.

All else is noted, but does not work as advertised.

Ignore for a day or so and give me time to download a new copy and try it.

CSSJR

---

### Post by cstudent on 2006-04-29
I use Moneydance. To install it, download the file moneydance_linux_x86.sh (assuming you have a x86 machine).

Open a terminal and navigate to where the file is stored. 

Enter the following command:
```

sudo sh moneydance_linux_x86.sh

```

A dialog box will pop up and walk you through the install. I placed my moneydance in the /opt directory. I have an icon in my applications>office menu, but I can't remember if it placed it there automatically. If it doesn't just let me know. I can help you fix that too.

---

### Post by lotheac on 2006-04-29
[QUOTE=cssutto]The "d;" was not entered on the command line.

In copying the line to show what I had entered, I accidentally copied the last letter of the machine name, the last word of which is "thinkpad".

So the command line actually began with ubuntu.

All else is noted, but does not work as advertised.

Ignore for a day or so and give me time to download a new copy and try it.

CSSJR[/QUOTE]

Well I figured that part was accidental, but you're not supposed to type in "ubuntu:~/Desktop$", rather just the part after that (starting from 'chmod').

---

### Post by cssutto on 2006-04-29
The real problem was that in trying to keep from making a mistake, I copied the command line as given.

There were two mistakes.  You pointed out one of them, which was a biggie.

But them I just realized that the correct file name is x86wj

That wj was also a killer.

It is installed now.

Thank you.

CSSJR

---

### Post by cssutto on 2006-04-29
Well, I am stumped again.

I have the Moneydance files backed up on an exteral hard drive.

Looking at the file properties, it shows that it is located at /media/Local Disk/Sunday/Program Files/Moneydance

I was able to drag a copy of it to the desktop and load it all, but I can not figure out how to copy it to the Monedance folder, which is in /usr/local/moneydance.

I get the permission not allowed message when I try to drag it, but when I try to change the permission, I can't work my way through all of those file levels without getting stopped by the "  " is not a file or directory.

I can use chmod for the same reason.  I can't follow the directory trail.

Moneydance itself is loaded and working, but I need to get the data files copied.

CSSJR

---

### Post by cssutto on 2006-04-29
I can use chmod for the same reason. I can't follow the directory trail.

Sorry.

Should have been "I can not use chmod....

---

### Post by cssutto on 2006-04-29
I finally got this far.

Password:
claude69694@mythinkpad:/usr/local$ sudo chmod +rwx moneydance
claude69694@mythinkpad:/usr/local$

But the moneydance folder or directory still will not let me put the data file in it.

When I look at its properties, I see that root owns it and I am not allowed to wrie to it.

CSSJR

---

### Post by static chaser on 2006-06-19
I used this thread to get my Moneydance installed.  I had used it in XP and my key
was still good so I downloaded a Linux version and installed it. I even got it to backup in my home folder. Thanks for all the help.

---

### Post by Corey on 2006-06-21
Moneydance looks like exactly the tool I need. I'd gladly pay $30 for a native linux quicken replacement. I can't get the trial installed though :( 

```

~/Desktop$ sudo sh moneydance_linux_x86.sh
Starting Installer ...
java.lang.NoClassDefFoundError: javax.swing.JOptionPane
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.install4j.runtime.installer.Installer.reportExeption(Unknown Source)
   at com.install4j.runtime.installer.Installer.main(Unknown Source)
   at java.lang.reflect.Method.invoke(libgcj.so.7)
   at com.exe4j.runtime.LauncherEngine.launch(Unknown Source)
   at com.install4j.runtime.Launcher.main(Unknown Source)

```

---

### Post by static chaser on 2006-06-21
I had to download the version with java and install that package. For some reason their is an issue with the previously installed java. Then had to do the chmod to be able to write to the monedance folder.  I installed by using sudo sh moneydance_linux_x86wj.sh and then followed the instructions and it installed fine.

---

### Post by beameup on 2006-06-24
It doesn't like the GNU version of Java that comes with Ubuntu. You have to install Sun Java, then make it default. You can grab that from Add/Remove. 
Then you can install Moneydance without Java. I've been messing with it and finally got them working together.


As far as the install locations, would it be better to install it in the Home folder?

---

### Post by radagast2 on 2006-06-25
I had the same install problem as Corey, and beameup's suggestion on installing Sun's java and then making it default did the trick.  To make Sun's java default, all you need to do is run the command

> sudo update-alternatives --config java

and select Sun's java from the list.  For more, see [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java).

---

### Post by static chaser on 2006-06-25
Moneydance installed itself in my usr/local folder. I have the backup go to my home folder so I can slap it into a thumb drive easily. Ive had enough hard drives/os go wierd on me to lose my data.

---

### Post by beameup on 2006-06-26
Sorry about that radagast2, I was supposed to post the command too. Thanks. ](*,) 

Static Chaser, I'm asking about forcing the installer to load it where I want it to go. My thinking is loading it in the Home folder would be fine unless you have a shared machine. Of course, if you change the permissions on the usr/local/Moneydance files and folders, then that pretty much does the same thing.

---

### Post by static chaser on 2006-06-27
beameup, i didn't try to install md in another folder. i'm the only one that uses my computer except for 9 yr old grandaughter. she uses it for school work and some internet games. i think you would still have to do chmod to let whoever use md.

---

### Post by Al3xanR0 on 2006-06-28
Have you tried [Grisbi]("http://www.grisbi.org/")? It is a great alternative to GNUcash and Moneydance, and should be available in apt-sources.

---

### Post by bmc5311 on 2008-01-19
> **yager said:**
> Okay, I downloaded the .sh file and successfully installed it.  Here were the steps.

After downloading to my Desktop, I opened up a terminal window.

```
ubuntu:~/Desktop$ chmod +x moneydance_linux_x86.sh
ubuntu:~/Desktop$ sudo moneydance_linux_x86.sh

```

This then ran the installer routine and put the program into the /opt/moneydance directory.

To execute the program, watch for a capital letter at the start of the program name.
 ```
ubuntu:/$ Moneydance

```
I could not find if it had added itself to the menu structure so you may need to create the menu yourself.

Was having the same problem - found your post.  Thanks, all worked, all is well.

---

