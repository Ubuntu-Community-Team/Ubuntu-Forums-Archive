---
title: "rm -rf / ?"
date: 2010-01-23
forum: General Help
---

### Post by W.Y.N.F.S on 2010-01-23
why this don`t work?

```
deniss@deniss-desktop:~$ su root
Password: 
root@deniss-desktop:/home/deniss# rm -rf /
rm: cannot remove root directory `/'
root@deniss-desktop:/home/deniss# 
```

---

### Post by jamesisin on 2010-01-23
What exactly are you trying to accomplish?  If that command were to succeed you would kill your system.

---

### Post by W.Y.N.F.S on 2010-01-23
I want to see how. 
And will it remove everything from mounted external disks or not.

---

### Post by W.Y.N.F.S on 2010-01-23
everyone say that it will kill my system, but I see what it does NOT

---

### Post by jamesisin on 2010-01-23
I believe that -r will not follow links but only delete the link.  Is that what you are asking?

I trust you are testing this in a sandbox or on a test system (virtual or otherwise)?

---

### Post by d3v1150m471c on 2010-01-23
As long as you know what you're doing. Hey, knock yourself out. I broke ubuntu 9 million times before I got good with linux but sometimes that experience is the best teacher. Especially if you don't take the cheap way out and do a reinstall to fix your problems.

---

### Post by W.Y.N.F.S on 2010-01-23
I know what exactly I want to do, and what I want to get from it. but I don`t understand why it doesn`t work. I will never believe in anything while I don`t see it. maybe someday I will need to destroy all information from my computer quickly, I want to know if I can use this command, or I should not to waste my time.

---

### Post by eyelessfade on 2010-01-23
Your "problem" is that debian has made rm a bit safer. --preserve-root is automatically added to your command. What you want to do is ```
#rm -rf --no-preserve-root /
``` Congratulation your system is gone.

---

### Post by ankspo71 on 2010-01-23
Just out of curiosity,
what happens when rm reaches the /bin/rm file?
Does it get stuck and the person is left with some files on the system? :D

-----
**As a reminder, nobody use any rm commands from this thread unless you want your system destroyed.**

---

### Post by mick222 on 2010-01-23
> **eyelessfade said:**
> Your "problem" is that debian has made rm a bit safer. --preserve-root is automatically added to your command. What you want to do is ```
#rm -rf --no-preserve-root /
``` Congratulation your system is gone.

I thought we were not alowed to post unsafe commands in the forums.Although that is pretty hard to do by mistake.

---

### Post by John Bean on 2010-01-23
> **ankspo71 said:**
> Just out of curiosity,
what happens when rm reaches the /bin/rm file?

It gets removed. The file is only important if it needs to be loaded into memory.

Programs run in memory.

---

### Post by fjf314 on 2010-01-23
If you really just want to watch what happens, this should satisfy your curiosity without all of the hassle:

[http://www.youtube.com/watch?v=D4fzInlyYQo](http://www.youtube.com/watch?v=D4fzInlyYQo)

---

### Post by ankspo71 on 2010-01-23
Thanks John Bean and fjf314,
I wasn't curious enough to actually try it. I was just curious to know if the poster was going to accomplish what he/she wanted to do. And the video satisfied my curiosity too :D
Thanks.

---

### Post by d3v1150m471c on 2010-01-23
I think this thread is a good heads up regarding this malicious command. Personally, I don't think it meets the criteria for an accident waiting to happen, but rather the exact opposite. Then again i'm not forum staff...

---

### Post by Techsnap on 2010-01-23
**Don't actually do this if you don't want to loose everything on your computer**

Stick a wildcard after /, so it's /* and you need to run it as root as most of the folders under there are going to be out of a normal user permissions set. Why you'd want to do this? I don't know, it's only going to delete everything there's no secret easter egg or anything.

BTW make sure you unmount your other drives first if any.

---

### Post by c0mput3r_n3rD on 2010-01-23
> **fjf314 said:**
> If you really just want to watch what happens, this should satisfy your curiosity without all of the hassle:

[http://www.youtube.com/watch?v=D4fzInlyYQo](http://www.youtube.com/watch?v=D4fzInlyYQo)


Haha wow, I've never seen that before.  Yeah you don't need to actually do it yourself if you can see it done right there! What's to really know? The O.S. wont crash because most of it is in memory, it just wont function what so ever, and if you try and view your files nothing will be there.  You must have a lot of time on your hands lol.

---

### Post by Techsnap on 2010-01-23
> The O.S. wont crash because most of it is in memory

It will if you try to get it to do something, though it's unlikely because any launchers would be deleted. Commands won't work either, same reason.

---

### Post by c0mput3r_n3rD on 2010-01-23
> **Techsnap said:**
> Stick a wildcard after /, so it's /* and you need to run it as root as most of the folders under there are going to be out of a normal user permissions set. Why you'd want to do this? I don't know, it's only going to delete everything there's no secret easter egg or anything.


You don't have to use a wildcard after because the -r option means it's recursive and keeps going until it gets to the end of (in this case) every where, and he is root; first command was sudo su.

---

### Post by Techsnap on 2010-01-23
I know, but using a wildcard usually overrides it and will continue to delete it.

---

### Post by c0mput3r_n3rD on 2010-01-23
> **Techsnap said:**
> It will if you try to get it to do something, though it's unlikely because any launchers would be deleted. Commands won't work either, same reason.


Lol well obviously it wont operate, though the screen wont just shut out on you either.  And I'm sure you could actually click on things and you would just get weird error messages with no type of readability .  I don't think it would crash....  Let's get this guy to try it then lol

EDIT: By the way **DO NOT ACTUALLY DO THIS UNLESS YOUR WILLING TO HAVE SOMETHING DEVASTATING HAPPEN (THIS IS MY DISCLAIMER)**  but using the -i command will prompt before deleting anything, so if you want to know whether or not it would work, you could use that method.  

And just look at the youtube video; he clicks on things and it doesn't crash.  If you delete from HDD it does not delete from RAM.

---

### Post by Techsnap on 2010-01-23
It's possible it will, because it would be highly unstable :P It's not going to give you any errors, it will just lock up.

---

### Post by fjf314 on 2010-01-23
> **c0mput3r_n3rD said:**
> Haha wow, I've never seen that before.  Yeah you don't need to actually do it yourself if you can see it done right there! What's to really know? The O.S. wont crash because most of it is in memory, it just wont function what so ever, and if you try and view your files nothing will be there.  You must have a lot of time on your hands lol.

Just to clarify, I didn't create that video. I had just happened to see it once before and figured a link to it would be handy for this thread.

---

### Post by c0mput3r_n3rD on 2010-01-23
> **fjf314 said:**
> Just to clarify, I didn't create that video. I had just happened to see it once before and figured a link to it would be handy for this thread.


Well I figured you wouldn't be crazy enough to do that haha.  Why any body would, I'm not sure.  I guess if you were going for a fresh install it would be neat to do  :popcorn:

---

### Post by fjf314 on 2010-01-23
The creator set up a VM of Ubuntu just for the purposes of making the video, probably so it could be used in instances like this, haha.

---

### Post by 3rdalbum on 2010-01-23
It will destroy any mounted disks, and it actually won't delete /bin/rm until 'rm' finishes. It will appear to delete it, but actually keep it on disk until the file is no longer busy.

I'm not sure what would happen when it deletes everything in /dev - I'd be sure that it would break the system right then and there!

---

### Post by c0mput3r_n3rD on 2010-01-23
Does everybody just think that the system would just crash?  I guarantee you could run it for a quite a while messing around clicking on things (not being able to actually do anything) but it should stay up!  In the video he click on Applications, clicks on a program, opens terminal, types a command, and shuts down the box using the button.  Just think, especially if your system has like 2Gb's of RAM, you have probably 512Mb of the whole OS in there, which would be everything needed to run it independent of the HDD until a program needs to execute, when it tries to execute the program (which commands are programs too), you would just get an error message that is a part of the O.S. therefore loaded in RAM.  Error detection is most likely in RAM for such stability.  

I don't know some one prove me wrong I'm curious!! That's just my educated opinion...

---

### Post by Techsnap on 2010-01-23
As soon as the system tries to do anything it will probably lock up, got a job ready to run in memory for example? Also if you were to plug a USB Flash drive in or a CD it's likely to lock up.

---

### Post by ibuclaw on 2010-01-23
> **3rdalbum said:**
> It will destroy any mounted disks, and it actually won't delete /bin/rm until 'rm' finishes. It will appear to delete it, but actually keep it on disk until the file is no longer busy.

I'm not sure what would happen when it deletes everything in /dev - I'd be sure that it would break the system right then and there!

/dev itself is a volatile filesystem that gets recreated/populated everytime you boot/reboot the workstation.

The most damage that can happen is that already running applications just start complaining (especially ones that require /dev/pts to exist) whilst the system is still running.

You should be able to recreate the /dev filesystem if you ever (accidentally? curiously?) remove it whilst the system is still live.

I do believe it is something along this sequence (never tried it though).
```

# Unmount the already existing filesystems
umount /dev/pts
umount /dev/shm
umount /dev

# Create /dev
mount -t tmpfs none /dev -o mode=0755

# Copy static devices into /dev
cp -a /lib/udev/devices/* /dev/

# Regenerate dynamic devices
udevd --daemon
udevadm trigger
udevadm settle

```

Of course, you require /sys and /proc to be present beforehand.
```

mount -t proc proc /proc
mount -t sysfs sysfs /sys

```

Regards
Iain

---

### Post by c0mput3r_n3rD on 2010-01-23
> **Techsnap said:**
> As soon as the system tries to do anything it will probably lock up, got a job ready to run in memory for example? Also if you were to plug a USB Flash drive in or a CD it's likely to lock up.


No see you're not understanding.  Watch the video first, and you'll see that it doesn't lock up, and when you try to run a command, the O.S. acts first and goes to fetch the binary file in what ever location.  If location doesn't exist a default error message set up in the KERNEL which is IN RAM pops up and O.S. never lets go of control.  Learn a little bit about programming and a little bit about the CS and you'll know what I'm talking about.  

Oh! You want to emulate that?  Boot from livecd, while it's up, take out livecd, and there you go, same affect! Try it out if you guys don't believe me.

---

### Post by Techsnap on 2010-01-23
For goodness sake I've done it before. Sheesh. I tried it on an old Fedora system and it DID lock up after about 20 minutes. It depends on how you were using the system when you issued the command. I'm not saying that deleting your root partition is going to definitely without a doubt going to lock the system up but it CAN happen, I know it can because I've tried it. Who cares anyway, if you've deleted your root partition it doesn't ******* matter what the system does because it's most likely you'd be reinstalling anyway.

---

### Post by c0mput3r_n3rD on 2010-01-23
> **Techsnap said:**
> For goodness sake I've done it before. Sheesh. I tried it on an old Fedora system and it DID lock up after about 20 minutes. It depends on how you were using the system when you issued the command. I'm not saying that deleting your root partition is going to definitely without a doubt going to lock the system up but it CAN happen, I know it can because I've tried it. Who cares anyway, if you've deleted your root partition it doesn't ******* matter what the system does because it's most likely you'd be reinstalling anyway.


Hey there's no reason to get all heated and start cursing and everything.  Of course it would would lock up, especially at the 20 minute mark, I wans't arguing that, only that it would not instantly freeze after doing the smallest thing.  I was not trying to start a fight, just felt like you were being a bit repetitive and wasn't understand what I was saying so I was trying to explain, and teach you or any one else reading how a system works on a bit of a deeper level than the GUI.

---

### Post by Techsnap on 2010-01-23
Did I ever say it was going to instantly freeze. 

> I was trying to explain, and teach you or any one else reading how a system works on a bit of a deeper level than the GUI.

See you're using the snide comments yet again, then you wonder why I'm getting pissed off. I KNOW how it works, and I was just saying it HAS the possibility of locking up, I never once said it's going to totally lock the instant you issue that command.

---

### Post by PmDematagoda on 2010-01-23
Ok, it would seem like this thread has just about reached it's end. The issue in question has already been discussed before and a fix already available, so there really does not seem to be much of a point in discussing this again.

Thread closed.

---

