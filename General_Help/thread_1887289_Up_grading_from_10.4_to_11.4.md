---
title: "Up grading from 10.4 to 11.4"
date: 2011-11-26
forum: General Help
---

### Post by Silvernail on 2011-11-26
I would like to upgrade. Not being a power user, I need some basic newbie type questions answered for my own peace of mind.
1. Am I reading this correct, I should not upgrade straight to 11.4 but go from 10.4 to 10.10 then to 11.4?
2. Is this big a jump called an upgrade or a new install?
3. What should I backup to an external hard drive? Everything above 'home'? Then, does everything just copy back and work?
4. Would I better off to just go with a new install?

Thanks for any help.
Dave

---

### Post by OrangeCrate on 2011-11-26
> **Silvernail said:**
> I would like to upgrade. Not being a power user, I need some basic newbie type questions answered for my own peace of mind.
1. **Am I reading this correct**, I should not upgrade straight to 11.4 but go from 10.4 to 10.10 then to 11.4?
2. Is this big a jump called an upgrade or a new install?
3. What should I backup to an external hard drive? Everything above 'home'? Then, does everything just copy back and work?
4. **Would I better off to just go with a new install?**

Thanks for any help.
Dave

You are correct. To upgrade, you would have to go through 10.10 to get to 11.04. A quicker and cleaner way to get to 11.04, would be to backup your important files in the home folder (no need to backup the hidden files), and install 11.04.

---

### Post by Silvernail on 2011-11-27
Thanks for the feedback. I'll just go with the complete install..

One last question. I did not find a thread on this.
I would rather keep the desktop screen and icon I now have with 10.4 instead of the  new theme. Is that possible. If so what words do I search for to find the howto?

---

### Post by OrangeCrate on 2011-11-27
> **Silvernail said:**
> Thanks for the feedback. I'll just go with the complete install..

One last question. I did not find a thread on this.
**I would rather keep the desktop screen and icon I now have with 10.4 instead of the  new theme. Is that possible.** If so what words do I search for to find the howto?

Personally, even if it could be done, I wouldn't have any idea how to do it. Maybe some other kind soul can jump in here and help you...

Good luck.

---

### Post by oldtimer7777 on 2011-11-27
I'm recommending 10.04 users to wait until the upcoming LTS Ubuntu version.

It isn't quite there yet.

> **Silvernail said:**
> I would like to upgrade. Not being a power user, I need some basic newbie type questions answered for my own peace of mind.
1. Am I reading this correct, I should not upgrade straight to 11.4 but go from 10.4 to 10.10 then to 11.4?
2. Is this big a jump called an upgrade or a new install?
3. What should I backup to an external hard drive? Everything above 'home'? Then, does everything just copy back and work?
4. Would I better off to just go with a new install?

Thanks for any help.
Dave

---

### Post by Silvernail on 2011-11-27
> **oldtimer7777 said:**
> I'm recommending 10.04 users to wait until the upcoming LTS Ubuntu version.

It isn't quite there yet.
Why is that?

---

### Post by oldtimer7777 on 2011-11-27
> **Silvernail said:**
> Why is that?

If you want to get a really quick idea what is different between  11.10 and previous versions of Ubuntu I highly suggest reading these  reviews of the differences first:

 [http://www.cc-c.de/german/linux/ubuntu.php](http://www.cc-c.de/german/linux/ubuntu.php)

 and this

 [http://www.zdnet.com/blog/perlow/why-ubuntu-1110-fills-me-with-rage/19103](http://www.zdnet.com/blog/perlow/why-ubuntu-1110-fills-me-with-rage/19103)

I'm still back at 11.04, quite happy with Gnome 2 (Classic Gnome), and working on a "production" system.  I'm not really into debugging all the "new" issues. I have work to do with this computer, so hopefully that clears up any confusion there.

If I was going to suggest Ubuntu to a friend, I would probably tell them to use this walkthrough to have the best system for now, or at least until the LTS:

[https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](https://debianhelp.wordpress.com/2011/07/05/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

This isn't a complaint as much as it would be friendly advice. I love Ubuntu, but if it is my machine, it is going to be Classic Gnome, and Ubuntu 11.04 for now.

If you absolutely must have the latest and greatest thing, I would probably give the new Mint 12 a run for its money. But I don't have a guide for new users to help them with installing it yet.

---

### Post by Silvernail on 2011-11-27
> **oldtimer7777 said:**
> 
This isn't a complaint as much as it would be friendly advice. I love Ubuntu, but if it is my machine, it is going to be Classic Gnome, and Ubuntu 11.04 for now.


Actually 11.4 is where I want to go. Most likely for the same reasons you are there.

---

### Post by Silvernail on 2011-11-27
> **OrangeCrate said:**
>  A quicker and cleaner way to get to 11.04, would be to backup your important files in the home folder **(no need to backup the hidden files)**, and install 11.04.

I created a directory with the following content.
> 
.  ..  nodot1  NODOT1  nodot2  NODOT2  nodot3  NODOT3  .nodot4  .NODOT4  .nodot5  .NODOT5  .nodot6  .NODOT6

The lower case being directories and the upper case files. Both visible and hidden directories had files and sub-directories.

Then ran this command line.
```

ls -R | rm -R .*

```
All the hidden files and directories were removed.

My question:
When making a new install of a newer OS, can I copy my entire primary drive to an external hard drive and run this command line?  Would I be save?

---

### Post by OrangeCrate on 2011-11-27
^,

Boy, you're way ahead of me, I have no idea what you're doing. :(

I just copy my personal folders and files from the Home Folder to a USB stick, and then transfer them back into the new install.

---

### Post by oldtimer7777 on 2011-11-27
> **OrangeCrate said:**
> ^,

Boy, you're way ahead of me, I have no idea what you're doing. :(

I just copy my personal folders and files from the Home Folder to a USB stick, and then transfer them back into the new install.

What I do that works for me.. is I install a fresh system just the way I want it..  Clone it with Remastersys, and then I have the ability to reinstall it in about 10 minutes from a Live USB Flash stick of Remastered iso Ubuntu created with Ubuntu Startup Disc Creator.  Unless you have a system that is larger than 4.7GB, you really should check out Remastersys or Relinux. You can even move your stuff into Skel to have those moved over as well.  It is so easy for data migration and you have a nice fresh clean system to work with. Flawless.

---

### Post by Silvernail on 2011-11-27
What I'm about to do is **MAKE A BIG MISTAKE**.
Some of those hidden files contain things like my FTP connect data, my bookmarks for my browsers etc.

I need to **move** those files outside the main backup directory.

Then remove them. Then copy relevant stuff back.

---

### Post by oldtimer7777 on 2011-11-27
> **Silvernail said:**
> What I'm about to do is **MAKE A BIG MISTAKE**.
Some of those hidden files contain things like my FTP connect data, my bookmarks for my browsers etc.

I need to **move** those files outside the main backup directory.

Then remove them. Then copy relevant stuff back.

Then you use Remastersys to do a complete backup instead.  That way it copies all of your hidden files and folders.

---

### Post by OrangeCrate on 2011-11-27
> **oldtimer7777 said:**
> What I do that works for me.. is I install a fresh system just the way I want it..  Clone it with Remastersys, and then I have the ability to reinstall it in about 10 minutes from a Live USB Flash stick of Remastered iso Ubuntu created with Ubuntu Startup Disc Creator.  Unless you have a system that is larger than 4.7GB, you really should check out Remastersys or Relinux. You can even move your stuff into Skel to have those moved over as well.  It is so easy for data migration and you have a nice fresh clean system to work with. Flawless.

I'll look into that, thanks.

---

### Post by Silvernail on 2011-11-28
In the upgrade to 11.4 from 10.4, can I make these assumptions?

1. All the bash shell scripts I have written will be compatible?
2. Will the scripts that use calls to function in Image Magick and mencode still work?

---

### Post by bluexrider on 2011-11-28
[B]Let me ingest something here.
                                [/B]
[http://community.linuxmint.com/tutorial/view/2](http://community.linuxmint.com/tutorial/view/2)

This is a quick and easy way to do what you want.

---

### Post by Fred Doolie on 2011-11-28
> **OrangeCrate said:**
> A quicker and cleaner way to get to 11.04, would be to backup your important files in the home folder (no need to backup the hidden files), and install 11.04.

I disagree. The "hidden files" include your settings for your software. Also think about other things you may have installed or modified and include them in the backup.

This is my personal backup list as an example. Your mileage will vary.
/puppy
/FirestormCache
/PhoenixCache
/etc/grub.d/40_custom
/home/Fred/.mozilla  <---PRICELESS Firefox settings!!!
/home/Fred/.skype 
/home/Fred/.firestorm   <---took me *days* to tweak just right
/home/Fred/.secondlife <--same
/home/Fred/*   <---my home folders and files
Four of those are hidden.

Restoring those and typing "sudo update-grub2"  puts me back to what I had before (more or less) when changing Ubuntus.

---

### Post by OrangeCrate on 2011-11-28
> **Fred Doolie said:**
> **I disagree. The "hidden files" include your settings for your software. Also think about other things you may have installed or modified and include them in the backup.**

This is my personal backup list as an example. Your mileage will vary.
/puppy
/FirestormCache
/PhoenixCache
/etc/grub.d/40_custom
/home/Fred/.mozilla  <---PRICELESS Firefox settings!!!
/home/Fred/.skype 
/home/Fred/.firestorm   <---took me *days* to tweak just right
/home/Fred/.secondlife <--same
/home/Fred/*   <---my home folders and files
Four of those are hidden.

Restoring those and typing "sudo update-grub2"  puts me back to what I had before (more or less) when changing Ubuntus.

I understand your opinion, and I certainly have no problem with it, but frankly, when I do a *fresh* install, I don't want settings from the previous one. All I want is my personal files from the previous Home folder. I always want to start again, with a pristine installation.

---

### Post by dFlyer on 2011-11-28
Regardless of how you decide to upgrade, you need to backup your home folder before doing anything. I would suggest you download the iso and do a fresh install, time making a separate partition for your home folder. That way in the future when you upgrade you can keep your home folder intact.

---

