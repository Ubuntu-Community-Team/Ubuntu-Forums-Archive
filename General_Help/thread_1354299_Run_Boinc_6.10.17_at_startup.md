---
title: "Run Boinc 6.10.17 at startup"
date: 2009-12-13
forum: General Help
---

### Post by jason102 on 2009-12-13
Hi, I recently upgraded to Ubuntu 9.10 and annoyingly discovered that the default version of boinc (6.4.5) now available in Synaptic doesn't work with the World Community Grid project.They say the best answer is to just get a different version of boinc, so I decided to get the latest from the Berkeley site (6.10.17). This solved the problem and I was able to start crunching data for the World Community Grid.

However, because I downloaded the latest version of boinc from the website and not the package manager, it isn't associated with my system, something the package manager has always done for me. In other words, boinc isn't set up to run at startup and immediately start processing in the background.

I've tried to use System > Preferences > Startup Applications to select the boinc executable by browsing for it as the command, but it doesn't work. When I either logout and login or restart the machine boinc fails to initiate at startup. However, when I go back to the Startup Applications list, it's still listed there. 

The only thing I can figure out is that I'm not specifying the command for it's startup profile correctly. Right now all I have is the path to the executable, like this:

```
Command: /home/jason/BOINC/boinc
```

where "boinc" is the executable file.

Obviously I have to do something more for this to work?

EDIT:

Also, whenever I close out of the Boinc manager GUI it quits out of the boinc background process as well, a behavior that doesn't occur when it's installed via the package manager. The regular behavior that I want is for it to simply close the manager, but not quit boinc altogether. 

Or is there a way to update the repositories in Synaptic to instead allow me to install 6.10.17 instead of 6.4.5? In the past I've been able to "Force version" in Synaptic, but that has always only allowed me to choose previous software versions. In this case I want to choose an even later version. Any ideas?

---

### Post by oldos2er on 2009-12-13
> **jason102 said:**
> ```
Command: /home/jason/BOINC/boinc
```

where "boinc" is the executable file.

Obviously I have to do something more for this to work?


 Try ```
/home/jason/BOINC/run_client
``` instead. This way opening and closing Boinc manager shouldn't interfere with the running client.

---

### Post by jason102 on 2009-12-14
Thanks oldos2er, that works!

Now the only problem I have is that when I log out and log in (not restart), it'll add another instance of boinc running. I guess when I log out it doesn't quit the first instance of the process? Have any idea how I can fix this?

---

### Post by oldos2er on 2009-12-14
Hmmm. Not sure--I've never run into that problem. Have you looked here: [http://boincfaq.mundayweb.com/](http://boincfaq.mundayweb.com/)

---

### Post by jason102 on 2009-12-14
Ha - actually I saw something temporary. As soon as I logged back in I checked my processes in the System Monitor, and it listed 2 boinc processes. However, one was labeled hrtimer_nanosleep for the Waiting Channel, which eventually dissappeared after 10 seconds or so, and another instance, which stuck around, labeled as poll_schedule_timeout like most all of the other processes. 

I'm not exactly sure what these waiting channels are, but I must have opened and closed the System Monitor too quickly for me to see that the hrtimer_nanosleep instance of boinc was going to end shortly.

I think at this point I'm good to go. Thanks!

---

### Post by RoyStrachan on 2010-01-23
I'm late to the party for this, but it may help someone else.

Ubuntu installs boinc in /usr/bin.  Do the normal Ubuntu install to set things up then /usr/init.d/boinc-client stop to shut it down.  Rename the boinc files in /usr/bin to save them in case this doesn't work for you.  Download the boinc 6.10.17 file for your computer and do the shell install.  In the newly created BOINC directory you will find replacements for boinc, boinccmd and boincmgr.  Copy the new files to /usr/bin and perform /usr/init.d/boinc-client start.  You should now have the equivalent of the standard install but using 6.10.17.  With luck you should be able to carry on with work units you had running under the old version of boinc.  Now if I could only figure out how to get this working on Ubuntu Server...

---

### Post by Ivkosky on 2010-05-19
Hi everyone


I apologize when my questions would sound a bit silly, but I am new to linux, so please be patient with me... :)

I have contributed to BOINC community when using Window$ and would like to continue with it. I know that generally there are two processes - BOINC without GUI which does all the work and BOINC manager. I thought that you can run BOINC without manager, but when I quit it, I cannot see any process which could potentially be BOINC calculations running on the background...

I would also like BOINC to start automatically at startup. I have tried to sort it out using tips above, but nothing helped me. :( Maybe I did something wrong... :( For instance, I don't know, how to install from shell (sorry, I am newbie, I know :) )

The best would be either to run at startup without GUI (BOINC manager) or to run it also with it, but on the second desktop if possible...  Or minimised in the tray (but as far as I know, there isn't a possibility to do that for linux BOINC)... Simply, I would really like to start it up in such way, that it won't be noticeable. 

And the last, not so important, issue is that I cannot see graphical presentations of the calculations in BOINC manager - the window with graphs simply does not appear after clicking on the appropriate button...

I would be really grateful for any comments! Thank you!

P.S.: I am running Ubuntu 9.10 and I have installed Synaptic version of BOINC.

---

### Post by oldos2er on 2010-05-19
Maybe this will help: [http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu](http://boinc.berkeley.edu/wiki/Installing_BOINC_on_Ubuntu)

---

### Post by jason102 on 2010-05-19
Ivkosky - try this:

1) Uninstall boinc from Synaptic

2) Download latest version of Boinc from [http://boinc.berkeley.edu/download.php](http://boinc.berkeley.edu/download.php)

3) Open up a terminal, and navigate to the location where you downloaded the file

4) use "sh boinc_...-linux-gnu.sh" (replace actual filename after sh) to extract the folder to the current directory

5) cut and paste this extracted folder to the directory you'd like the Boinc program files to reside in - an easy location is your home folder (that's where I'm storing mine)

6) Next, open up the BOINC folder and use a text editor to open and modify "run_client"

7) change the directory path specified in parenthesis " " to be that of the current directory it's in (again, for an example, my run_client looks like this, since I have the BOINC folder in my home directory: cd "/home/jason/BOINC" && exec ./boinc $@)

8) run_client is the file you will use to automatically start boinc in the background automatically upon login without you having to always have the boinc manager GUI window open for the program to run - go to System > Preferences > Startup Applications.

9) Under the Startup Programs tab, click the Add button. Give the process a name (like Boinc, or really whatever you want to identify the boinc process to be).

10) the Command is the most important part of this - specify the path of your run_client file. You can either Browse for this file or type the path in manually. Again, for example, my path/command to run_client is

/home/jason/BOINC/run_client

11) Save the new startup process and make sure it was added to the Startup Programs list.

12) Now run the GUI straight from the BOINC folder - run boincmgr

13) Attach/sign in, to whatever project(s) you want your system to work on

14) Close the window - you can X the window out - all we needed to do here was to get you signed into your projects

15) logout and log back in. See if boinc is running in the background by checking the system monitor: System > Administration > System Monitor. Click on the Processes tab and look for "boinc". If it's listed, you should be set! This means boinc was successfully started up in the background. You can run boincmgr any time you want to check on the boinc's progress. You can also close the window without actually ending the background boinc process. Is this the behavior you want?

16) It's good to be aware of what you're processor's current load is, especially when boinc is running. I suggest you add a widget to one of your gnome panels, System Monitor. Right-click the panel you want to add it to, and find System Monitor in the Add to Panel list. Click Add and then Close. You should be able to see boinc working in the background visually now - you should see your processor peak every second or so - that's boinc. 

Does that work for you?

---

### Post by Ivkosky on 2010-05-22
Hi Jason


Thank you very much for your guide! I have done everything that you wrote.

My only problem is that the BOINC process is not listed in the system monitor... However, from the processor monitor I can see that it should be working on the background (I have those peaks you mentioned)... Weird...

Is there any chance that the process is running but under another name? I scanned the whole list of processes and didn't find anything which could be connected to BOINC though... :(

---

### Post by dcstar on 2010-05-22
> **Ivkosky said:**
> 
..........
And the last, not so important, issue is that I cannot see graphical presentations of the calculations in BOINC manager - the window with graphs simply does not appear after clicking on the appropriate button...

I would be really grateful for any comments! Thank you!

P.S.: I am running Ubuntu 9.10 and I have installed Synaptic version of BOINC.

There is an issue with the Boinc graphics that is resolved with a xhost command:

[http://wiki.debian.org/BOINC/Troubleshooting](http://wiki.debian.org/BOINC/Troubleshooting)

This is not required any more on 10.04 systems, you may just want to install the Boinc packages for 10.04 from:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by jason102 on 2010-05-23
> **Ivkosky said:**
> Hi Jason


Thank you very much for your guide! I have done everything that you wrote.

My only problem is that the BOINC process is not listed in the system monitor... However, from the processor monitor I can see that it should be working on the background (I have those peaks you mentioned)... Weird...

Is there any chance that the process is running but under another name? I scanned the whole list of processes and didn't find anything which could be connected to BOINC though... :(

Hmm... I actually just had to do a system reinstall, so I followed my own instructions exactly and I can see "boinc" listed in my process list. 

A weird problem I had before was that sometimes the Startup Applications program would "forget" the latest thing I added after a reboot or logout/login, and I'd have to add it again until it somehow "remembered". However, that was when I was running 9.10 - I'm using 10.04 now and I haven't had any issues with that. 

What about when you run boincmgr? When you see the processing peaks in the system monitor (Resources tab or your panel widget), does boincmgr under the Tasks tab (advanced view mode) show the Progress and Elapsed time columns updating/changing/increasing? If the progress percentage is slowly going up, it must be working ok...

Other than that I'm not sure - my instructions just worked for me on a clean install of 10.04, so I don't know.

---

### Post by Ivkosky on 2010-06-04
Hi Jason


I apologize for my late response. I've been pretty busy at work and haven't had time to look at it. Thanks for all your help! I think I will wait till I switch to 10.4 and try to set up boinc just after that. Maybe I will find some time to do the upgrade already this week... :)

Thanks!

---

