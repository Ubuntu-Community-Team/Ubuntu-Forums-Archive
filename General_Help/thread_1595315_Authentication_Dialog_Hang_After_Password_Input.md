---
title: "Authentication Dialog Hang After Password Input"
date: 2010-10-13
forum: General Help
---

### Post by siaush on 2010-10-13
I have a Ubuntu 10.10 installed on my HP Mini 210, and is having a problem with authentication dialogs when applications requests for elevated permissions. As far as I concern, there are two types of them, one is the kind when you run anything with gksu where the background dims and a dialog pops up. Another type is when you try to install software through Synaptic and a dialog box requests for your password. I am having problems with the later one. Whenever the authentication dialog box pops up, after typing my password and presses enter, or the Authenticate button, the password field disappears while leaving the authentication dialog on the screen. The Authenticate and Cancel buttons are still clickable, but they are not bringing any actions by clicking them. I would have to let the application to continue with elevated permissions by manually closing the dialog. There are very very rare occasions where the dialog disappears after I click on authenticate, which I can say is 1 in every 100 times.

This is particularly annoying as the dialog is suppose to be disposed after the correct password is inputed.

Any help will be greatly appreciated.

Thanks.

---

### Post by NTHQ on 2010-10-14
I am having the same issue since 10.04. If you just click on the X in the corner to close the dialog box the authentication still works but we shouldn't have to do this... the dialog box should close on its own.

---

### Post by siaush on 2010-10-15
I have tried another installation in VMWare, and the authentication dialog works fine. Any ideas? anyone?

Thanks.

---

### Post by sixit on 2010-10-15
I'm having exactly the same issue on the same setup.  The end result is that the software is not installed.

---

### Post by siaush on 2010-10-15
I can have the software installed, or any application have their elevated permissions granted by closing the authentication dialog myself though. It is not a big deal, but such a simple issue should not happen right?

---

### Post by sisco311 on 2010-10-15
Does
```
pkexec echo
```produce any error messages?

---

### Post by siaush on 2010-10-15
no errors, an authentication dialog pops up instead, and having the same problem after inputing password.

---

### Post by dannns on 2010-10-21
I was having the same issue. This system has gone through a couple distribution upgrades. Today I tried this and it seems to have fixed it. Lets see if it lasts.

Go to Synpatic Package Manager, right click on policykit-1-gnome, and select Mark for Reinstallation. Apply that, log out and log back in.


EDIT: I take that back. Tried to do a "pkexec echo" and it went back to the problem.

---

### Post by gfi on 2010-10-21
This is very annoying (Running on VMWare).  in 50% of the cases, it appears that the authentication goes thro.  50% chances that the hang will cause authentication failure.
Only way to realize authentication failure in software center is to look out for a 'progress dialog'.. similar to how a meerkat scout watches for predators in the wild!

---

### Post by AldenIsZen on 2010-10-22
I am getting this error when installing something via updates. I believe I have seen it happen other times when I need to authenticate, but when I click the x to close the prompt the action always seems to happen. I will report back if I see it other places. When I did the "pkexec echo" command, I again received the prompt that hung until it was "x'd" out. I ran it with sudo, was asked for my password in the terminal, and received the following output.

```
User of caller (1000) does not match our uid (0)
```

---

### Post by kijutsu on 2010-10-30
I too am having the same problem.

Additionally, the problem seems to exist in a terminal window as well.  VMWare Toolkit was not installed when I create a new VMWare Image.  I had to reinstall it, but when I issue sudo perl vmware-yadda-yadda.pl and it asked for authentication, it failed as well.  This has occurred with 3 different VMWare installations.  I've yet to figure out the problem.

---

### Post by sthilaire on 2010-11-13
I have also encountered the same issue - mostly in the graphical interface on Ubuntu 10.10 - new install on VMware.
I have not seen the issue using "sudo" via the command line - only the dialog prompt when doing Updates or Software installations.

--Tim

---

### Post by LinerJoe on 2010-11-15
I have the same issue as well.  For me, it started when I upgraded to 10.10 from 10.04 (with all updates applied before upgrading).  

I noticed it from day one of the 10.10 install.  I tested with 'pkexec echo' and I see the same issue.

---

### Post by LinerJoe on 2010-11-15
FYI - This has been resolved in policykit-1_0.96-2ubuntu1.2.  It is available here (as it hasn't hit the repositories yet):

[https://edge.launchpad.net/~james-w/+archive/polkit/+packages](https://edge.launchpad.net/~james-w/+archive/polkit/+packages)

I just installed and it fixed the issue on my machine.

The launchpad bug: 

[https://bugs.launchpad.net/ubuntu/maverick/+source/policykit-1/+bug/649939](https://bugs.launchpad.net/ubuntu/maverick/+source/policykit-1/+bug/649939)

joe

---

### Post by dannns on 2010-11-21
Thank you LinerJoe!

I installed James Westby PPA and updated Policy Kit and it did fix the problem.

sudo add-apt-repository ppa:james-w/polkit

---

### Post by Nordoelum on 2010-11-26
When will this hit the official repos?

---

### Post by cknoettg on 2010-11-29
I have encountered both of the problems mentioned in this thread since installing Ubuntu 10.10 Maverick. The authentication dialog does not go away when entering the correct password - I have to "x" it out to complete the install, and I cannot get full use out of command terminal, because it asks me for my password, then does not accept the correct password. For kicks, I tried restarting in Recovery Mode, went to root, and entered passwd -u *(my username)* and changed my password from within root. This did not solve the problem.

I then installed the James Westby PPA, and it solved both problems. Just in case there are any other extreme noobs out there - I was clicking individual i386 packages on his list (since I don't have an AMD64), and I was going in the order listed, using Ubuntu Software Center to open/install each package. When I came to the gobject packages, I received an error stating that it would "Break existing installation." So I jumped to the last big file on the list that contained the whole archive file. I knew it was stored in the location I specified, but I am a noob, so I didn't know what to do with it all. I used dannns' "sudo add-apt-repository ppa:james-w/polkit" from within the Command Terminal. It completed the job (and accepted my password from the terminal, which was impressive enough). The problem appears to be solved.

Now, I just need to figure out how to get around the fact that Ubuntu asks me for my password twice when I first log in. I'm sure there is another thread for that.
****
Update 12-12-2010 - I decided to uninstall Ubuntu 10.10 and take a breather, due to minor annoyances such as the multiple password issue listed. I later burned an ISO image of 10.10, installed a second hard drive that had otherwise been collecting dust, and installed Ubuntu to its own second hard drive. When I performed the installation in this way, I did not encounter the "no video input detected" problem, the multiple password requests, or the screensaver not working problem. I am happy that I did not give up, but I did find that uninstall/reinstall was my best option.

---

### Post by NikoC on 2011-02-15
> **LinerJoe said:**
> FYI - This has been resolved in policykit-1_0.96-2ubuntu1.2.  It is available here (as it hasn't hit the repositories yet):

[https://edge.launchpad.net/~james-w/+archive/polkit/+packages](https://edge.launchpad.net/~james-w/+archive/polkit/+packages)

I just installed and it fixed the issue on my machine.

The launchpad bug: 

[https://bugs.launchpad.net/ubuntu/maverick/+source/policykit-1/+bug/649939](https://bugs.launchpad.net/ubuntu/maverick/+source/policykit-1/+bug/649939)

joe

Solution works! Added the ppa and sudo dist-upgrade to install policykit.

Thanks

---

