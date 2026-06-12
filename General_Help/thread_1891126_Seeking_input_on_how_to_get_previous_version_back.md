---
title: "Seeking input on how to get previous version back"
date: 2011-12-04
forum: General Help
---

### Post by alvinmoneypit on 2011-12-04
Hi All,
Looking to upgrade my Lenovo N500 (Intel 575 @ 2 Ghz w/3Gb memory) to a newer version of Ubuntu (simply to get a later version of Mozilla Firefox and make sure everything is running well).

I'm running 9.10 flawlessly and have all the functionality I wish for (except for the firefox 3.6.13 that I'm running) including my WINE programs are also running well. 
 But getting new Ubuntu software through software center is getting impossible to do, so what are my best options?  Can I go back to what I have and be sure I have all the functionality I have?  If so, How do I do it?  
I haven't made a change yet, just exploring whether I want to invest the time it takes (of my rare and precious vacation time!) to install the new system and if necessary, come back to the one I got.

---

### Post by oldtimer7777 on 2011-12-04
> **alvinmoneypit said:**
> Hi All,
Looking to upgrade my Lenovo N500 (Intel 575 @ 2 Ghz w/3Gb memory) to a newer version of Ubuntu (simply to get a later version of Mozilla Firefox and make sure everything is running well).

I'm running 9.10 flawlessly and have all the functionality I wish for (except for the firefox 3.6.13 that I'm running) including my WINE programs are also running well. 
 But getting new Ubuntu software through software center is getting impossible to do, so what are my best options?  Can I go back to what I have and be sure I have all the functionality I have?  If so, How do I do it?  
I haven't made a change yet, just exploring whether I want to invest the time it takes (of my rare and precious vacation time!) to install the new system and if necessary, come back to the one I got.

Try using Ubuntu 11.04?

[https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

I'm waiting for the LTS in April at this point to see what changes that may bring for the current state of 11.10.  It is kind of inflexible sometimes for my uses.  It really is subjective and depends on what you are going to use it for.  At least 11.04 still has the option of Gnome 2, which might be of interest to you.

---

### Post by Dennis N on 2011-12-05
> **alvinmoneypit said:**
> Hi All,
Looking to upgrade my Lenovo N500 (Intel 575 @ 2 Ghz w/3Gb memory) to a newer version of Ubuntu (simply to get a later version of Mozilla Firefox and make sure everything is running well).

I'm running 9.10 flawlessly and have all the functionality I wish for (except for the firefox 3.6.13 that I'm running) including my WINE programs are also running well. 
 

You can always get the latest Firefox directly from Mozilla:

[http://www.mozilla.org/en-US/firefox/fx/]("http://www.mozilla.org/en-US/firefox/fx/")

The archive you download contains the folder 'firefox' which you could extract to your home folder. Inside that folder is the executable, also 'firefox'. Change any application launcher to point to that executable file. It will normally find and use your existing profile as well.

---

### Post by alvinmoneypit on 2011-12-05
I wish a completely functioning software for my hardware parameters.  If it doesn't give me full video support, printing, firefox, flash and especially multimedia support, including my WINE and associated windows programs out of the box, then I'm probably not going do the upgrade.

I just want to see that IF I do the upgrade, I can somehow get back exactly to where I'm at now if things don't work out AND about how long it should take to  do so. If you have any ideas or thoughts on these questions, it would be most appreciated.

Al

---

### Post by SteveDee on 2011-12-05
> **alvinmoneypit said:**
> 
I haven't made a change yet, just exploring whether I want to invest the time it takes (of my rare and precious vacation time!) to install the new system and if necessary, come back to the one I got.

To safeguard your existing system I recommend you download Clonezilla and make a CD. You can use this to create a clone of your system (on a USB drive or memory stick) so you can recover your entire system if you are not happy with the upgrade.

Upgrading is always a risk. I often discover things that are not right weeks or sometimes months after an upgrade (most often video or sound related). As you don't have much time, having a clone is a great fall-back mechanism. Creating a clone is a relatively quick process, and restoring it back to your system is much, much quicker that an install or upgrade.

A lot of people on this forum upgrade as soon as a new version becomes available, because they are interested in running something new, or maybe they like experimentation. But many others just want a reliable computer, and having dealt with any initial problems, should probably stick with a version for as long as its useful..."if it aint broke...."

---

### Post by SteveDee on 2011-12-05
> **alvinmoneypit said:**
> ...AND about how long it should take to  do so. ...

Once you have your Clonezilla CD, creating a clone should take less than 10 minutes. Restoring your system using the clone, again less than 10 minutes.

However, since recovery seems to be so important to you I suggest you restore your clone to a test system before upgrading your main system (Its very easy to get hold of old unwanted computers from family & friends).

Another great alternative (if you are happy handling the hardware) is to invest in a new hard drive. Just take the old one out and store in an anti-static bag, then install the new version on the new drive.

---

### Post by alvinmoneypit on 2011-12-05
Thanks for your view, SteveDee, I'll probably buy the harddrive if I can find one cheap enough.  However, I don't want to risk losing some of my photos.  These are photos I know I have because I see them on the slideshow in my screensaver, but I can't find them to save them onto a thumb drive.  So, now it looks like I may need some good file system advice if I want to do this, or just take the risk, btw this disk is using about 140GB of a 160 GB drive.

Al

---

### Post by SteveDee on 2011-12-05
> **alvinmoneypit said:**
> ...I don't want to risk losing some of my photos....but I can't find them to save them onto a thumb drive....

Lubuntu does not have a search tool in the basic install, so I suggest you go to Synaptic and install: gnome-search-tool
You can then search your entire file system by ".jpg" or whatever graphics file extension you are using....you sure don't wanna lose those happy snaps!

---

### Post by marinara on 2011-12-05
hey it's linux.  about 90% of your stuff will work great.

no there isn't a way to go back.  But there's several ways to test out 11.10
virtual machine, live cd, installing 11.10 to a partition

go ahead and wipe your laptop and install 11.10.
if it doesn't work you can blame me.

---

### Post by MartyBuntu on 2011-12-05
You should be making regular drive backups and at least a backup before you do a major version upgrade.

You can always reload the drive image if your not satisfied with the upgrade. At least it will buy you some time t=until you figure out your next move without losing data or productivity.

---

### Post by alvinmoneypit on 2011-12-06
Thanks for all the input.

I'll probably wait to do this now since getting a harddrive for backup will probably be a while and this is working OK for now.  
I've can't remember a upgrade in Ubuntu or Windows for that matter that went smoothly.

---

### Post by alvinmoneypit on 2011-12-07
Thanks All for your advice!

---

