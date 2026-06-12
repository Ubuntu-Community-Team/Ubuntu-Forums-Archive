---
title: "Entire System Is Borked"
date: 2012-01-09
forum: General Help
---

### Post by popejeremy on 2012-01-09
I've had these ongoing problems:

[LIST]
[*]Forgets wifi passwords after each use. I have to type them in again every time.
[*]    When I look at Edit Connections, I can't add, edit, or delete any connections. However when I gksu the Edit Connections app, I can use it normally.
[*]    Every time I load Gmail, it tells me that my cookies are bad and I must delete all cookies to continue.
[*]    When I put a USB memory stick into the computer, it won't mount.
[*]    When I click Shut Down, it doesn't shut down. It just sends me to the login screen. When I select Shut Down from the login screen, it still doesn't shut down. The only way I can figure out how to shut down the computer is to open a terminal and sudo shutdown -h.
[/LIST]

I guessed that there might be some problems with my user groups. I tried to edit them in the Users and Groups application, but when I click on "Change" nothing happens...

In short, my system is borked and I can't even get it to mount an external hard drive in order to save my files and reinstall. What should I do?

---

### Post by imachavel on 2012-01-09
umm, what version ubuntu? For a moment, because of what I see you are having trouble with, it almost seems as though you are using windows ;)

I haven't had these linux problems yet, other ones but not the windows look alike problems. sorry mate. btw have you sudo apt-get install update recently? Well, your system does look pretty screwed up, have you tried rebooting, then holding f8, then clicking the option to 'repair broken packages'??

---

### Post by popejeremy on 2012-01-09
I'm running Ubuntu 11.10. All software packages are up to date.

---

### Post by imachavel on 2012-01-09
maybe you should reinstall. I hate recommending it, after all, it should be the very last option. I don't know let's see if a mod comes by and disagrees with me. If not then go ahead and reinstall

---

### Post by QIII on 2012-01-09
Don't reinstall.  Solve.

You've given a "laundry list", which is difficult to deal with.  Pick one to solve in this thread and then begin a thread for the next one.

People often just pass over laundry lists.  Single-issue posts attract the people with expertise in that item.

---

### Post by imachavel on 2012-01-09
any thing against putting in the OS disk, restarting the computer, and choosing 'system recovery' then from the command line entering:

[http://ubuntuforums.org/showthread.php?t=965882](http://ubuntuforums.org/showthread.php?t=965882)

sudo apt-get -f install

if he doesn't want safe mode in terminal command line form, he can use startx to get into gui in safe mode. It's not guaranteed to work, but it's worth a try. Here is what it says for me if I run it from here:

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

there are several other options, most of which I'm not too familiar, but it's worth a shot. I know I'm throwing things off the top of my head, I'm not sure just giving out ideas.

---

### Post by QIII on 2012-01-09
Any problem could be many things.  One might throw out any number of things from the top of the head.  One may also engage in endless and fruitless goose chases.

Identify.  Diagnose.  Resolve.  Test solution.  Redirect as necessary.

Problem solving is directed and deliberate.

---

### Post by topsites on 2012-01-09
I'd have to agree, lets address these problems one at a time, take a problem, any one, and work on it until that is fixed.
Only when the first problem you have picked out is fixed do we go on to the next.

That having been said...
[http://www.necopost.com/2011/05/ubuntu-wont-shutdown-logout-or-restart.html](http://www.necopost.com/2011/05/ubuntu-wont-shutdown-logout-or-restart.html)

---

### Post by Henkdroid on 2012-01-09
Check in the users and groups in the system settings what your permissions are, some of it sounds like you aren't being allowed to.

---

### Post by popejeremy on 2012-01-16
> **Henkdroid said:**
> Check in the users and groups in the system settings what your permissions are, some of it sounds like you aren't being allowed to.

I would like to be able to do this, but when I open the Users and Groups application and click on a button in the window, nothing happens. It's like I don't have permission to see the permissions. Catch-22.

---

