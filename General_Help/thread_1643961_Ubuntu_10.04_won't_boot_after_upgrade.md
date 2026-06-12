---
title: "Ubuntu 10.04 won't boot after upgrade"
date: 2010-12-12
forum: General Help
---

### Post by jimbarfield on 2010-12-12
I downloaded recommended updates and restarted the computer (Lenovo G550).

As I clicked my user name and typed in my password the video went haywire for a split second and it made a horrible audio sound.

Now when I try to boot up it just returns me to the login screen over and over.

I booted off of a liveCD and can see the folders on my hard drive but root and home have an X on them and I am denied permission to view them.

I tried Ctrl+Alt+F1 and I am able to login in text mode.  The folder I am trying to recover is on my desktop and it is named Jim Barfield (2 words).  When I attempt to navigate to this folder it says that the folder or command does not exist.

Does anyone have any ideas?  I have replaced the hard drive and Win7 runs fine- I do not think it is a hardware problem.

I really need those files- it is a customer's backup of all thing!  Argghhhh!!!  Thanks one million for any help please.

---

### Post by ChuckyDuckster on 2010-12-12
Ouch. You could try to install Ubuntu again (Side-by-side) and then get the files from the first partition

---

### Post by jimbarfield on 2010-12-12
I thought about installing Ubuntu a second time in another partition but I do not know if that will enable my permissions to copy the files.  I am thinking I have a problem with x.  One thing I did notice one item listed in the updates to install has a Micro$oft EULA; it was some kind of Windows folder share permissions for Samba.

Again- I can login in a console, but when I try to open that folder on my desktop it fails.  Also, when I navigate to downloads I can see all my movies and stuff, but they will not open (maybe because .avi cannot open without x...)

I'm not good at consoles but I can follow directions.  I only have this one computer and I have to switch out hard drives to get back into Ubuntu.

Any ideas appreciated!!!!!!

Thanks

---

### Post by MooPi on 2010-12-12
Try this before attempting to install again. In fact I don't believe that is a good option at all.
First you'll want to boot into recovery console. Restart you computer and when the bois splash disappears hit the shift key to enter grub. From the grub menu pick ```
recovery mode
```Then scroll down to root console.

Try this 
```
dpkg --configure -a
```
This should try to correct a partial update or upgrade.

---

### Post by jimbarfield on 2010-12-12
Thank you I will try after switching out hard drives again.  I do know that when I choose Ubuntu Recovery Console from the menu at the bottom of my screen it does the same ting: I click on my user name and enter my password, so text flies by very quickly and it presents me back to the login box.

The only way I have been able to login is Ctrl+Alt+F1.  Then I can cd to /Desktop and see my folder- I think it is in blue text.  When I try to cd to that folder it says command or folder not found.

I tried to install a root user but it failed to fetch all files. 

From the liveCD I have not setup wireless yet, because I was so disgusted, but maybe I will boot off of liveDC, setup wireless and then install a root user if anyone thinks that will help.

Basically I am trying to get all the ideas I can, and write them down, so that I can try any and all ideas while offline.

Thanks again!!!!

---

### Post by MooPi on 2010-12-12
> **jimbarfield said:**
> Thank you I will try after switching out hard drives again.  I do know that when I choose Ubuntu Recovery Console from the menu at the bottom of my screen it does the same ting: I click on my user name and enter my password, so text flies by very quickly and it presents me back to the login box.
This does not sound right. If your in recovery mode you should not have to enter a user name or password. You may want to try again but this time scroll down and select ```
dpkg Repair broken packages
```

---

### Post by jimbarfield on 2010-12-12
Thank you.  When I have to select recovery mode from the login it just kicks me back to the login.  However, I have not trie enter recovery mode by hitting the Shift key while booting up, so I will try this. Thank you!

---

