---
title: "A hair pulling problem!!!"
date: 2010-02-11
forum: General Help
---

### Post by Jonny87 on 2010-02-11
Ok so the other day I installed Ubuntu 9:10, and yesterday I took it to a mates place and did some updates and installed some software.
Then last night I was in the process of copying some files across from my Library drive (500GB Sata, still quite new) and then the copying stoped on one particular folder and came up with an error. It was an Input/Output error (have had this before on Linux Mint 8 once or twice but don't know how to get around it or fix it, if any one could help wiht this as well I'd aprectiate it). I then continued to try copying and to work out the problem. Then I think I somehow over loaded things cause it seemed to have frozen I managed to force quit it and then I end up my hair pulling problem.
The extra desktop effects diabled themselves for one, and now it wont let me enable them again. it comes up wiht an error "Unable to enable desktop effects."

If that was it I wouldn't be so worried. Now I can't access any other drives i.e. my Library drive. it comes up with a message "Unable to Mount" "Authentification Needed" I've tried everything I can but can't seem to work out how to fix it.

Is there a way I can get it back to the way it was with out lossing all the updates and software etc??

Please Help.

---

### Post by elliotn on 2010-02-11
The input/output error mostly happens if the drive is full or drive not found.

The effects. Go to terminal and type and type compiz it would tell u the error

---

### Post by Jonny87 on 2010-02-12
But the drives were far from full. I always check that theres enough space when I copy something across to another drive, and there was. Is there anything else that could cause it?
 
Will try the compiz though thanks. What about the drive access thing? Thats bothering me at the moment cause I'm wanting to use Ubuntu as much as possible to get use to it and familure with it but can't access my library drive. If I want to use it I have to reboot into Mint 8 or XP.
 
*note*
Aside from the effects and drive access, all else seems to working fine. Everything operates as normal.

---

### Post by bruno9779 on 2010-02-12
Could you please post the content of your /etc/fstab ?

with all the drives plugged. (sata drives? USB drives?)

Run compiz from the terminal to have a precise error message as suggested by elliotn and post that too

---

### Post by Jonny87 on 2010-02-12
K will post fstab info next post.
 
Have run "compiz" and got the following;
 
"aborting and using fallback /user/bin/metacity"
 
It then drops the curser to the next line with no text. It's been sitting like that for awhile. If I try closing the terminal, it says that its still running a process so I've just left it to keep doing its thing.
Is this normal?

---

### Post by sgosnell on 2010-02-12
No, it's not normal.  Stop the process with Ctrl-C, and then post the fstab info as requested.

---

### Post by Jonny87 on 2010-02-12
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=9ddd5bb7-84b0-4ab7-b2e8-3b62acccf62e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=1fb73bb7-8615-4fcc-8ff2-994fbef14a55 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
 
 
 
Im guessing that this is the needed info?
Have just stoped compiz. Since stoping it, it seems to be acting strange. almost frozen but not. I can do a couple things but some things like closing windows wont. the buttons in the top right of windows to minamize, maximize and close the window have disapared.

---

### Post by sgosnell on 2010-02-12
That's a rather strange configuration in fstab.  I've never seen sda1 used for swap before.  It's possible, but unusual.  Any idea how that happened?

Your theme may have been changed.  Different themes have different icons for the minimize/maximize/close buttons.  Have you tried changing the theme and seeing if they come back?

---

### Post by Jonny87 on 2010-02-12
It could have just been the way that I set things up on the install. I'm still learning linux and just starting to get a handle on it. still got a lot to learn though. Is that bad to have it as sda1? What should it be?
So any ideas on whats stoping my drive access and being able change effects.
 
The only drives I can access is the Ubuntu filesystem, and any usb drives i.e. my i-pod, usb sticks etc. The internal dives such as my 500GB Sata NTFS Library drive wont mount as mentioned above.

---

### Post by Claus7 on 2010-02-12
Hello,

I'll try to fill in giving information from my recent experience.

1st: Do not try to write new things on the hdd. Probably either is corrupted and its life is getting to end sooner or later or it is somehow corrupted. 

2nd: The input/output error you get is either a problem of transferring data to an unmounted drive (possibly it gets unmounted because of being faulty) or because it has an error.

3rd: Take BACKUP if you can with the best possible way you can: dd command, dd_rescue command, cp command.

4th: Then I think that you have to check your hdd 
consistency with commands like e2fsck while it is unmounted.

I'm personally in the 4th step and waiting for the process to take an end, yet my situation has to do with an external hdd. ([http://ubuntuforums.org/showthread.php?t=1401700&page=2](http://ubuntuforums.org/showthread.php?t=1401700&page=2))
Why this thing happens is beyond my knowledge.

Hope I gave some hints,
Regards!

---

### Post by Jonny87 on 2010-02-12
Ok I'm not sure how much this means but I've just noticed that if I log into root neither of these problems occur. It works perffectly fine as if theres been no problem. I mean I can access the drives and change the effects just like I used too on my user login.
 
As for the last post all should be fine, one drive was brand new and as for the other its had no sign of trouble. Will check the dives just incase though.
 
Thanks for all the help so far though guys:p
Please, any other ideas let me know.

---

### Post by sgosnell on 2010-02-12
You can probably access the drives, they just aren't being automounted when you plug them in.  You can mount them from a terminal, or from Nautilus by clicking on them.  Do a search on 'USB drives won't automount', both here and in Google and see if you find a solution.

Normally the swap partition is on sda5, which is inside an extended partition sda3, and sda1 is the / partition.  I don't know that your setup will cause problems, but it is somewhat unusual.

---

### Post by Jonny87 on 2010-02-13
#-o #-o #-o
Man do I feel like an IDIOT. I worked out the issue. It must have been from early on when I was trying to get around the input/output error. I had the session setting on the login set to failsafe GNOME (I think thats what it was called) instead of GNOME. I forgot all about it till last night. Man... #-o
 
As for the swap thing, I didn't realize. I just knew that linux need it, I didn't think it really mattered. It hasn't seemed to have been causing any trouble so I'll leave it for now and will just keep it mind if I ever reconfigure things.
 
Anyway I just want to finish by saying sorry for waisting your time to all that have looked at this thread hoping to help.

---

### Post by Miljet on 2010-02-13
You don't have to apologize for wasting anyone's time. That is what we are here for. Most problems do tend to turn out to be trivial mistakes in the end. Glad that you got it sorted.

---

### Post by sgosnell on 2010-02-13
I doubt the partition configuration will cause any problems, it's just unusual so I noticed it.  If it works, don't worry about it.

---

### Post by Jonny87 on 2010-02-14
OK cheers for that. Am enjoying Ubuntu though. It's quite good.

---

### Post by sgosnell on 2010-02-14
Yes, I like it.  I tried out all the major Linux distros, and most of the Ubuntu offshoots, especially the eee-pc specific ones, before settling on standard Ubuntu.  They're all pretty similar, using the same kernel and many of the same packages, but different interfaces and some different desktop environments.  Which one is best is a matter of taste, mostly, but they're all better than Windows.  I haven't booted Windows on my computers in a long time, a couple of years at least.  Ubuntu does take a little investment in time and effort, just as Windows did long ago, but it's not a huge investment, and it's certainly worth it.

---

### Post by Jonny87 on 2010-02-14
I know what you mean, I was getting sick of all the trouble I was having on windows with things crashing etc. Then a few months ago I brought a computer mag that had a free cd of free software etc. In that cd was a copy of Puppy Linux, in search for something new I gave it a go. This was my introduction to linux and I was impressed. With this I decided to look into linux abit more, so I did abit of reseach about linux and how it compears to Windows. Lets say I was liking what I was reading. I then found out about Linux Mint 8, so I downloaded it and gave it ago. Again I was impressed and then as I got ussed to it I decided I would like to give Ubuntu ago since Mint was based off it and from what I had read it was quite popular. Then that same Mag that I mentioned earlier had a copy of Ubuntu 9:10, so I was quite stoked as I have limited internet access at the moment. And well so far I linke what I see.
 
And I love the fact that theres forums like this that I can get any help I need from loads of friendly and helpful users, something that windows lacks abit (if there is such a thing for windows it's not to well advertized). I also like the fact of lower virus risk and less need to defrag. Oh and the fact that I can get any software I need to do the job for FREE and not have to worry bout breaking any laws, big plus!
 
I think its clear that I'm a linux convert. I plan to learn as much as possible about it as I can so that as I save people from the windows commercial world and get them on to the better life of linux, I can assist them and help them through any trouble they may have getting used to. Anyway thats my story.:p

---

