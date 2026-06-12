---
title: "Wht's with Lucid. I get repeatedly a login screen even after entering the right pswrd"
date: 2010-08-11
forum: General Help
---

### Post by yperionas on 2010-08-11
What's going on with the Lucid distribution. Does everybody has a problem login in or its a problem related to my laptop? I have a sony vaio vgn-sr29vn.
More specifically, when i get to the login screen i put my password then tries to load some visual interface tools, then i get a black screen and then back to the login environment.

Any ideas of how to degrade back to the previous distribution?  I actually tried to run it at the boot menu but i get the same lucid login screen and everything gets stuck, keyboard and mouse doesnt work.

Does anybody had the same problem and how was solved? Thank you in advance.

---

### Post by dabl on 2010-08-11
That would be #10 here: [http://kubuntuforums.net/forums/index.php?topic=3099811.0](http://kubuntuforums.net/forums/index.php?topic=3099811.0)

---

### Post by yperionas on 2010-08-12
Thanks dabl. Well I've tried some of the threads Ive found there some are quite old.
Tried so far:

deleting the language pack: sudo apt-get remove language-pack-kde-en
I rebooted and the login problem remains.

renaming mv /home/lefteris/.kde /home/lefteris/kdebackup
I rebooted and the login problem remains.

deleting ICEauthority and Xauthority hidden files.
I rebooted and the login problem remains.

removing kdm and reinstalling it: sudo aptitude remove kdm , then: sudo aptitude update && sudo aptitude install kdm
I rebooted and the login problem remains.

Whats left...
Btw when i try to access the virtual console with Ctrl+Alt+F1 the screen gets black, goes back the login screen and then its stucks! nothing works, keyboard or mouse.

pfffff why did i do the stupid upgrade to lucid i wonder.

---

### Post by dabl on 2010-08-12
> **yperionas said:**
> 

Whats left...


Full filesystem?  You'll have to boot Recovery mode, and at the "/" prompt run ```
du -h --max-depth=1 | sort -n
```

This will show you where the largest amount of space is used.

---

### Post by yperionas on 2010-08-13
Hey dabl thanks for your reply! Appreciate that.

I ran the command you've suggested but i just get a list of folders with their size. If i remember well the largest space at the bottom of the list was only up to 50MB no more and there were not more than 3-4 folders of the same or similar size.
I am not sure the partition is full but If i remember well I had given many gigas of space. I would say up to 60 GBytes space.  I use the windows mostly for multimedia and linux for work. But I could be wrong and missing something here.

I have tried running startx but the GUI appears with a black forzen screen and with no mouse and keyboard functionality. Actually i need to push down the power button to switch off the pc.

Then i tried installing the kubuntu desktop. Then the lucid desktop environment appears (no black screen) but the pc again gets frozen.

I checked Xorg.0.log file where i didnt find any errors ,just informational (II) notes.
kern.log came up with the following error: Cannot read proc file system, 1.

I have noticed also something else. when grub starts and i get the booting menu i have the following choices:

Ubuntu 9.10, kernel 2.6.31-14-generic
Ubuntu 8.10, kernel 2.6.27-11-generic 
Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)

windows vista OS

The  question is. Is there a possibility after the upgrade to Lucid 10.04 im  still trying to run the 9.10 karmic koala and thats the problem?  Shouldnt the Lucid kernel appear at the booting menu? Why it does not?

---

### Post by dabl on 2010-08-13
> **yperionas said:**
> 

 i need to push down the power button to switch off the pc.



I'll bet you do NOT have to do that, and that's very hard on a journalled filesystem (i.e. you could lose data).  Next time you think it's hung, press Alt-SysRq and while holding them down, press slowly in sequence R S E I U B

That will perform a proper shutdown of the filesystem, and reboot.

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

OK, on the real problem.

> 
kern.log came up with the following error: Cannot read proc file system, 1.

I've never seen that -- it can't be good.  Google says:

[https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/565288](https://bugs.launchpad.net/ubuntu/+source/rsyslog/+bug/565288)

and

[https://bugs.launchpad.net/ubuntu/lucid/+source/rsyslog/+bug/523610](https://bugs.launchpad.net/ubuntu/lucid/+source/rsyslog/+bug/523610)

(scroll down to #33)


But it doesn't say that prevents a user from logging in -- I think this error is _not_ the cause of your "login loop".  That is normally caused by either (a) full filesystem, or (b) root use of GUI apps (i.e. starting dolphin with "sudo" instead of "kdesudo", resulting in changed permissions on the applicable files in the user's home folder.

If you want to test my theory that the problem is limited to your user, you can boot recovery mode and then create a new user account.  Then restart and login as the new user, and I'll bet that user has no such login loop.  If he does, then that will strongly suggest that you _do_ have a full filesystem (or else that there is a third and previously unknown cause of the login loop).

To see how much free space is available on your filesystem, run

```
df -h
```

---

