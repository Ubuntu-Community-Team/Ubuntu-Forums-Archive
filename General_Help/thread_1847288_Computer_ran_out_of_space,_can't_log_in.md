---
title: "Computer ran out of space, can't log in"
date: 2011-09-20
forum: General Help
---

### Post by omeromer on 2011-09-20
Problem resolved, the final solution is in the first post of page 2, thanks for everyone who helped.

Hello,
First of all I'd like to say a few things:
I'm pretty new to ubuntu and to linux in general.

I've searched before asking, I've found people with problem 

exactly the same as mine by the solutions they've found just didn't work for me.

I need urgent help, I can't use my PC and there are some stuff there that I really need.

I'm running Ubuntu 11.04, and using Ubuntu Classic (since my unity 3d got messed up and 2d is just annoying)



Well my problem is that:

I've installed "recordmydesktop" and then installed "gtk-recordmydesktop".

For some reason it was working as a background process, or didn't stop recording after I've told it to, in any way, it filled up my /tmp folder with 168GB of screen recording data.

It stopped at 168GB because that all the free space I had on my PC.

While my desktop was still running, I deleted all the files, emptied the trash and thought that was it.

After a few minutes I noticed that Nautilus was saying in the lower status bar that I had 0 bytes of free space left.
I noticed none of my programs work as they should, so I just guessed maybe deleting that amount of data wasn't updated or something like that (as I said, I'm new to Linux), so I decided to restart my PC.

My PC restarted, the log in screen loaded, but it looked very weird, like something was limiting it (just like when you start Windows in safe mode, all the windows look simplified so it works smooth).

I tried to log in, there was a black screen for a short period as usual, and then the log in screen showed with the error in the top-right corner saying "the configuration defaults for gnome power manager have not been installed correctly", or something like that.

Nothing is accessible, I tried logging in as a different user, it didn't help, so I decided to Ctrl+shift+F1-6, and look around the web for commands I can use to check my disk space and all of that.

I used the command df, and it showed me that the directory / had 0 bytes left.

I tried going to some of my folders with heavy files, deleted some old stuff that I didn't need anymore but none of that helped, there was still only 0 bytes left.


That's it, I've tried many stuff I've found on Google but none helped me, I rarely ask for help on forums but this time I just gave up.

Sorry for the tl;dr (but I wanted to make sure you know all the details), if you can help me it will be really appreciated.

Thanks (writing this from a different PC in-case you wondered)

---

### Post by sanderd17 on 2011-09-20
Please change the title to Ubuntu instead of Lubuntu. When people read Lubuntu, most automatically think of a low-end pc with possible very little space.

If I were you, I would start a live CD and check out the disk analiser (command is baobab).

---

### Post by omeromer on 2011-09-20
> **sanderd17 said:**
> Please change the title to Ubuntu instead of Lubuntu. When people read Lubuntu, most automatically think of a low-end pc with possible very little space.

If I were you, I would start a live CD and check out the disk analiser (command is baobab).

oh I thought I picked Ubuntu, was kinda far away from the screen so didn't see the l. Though it's impossible to change the tag so I'll just ask the mods to change if they see it. Thanks for the tip I'll try that Live CD tip and post if I run into any trouble

---

### Post by Elfy on 2011-09-20
tag changed ...

---

### Post by omeromer on 2011-09-20
> **forestpiskie said:**
> tag changed ...

Thanks

sandred17: Does booting from a live CD has to be from CD or it can be done using a live flash drive? (with ubuntu on it of-course)

EDIT: Nevermind, just read [here (LiveCD ubuntu documentation)]("https://help.ubuntu.com/community/LiveCD") that it can be done with a flash drive

---

### Post by Elfy on 2011-09-20
Either will be fine :)

and you're welcome.

You might find you've enough space to move though if you boot into the recovery mode - run a root shell and do

```
apt-get clean
```

In fact if you're sure the file is in /tmp you should be able to remove it from there with rm in the same shell.

---

### Post by miasmablk on 2011-09-20
live usb is fine

---

### Post by omeromer on 2011-09-20
> **forestpiskie said:**
> Either will be fine :)

and you're welcome.

You might find you've enough space to move though if you boot into the recovery mode - run a root shell and do

```
apt-get clean
```

In fact if you're sure the file is in /tmp you should be able to remove it from there with rm in the same shell.

Well as I've said, I removed all the files, they're gone, I even removed more unrelated files, but no space was freed, I really don't get how the space thing works.

I'll try running ```
apt-get clean
``` though

---

### Post by Elfy on 2011-09-20
If you deleted them - you need to empty trash.

If you rm them - they are gone.

If you tried removing the file from /tmp you'd have used root to run nautilus I assume - the file would be in the root trash.

If apt-get clean doesn't help - run the live

---

### Post by omeromer on 2011-09-20
I've managed to boot from Live CD, it works great.

I've ran the baobab command and got the disk analyzer, but it shows me data which got me even more confused now, here's a screenshot:

[IMG]http://img268.imageshack.us/img268/5334/screenshotegi.png[/IMG]

As you can see, it says the capacity is 291GB,   290GB is used, 827MB is available, but / is only 81GB big (81GB is about the size of all my regular data like videos images and other stuff)... What's going on?

If you want to see what's going on through remote desktop I don't mind just ask

---

### Post by drs305 on 2011-09-20
Edit: Rewritten

The app is most likely reporting the *combined* size of your system partition as well as anything else mounted in /media. Unmount any mounted devices other than system partition(s) (the Ubuntu partition) to get an accurate reading. 

After unmounting, if you still have a great deal of occupied space in /media look at the Ubuntu partition (assuming you mounted it in /media), it could be a backup issue (sbackup, etc). You can use Baobab to look at a particular folder, so select the /media folder which contains your Ubuntu system.

Look in /media/yourUbuntu/media and see if there is data within. If so, it probably shouldn't be there and is probably the result of a bad backup. Look in /media/yourUbuntu/root/share/.local/Trash/files to see if you have undeleted root trash.

Here is a guide on troubleshooting disk space issues that might help:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by omeromer on 2011-09-20
Thanks! Thanks! Thanks!

For some reason the root trash folder didn't say it was full of files (and by that I mean, it didn't say it was a heavy folder, even when I right clicked-properties it), so I just skipped it, but after reading your guide I tried deleting it ('/root/.local/share/trash/'), it went for like a whole minute and then: 181GB of FREE space!

Thanks for all the help from everyone, you're great people and I can't thank you enough for helping out everyone and me, and you do it all for free out of kindness, one of the biggest reasons I like the open source community.

I will make sure not to bother you anymore :), good night!

---

