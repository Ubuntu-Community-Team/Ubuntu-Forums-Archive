---
title: "Hello, Ubuntu/Linux Newbie"
date: 2011-07-16
forum: General Help
---

### Post by Kartik10 on 2011-07-16
Hello all,

I recently installed Ubuntu 11.04 64bit to run along Winxp in a dual boot format. I have heard many good things about Ubuntu but am using it for the first time. Apologies for creating a new thread for my questions.

I have used a ntfs partition of 30GB for Ubuntu. During the installation part i was asked for the size and i gave 8 GB, i read that this was recommended. There are quite a few things i would like to know. 

1. What's the difference between Ubuntu software center & Synaptic software manager?

2. Can you do everything easily via the GUI?

3. My Nvidia 8800 GT works on 1440x900 on my win xp OS. Here it doesn't seem to get to that. Additional drivers window says that 173 version is active but not in use.

4. Where do all the updates/new softwares/ drivers etc get installed? I mean the path. Like in Xp i can give a path for the installation. Can i do that in here?

5. I want to install GNS 3 which is a routing simulator and have heard that Ubuntu is very stable for it.

6. How can i get desktop icons on the desktop?

7. What's the use of 4 workspaces? I mean why is it used and what are the advantages.

Apologies for asking so many questions. I tired searching the Internet but most of them just so confusing that it feels to difficult and am afraid i might break something.  Plus most of the commands are in cli that i am not able to grasp. 

Thanks in advance and apologies if i have created a thread under the wrong forum.

---

### Post by howefield on 2011-07-16
Thread moved to "*General Help*"

---

### Post by oldos2er on 2011-07-16
Did you do a Wubi install, or install Ubuntu into its own partition? It's not really clear from your description.

Synaptic Package Manager is more advanced than Software Center, and shows much info that Software Center hides from you.

You can use a GUI for nearly everything if that's what you're comfortable with, however for troubleshooting, repetitive tasks, etc., the terminal is the place to be. 

The video driver 'active but not in use' may be this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493)

In Linux the system handles where in the filesystem software is installed, normally these are fixed. [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

I'll let someone else handle the Unity questions, because I have no knowledge of it.

---

### Post by Kartik10 on 2011-07-16
> **oldos2er said:**
> Did you do a Wubi install, or install Ubuntu into its own partition? It's not really clear from your description.

Synaptic Package Manager is more advanced than Software Center, and shows much info that Software Center hides from you.

You can use a GUI for nearly everything if that's what you're comfortable with, however for troubleshooting, repetitive tasks, etc., the terminal is the place to be. 

The video driver 'active but not in use' may be this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493)

In Linux the system handles where in the filesystem software is installed, normally these are fixed. [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

I'll let someone else handle the Unity questions, because I have no knowledge of it.

Oldos2er, i did a Wubi install. Like i downloaded it on XP, ran it. Rebooted the machine and installed Ubuntu after that. Now Ubuntu is running on D while XP is running on C.

So all softwares that ubuntu install is always on it's own partition? I can't go and select a path to install something on another drive?

Thanks for your help, will have a look at the bug link and the wiki one too.

There's a strange feeling of goodness though, if i manage to learn the way linux operates then i can kiss windows goodbye.

---

### Post by oldos2er on 2011-07-16
If you installed Ubuntu to its on partition, that is not Wubi. Wubi installs it to a file inside an already existing NTFS partition. [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

One way to control where Linux installs software is to setup /usr, /etc,/ /var or any other folder on their own partitions; but that's not an exercise I would recommend to someone new.

---

### Post by mendhak on 2011-07-16
> 
1. What's the difference between Ubuntu software center & Synaptic software manager?


Same software, but the software center has better presentation, and I think that the Synaptic package manager will be dropped in later versions of Ubuntu. 

> 
2. Can you do everything easily via the GUI?


There are times when you will need to work with the terminal. It depends on what you want to do of course.  It's very possible that everything you do want to do already has a GUI application for it.  All I can say is, be open to the idea of using the terminal, you'll find a lot of tutorials that teach you to tweak certain aspects of the OS will simply do it via the terminal as it's a one-liner.

> 
3. My Nvidia 8800 GT works on 1440x900 on my win xp OS. Here it doesn't seem to get to that. Additional drivers window says that 173 version is active but not in use.


What is the maximum resolution you can get to now?  I was using an 8800GT until this morning and I had the additional drivers window, it had a 173 driver and it was 'green'.  How do you know it's not in use?

> 
4. Where do all the updates/new softwares/ drivers etc get installed? I mean the path. Like in Xp i can give a path for the installation. Can i do that in here?


Ah, this one had me puzzled for a while too.  Basically, there's a different mindset.  Most applications go to /usr/bin, libraries go to other folders, but these applications then store their settings in /home/Kartik10.  The idea being that you can easily reinstall your applications at any time from the package manager, the settings will still be there. 

> 
6. How can i get desktop icons on the desktop?


Which desktop icons?  If you're trying to create shortcuts, right click the desktop and there should be an option to 'create launcher'. 

> 
7. What's the use of 4 workspaces? I mean why is it used and what are the advantages.

If you have a lot of windows open, you can group them together.  So I could have my music application open in one workspace, then I can have Gimp and a photo viewer in a second workspace, and I could have a document/spreadsheet open in a third.  Use it however you want.  I found that the single-workspace mindset I use in Windows still sticks with me when I use Ubuntu and I have to make a conscious effort to get myself to use workspaces instead.  It's a personal preference.  Try it and see how you feel.

> 
Apologies for asking so many questions. I tired searching the Internet but most of them just so confusing that it feels to difficult and am afraid i might break something.  Plus most of the commands are in cli that i am not able to grasp. 

Thanks in advance and apologies if i have created a thread under the wrong forum.

Keep asking questions, best way to learn.

---

### Post by grahammechanical on 2011-07-16
Some of us are very competent with using the Command Line or terminal. So, they often give advice by suggesting that the person run a few commands. The information provided by these commands is useful provided you know what it all means. Some people find it quicker to suggest commands than to explain how to find a GUI utility and what to do with it. This is just two different styles of working.

Ubuntu is a fully functional operating system with a Graphical User Interface as standard. It still allows those who want to do things through the command line to do so. I rarely use it. Except to test out the commands that others are suggesting as a means of learning.

Synaptic and Software Centre are both ways of installing and uninstalling software over the Internet. The software centre is better looking and does not require much knowledge of what you are doing or an understanding of technical terms. It also allows the possibility of purchasing software which cannot be done through synaptic.

Linux keeps a separation between the files that a program uses to load and its user settings and configuration information. Bits of the program will be put in different folders located under File System. The files that the program uses to configure itself to the way that you have chosen are kept in hidden files in your home folder. We do not have a choice of where to install the program. The installation process takes care of it and we never know or need to know.

Regards.

---

