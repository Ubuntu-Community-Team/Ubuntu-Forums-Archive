---
title: "Getting optimized?"
date: 2011-06-18
forum: General Help
---

### Post by L a r r y on 2011-06-18
Hi,
I have been running Ubuntu now for a number of years, yet I am still no expert (as you know, that is a former drip under high pressure!) and I am not really familiar with how to get the most out of my computer in Linux.

I know that Linux runs on scripts, and these can be edited in a simple test editor,

I have a licensed copy of Windows XP Professional from before the time that I dived into Linux and settled on Ubuntu 6.06 at the time.

If I have a problem on my Windows computer, I can run HijackThis and generate a log of all the processes running on the system, submit it to a help forum, and get suggestions on how to proceed.

I don't really know the layout of Linux like I do Windows:  

The operating system is in typically the Windows folder, the programs install into the Program Files folder, and my home is in this ridiculously long file path called "Documents and Settings" (/home in Linux).  There are %ENVIRONMENT% variables in Windows that tell software just where the Program Files folder is, and where to find the OS and where to find the active user's home account.

I know that folders and directories are one and the same in both operating systems, and am familiar with the directory hierarchy of the filesystem.  I have worked with the Radio Shack Color Computer 2, and with MS-DOS since I was given an 8088 processor-based computer.

So my question is, if I want to ask for help and submit the equivalent of a HijackThis log, which is probably built right in to the Ubuntu OS, where do I start?

Before I got into Linux, everything was on a hard drive, and drive C was a partition on "this" physical drive...... but where is "/"?  Of course, now I know the answer to that question!  It is in whatever partition I chose at the time of installation if I made the choice, but it sure had me buffaloed for a long time!

I want to seek assistance on just how to go about speeding things up, getting rid of a bottleneck that exists because a script is waiting on something that doesn't exist or that is slow to respond for whatever reason, something is being a resource hog or whatever.

In Windows, I can open the Properties on an icon and, say I want to find a different icon, I can select the icon and see what dll file or exe file or which standalone ico file is providing the current icon, and I can navigate around the filesystem to find a different one.  In Ubuntu, I am always opened to my user home folder with no clue to where the present icon is to be found, so if I do change it, I don't know where to go to find the original.

In Windows I can open an "open with..." dialog that puts me in Program Files, but in Ubuntu I am put in the user home folder just as I was with the icon search.  

So since I don't know my way around as well as I should, I have not a clue where to begin.

I'm not trying to say that Windows is better than Ubuntu, but there are some common-sense things done there that I wish was carried over to here, because Linux is just a more secure operating system.

For instance, if I open an email in Windows, a script can run without my consent, but here I have to even give Windows executables permission under wine to execute by setting the permission flag.

In May of 2011, I downloaded a video chat program from oovoo.com called ooVoo, and ran it on my Windows computer.  It installed itself on my system and THEN presented me with its EULA which I carefully read, and did not agree to.  I exited the installer using the X in the corner of the window, and up came the sign-in window.  I closed it, and went into Add/Remove Software in the control panel, and first removed the ooVoo Toolbar.  Up came Internet Explorer with a new home page that the license terms said I must accept if I blow away the Toolbar.  I then closed it and blew away the program and cleaned up my Registry, then restarted Windows.  I was then presented with the fact that my admin password was changed without my authorization, and I could not restart Windows.  I have a project due tomorrow, so I had to pay a friend $50 to get my computer back in order.  He used some Linux-based scripts to blow away my Windows password and had to disable System Restore and clean up a bunch of stuff.  Next day I had my computer back in time for me to do my project.

Sorry for this long post, and thank you for reading this far!  Basically, what would I submit in the form of a log that would let someone review my system and give suggestions?  Tutorial links that may help me to better understand the lay of the land?  I am hoping this thread may be useful to others new to Ubuntu.

---

### Post by wildmanne39 on 2011-06-18
Hi, for starters you can open log file viewer and see all your logs your self, it takes a lot of looking and studying the logs to understand what is going on. If you post a log please post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by L a r r y on 2011-06-18
I found the log viewer in my System > Administration menu, and first thing it reported was that it could not open all of these files:

/var/log/user.log.0: Error stating file '/var/log/user.log.0': No such file or directory
/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/btmp.1: Error stating file '/var/log/btmp.1': No such file or directory

I have some of these log files without a ."number" extension when I go into the /var/logs folder.

Closing that yellow box, I have a lot of data here, which looks like I need to do a sudo apt-get install____ according to my boot-strap log which reads in part:
```

dpkg: regarding .../base-files_5ubuntu4_i386.deb containing base-files, pre-dependency problem:
 base-files pre-depends on awk
  awk is not installed.
dpkg: warning - ignoring pre-dependency problem !
(Reading database ... 0 files and directories currently installed.)

```

And it's nice to see that I don't have to upper-case the code tag to make that work.... I always thought I had to make it upper-case.

So thank you for getting me off on a start here, **wildmanne39**!

Following my missing installs I will restart and take a new look at the bootstrap log.

---

### Post by L a r r y on 2011-06-18
```
sudo apt-get install awk
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package awk is a virtual package provided by:
  original-awk 2009-11-26-1
  mawk 1.3.3-15ubuntu2
  gawk 1:3.1.6.dfsg-4build1
You should explicitly select one to install.
E: Package awk has no installation candidate

```
Now, given a choice right off between one version and another on my first apt-get install, How do I tell which one to use?  Or in a case like this, does it matter?

---

### Post by L a r r y on 2011-06-18
To answer my own question about awk, gawk and mawk, I started a Google search, and am finding a bit of useful info, so just like when I was learning how to write HTML, I use a lot of Google.  If you have any direct advice, please pass it on as well.  Thanks.

---

### Post by idoitprone on 2011-06-19
if you want all the processes that are currently running, run ps
```

ps -ef

man ps
```

---

### Post by L a r r y on 2011-06-19
OK to start out with, my bootstrap log begins with:
```

Selecting previously deselected package base-files.
dpkg: regarding .../base-files_5ubuntu4_i386.deb containing base-files, pre-dependency problem:
 base-files pre-depends on awk
  awk is not installed.
dpkg: warning - ignoring pre-dependency problem !
(Reading database ... 0 files and directories currently installed.)
Unpacking base-files (from .../base-files_5ubuntu4_i386.deb) ...
Selecting previously deselected package base-passwd.
Unpacking base-passwd (from .../base-passwd_3.5.21_i386.deb) ...
dpkg: base-passwd: dependency problems, but configuring anyway as you request:
 base-passwd depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
Setting up base-passwd (3.5.21) ...


```
I have a pre-dependency problem with awk not being installed, so I sudo apt-get install awk only to find that I have choice of gawk or mawk, but no awk.  I installed mawk only to find it already installed.


In this post I found some advice I thought might have to do with why the system wants awk and not mawk or gawk:
[http://ubuntuforums.org/showthread.php?t=1200506](http://ubuntuforums.org/showthread.php?t=1200506)

It has me run: ```
sudo update-alternatives --config awk
```

So I ran that command, then ran it again just to document the change:```

There are 2 choices for the alternative awk (providing /usr/bin/awk).

  Selection    Path            Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gawk    10        auto mode
  1            /usr/bin/gawk    10        manual mode
  2            /usr/bin/mawk    5         manual mode

Press enter to keep the current choice[*], or type selection number: 2
update-alternatives: using /usr/bin/mawk to provide /usr/bin/awk (awk) in manual mode.
/////////Run the command again://///////
me@fast:~$ sudo update-alternatives --config awk
There are 2 choices for the alternative awk (providing /usr/bin/awk).

  Selection    Path            Priority   Status
------------------------------------------------------------
  0            /usr/bin/gawk    10        auto mode
  1            /usr/bin/gawk    10        manual mode
* 2            /usr/bin/mawk    5         manual mode

Press enter to keep the current choice[*], or type selection number: 

```
Did not solve the pre-dependency problem.  So obviously I did not find the right advice for my issue.  As you see in the top snippet of the very lengthy bootstrap log, there is yet another missing pre-dependency that I have not yet tackled, and much further down the log there are some warnings about a false stop-start daemon.  Trying to deal with one thing at a time.

I need some advice.  Thanks much.

---

