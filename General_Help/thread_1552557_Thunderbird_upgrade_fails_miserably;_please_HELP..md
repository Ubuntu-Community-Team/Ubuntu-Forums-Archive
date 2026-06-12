---
title: "Thunderbird upgrade fails miserably; please HELP."
date: 2010-08-13
forum: General Help
---

### Post by noob555 on 2010-08-13
Hello all,

I added the ubuntuzilla ppa and downloaded thunderbird.  But it crashed almost instantaneously.  I tried opening in safe mode, but it crashed again.  I gave up and opened my original version of Thunderbird from Ubuntu's repositories, but *then that crashed*.  Then I tried to open firefox *but that crashed* (Huh? I didn't even touch that program.)

I then tried removing, reinstalling, and then restarting.  But something happens when I restart because now my computer is convinced that thunderbird and firefox are running all the time.  If I click on the launcher, it tells me that the program is already running.  But if I check the list of running processes on the system monitor, there is no reference to either program.

I have since tried completely removing and reinstalling from synaptic and Ubuntu software center, removing the Ubuntuzilla ppa, completely removing all ubuntuzilla software, starting in safe mode, and even deleting my user profiles (after making a copy to my desktop).

Nothing works.

What is going on?  I have never seen anything like this before.

Please help.  These programs are essential to my life.  :(

Specs:

Lucid
32 bit
IMB Thinkpad x41 with Intel Centrino

---

### Post by afrodeity on 2010-08-13
Can you run thunderbird from a terminal to see if there's any output. I never use the Ubuntuzilla script precisely because of the chances something like this will happen, also you're probably installing too high upstream and need to come down. Ubuntuzilla tends to install development versions of these programmes.

---

### Post by noob555 on 2010-08-13
Thank you for your assistance.  I used ubuntuzilla when I was on Jaunty and never had a problem.  But I'm sure you're right.

In answer to your question, no I cannot open Thunderbird or Firefox in the terminal.  Whenever I try to open either program (whether it is in the terminal or via the main menu) I receive the following error message in a pop-up window:

[INDENT]*Thunderbird* is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.[/INDENT]

or

[INDENT]*Firefox* is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system.[/INDENT]

This is true even after a fresh restart of the entire system.

---

### Post by lidex on 2010-08-14
Alt+F2
```
gnome-system-monitor
```
Kill anything firefox/thunderbird related. Rename your profiles. 
Purge these:
```
sudo apt-get purge firefox thunderbird
```
Now try a re-install.

---

### Post by noob555 on 2010-08-14
Hi lidex,

Thanks for assistance.  I did as you suggested: checked the system monitor (nothing there) and then purged both programs via terminal.  Then I restarted and reinstalled.  But I still get the same error message.  It's very strange.

I noticed a couple things in the terminal that looked weird -- both when I purged and when I reinstalled.  So I saved the output and I'm attaching here.

Also, I took screenshots of my system monitor.  I don't see anything mozilla related, but the computer believes otherwise.

Thoughts?

THIS IS THE TERMINAL OUTPUT FROM WHEN I CHECKED THE SYSTEM MONITOR AND PURGED FIREFOX & THUNDERBIRD:

```
xxx@xxx-ubuntu:~$ gnome-system-monitor

** (gnome-system-monitor:1615): WARNING **: SELinux was found but is not enabled.

xxx@xxx-ubuntu:~$ sudo apt-get purge firefox thunderbird
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-getoptions2.0-cil linux-headers-2.6.32-21 python-paramiko
  python-configobj linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  firefox* firefox-branding* thunderbird*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 60.0MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 225058 files and directories currently installed.)
Removing thunderbird ...
Purging configuration files for thunderbird ...
Removing firefox ...
Purging configuration files for firefox ...
Removing firefox-branding ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for python-support ...
xxx@xxx-ubuntu:~$ 
```

THIS IS THE TERMINAL OUTPUT FROM WHEN I REINSTALLED THEM AFTER I RESTARTED THE COMPUTER:

```
xxx@xxx-ubuntu:~$ sudo apt-get install firefox thunderbird
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-getoptions2.0-cil linux-headers-2.6.32-21 python-paramiko
  python-configobj linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  firefox-branding
Suggested packages:
  firefox-gnome-support kmozillahelper thunderbird-gnome-support
The following NEW packages will be installed:
  firefox firefox-branding thunderbird
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.9MB of archives.
After this operation, 60.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package firefox-branding.
(Reading database ... 224380 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Selecting previously deselected package thunderbird.
Unpacking thunderbird (from .../thunderbird_3.0.6+build2+nobinonly-0ubuntu0.10.04.1_i386.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up thunderbird (3.0.6+build2+nobinonly-0ubuntu0.10.04.1) ...

Setting up firefox-branding (3.6.8+build1+nobinonly-0ubuntu0.10.04.1) ...
Setting up firefox (3.6.8+build1+nobinonly-0ubuntu0.10.04.1) ...
Please restart all running instances of firefox, or you will experience problems.

xxx@xxx-ubuntu:~$
```

---

### Post by afrodeity on 2010-08-14
trying opening a terminal and running

```

firefox --safe-mode

```

---

### Post by noob555 on 2010-08-14
> **afrodeity said:**
> trying opening a terminal and running

```

firefox --safe-mode

```

Doesn't work.  I get the same error message every single time.

[INDENT]Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.[/INDENT]

Same problem with Thunderbird.  

The problem is, I can't figure out what process is "running" both firefox and thunderbird.  

Something really screwy happened when I tried updating thunderbird via ubuntuzilla and I have no idea what it is.

---

### Post by lidex on 2010-08-14
Why do you have so many chromium processes running? Try killing those as well. Firefox gives me three processes.
Also, in System Monitor, the View menu, make sure 'All Processes' is ticked.

---

### Post by noob555 on 2010-08-14
> **lidex said:**
> Why do you have so many chromium processes running? Try killing those as well. Firefox gives me three processes.
Also, in System Monitor, the View menu, make sure 'All Processes' is ticked.

I don't know why Chromium runs so many processes.  I just downloaded it recently as a backup browser.  Anyways, I shut down chromium and it has no effect on firefox or thunderbird.

I checked the "all processes" box and did another set of print screens.  The first five are attached here.  I'll attach the 6th, which has just a few extra processes, to the next post.

---

### Post by noob555 on 2010-08-14
Here's the 6th screen shot.  Just a few more processes at the bottom of the list.

---

### Post by afrodeity on 2010-08-14
Try removing ubuntuzilla. It should show up in synaptic, otherwise use ppa-purge, it will figure out what needs to be done to return your system to state before you added the ubuntuzilla ppa.

---

### Post by noob555 on 2010-08-14
> **afrodeity said:**
> Try removing ubuntuzilla. It should show up in synaptic, otherwise use ppa-purge, it will figure out what needs to be done to return your system to state before you added the ubuntuzilla ppa.

Afrodeity,

Thanks for the advice.  I downloaded ppa-purge from get-deb.  Seems like this is precisely what I need.

I ran ```
sudo ppa-purge http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt
```

This is what I got.

```
xxx@xxx-ubuntu:~$ sudo ppa-purge http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt
PPA to be removed: 
http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt ppa
Warning:  Could not find package list for PPA: 
http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt ppa
xxx@xxx-ubuntu:~$ 
```

Am I doing something wrong?

---

### Post by lidex on 2010-08-14
> **noob555 said:**
> Here's the 6th screen shot.  Just a few more processes at the bottom of the list.

It would help to see the 'command line' field in system monitor. If the ppa:purge doesn't work just uninstall everything you can using apt/synaptic then run these commands:
```
sudo updatedb
locate firefox
locate thunderbird
```
Delete everything you find. Probably have something in /opt
Re-run the commands to make sure nothing is left. You may also want to try: ```
locate mozilla
``` 
Lastly remove any ubuntuzilla sources from 'System>Administration>Software Sources' and **reboot**. Back at the desktop install firefox and see what happens.

---

### Post by noob555 on 2010-08-14
I removed everything I could think of on synaptic.  I ran updatedb, locate, etc...

Couple questions.

(1) is there a fast way to delete all of these files?  the number of files that comes up associated with firefox is HUGE and running rm -r on every one will take forever.

(2) even after I delete some files, they still show up when I run locate ___.  For example, I have deleted /home/xxx/.mozilla-thunderbird already.  If I try to delete it again, I get the following error:

```
xxx@xxx-ubuntu:~$ rm -r /home/robziff/.mozilla-thunderbird
rm: cannot remove `/home/xxx/.mozilla-thunderbird': No such file or directory
xxx@xxx-ubuntu:~$ 

```

But it keeps showing up when I run locate.

---

### Post by supermario641996 on 2010-08-14
> **noob555 said:**
> I removed everything I could think of on synaptic.  I ran updatedb, locate, etc...

Couple questions.

(1) is there a fast way to delete all of these files?  the number of files that comes up associated with firefox is HUGE and running rm -r on every one will take forever.

(2) even after I delete some files, they still show up when I run locate ___.  For example, I have deleted /home/xxx/.mozilla-thunderbird already.  If I try to delete it again, I get the following error:

```
xxx@xxx-ubuntu:~$ rm -r /home/robziff/.mozilla-thunderbird
rm: cannot remove `/home/xxx/.mozilla-thunderbird': No such file or directory
xxx@xxx-ubuntu:~$ 

```

But it keeps showing up when I run locate.
Did you restart your computer after.  That might work.

---

### Post by lidex on 2010-08-14
You need to run the 
```
sudo updatedb
```
command to show the changes.
As for file removal you could run nautilus as root and delete that way but **you have to be very careful** as you don't want to remove system files.
```
gksu nautilus
```

---

### Post by noob555 on 2010-08-15
Hi again Lidex,

Thank you so much for all of your assistance.  I finally got everything working again this morning.  I'm not sure how.  I just focused on deleting the files associated with Thunderbird, since that's where the problem started.  Eventually, I grew tired, so I just tried to see if I could get it to work. I restarted the computer, reinstalled FF and TB from the repos, redirected them to my profiles, and suddenly everything works like a charm again.

Once again, thank you.  And to everyone else who assisted me on this thread.  You have all been tremendously helpful.  Every time my computer breaks down, I end up learning something new and valuable from the forum members.

Cheers.

---

### Post by afrodeity on 2010-08-15
> **noob555 said:**
> Afrodeity,

Thanks for the advice.  I downloaded ppa-purge from get-deb.  Seems like this is precisely what I need.

I ran ```
sudo ppa-purge http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt
```

This is what I got.

```
xxx@xxx-ubuntu:~$ sudo ppa-purge http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt
PPA to be removed: 
http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt ppa
Warning:  Could not find package list for PPA: 
http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt ppa
xxx@xxx-ubuntu:~$ 
```

Am I doing something wrong?

Glad you solved your problem. I took a look at the man page for ppa-purge and notice there's a switch -p or -purge which seems a bit redundant to me.

```

ppa-purge -p|-purge nameoftheppa [-s|-server host]


DESCRIPTION
       This script provides a bash shell script capable of automatically down&#8208;
       grading all packages in a given PPA back to the ubuntu versions.

       You have to run it using root privileges because of  the  package  man&#8208;
       ager.

OPTIONS
       -p, -purge PPA
              Name of the PPA to be reset, the default value is ppa.

       -s, -server host
              Name  of the repository server, the default value is ppa.launch&#8208;
              pad.net.


```

Should be something like this:

```

sudo ppa-purge ppa:ubuntuzilla

```

---

