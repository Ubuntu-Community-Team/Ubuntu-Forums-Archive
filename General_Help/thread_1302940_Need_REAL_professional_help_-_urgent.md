---
title: "Need REAL professional help - urgent"
date: 2009-10-27
forum: General Help
---

### Post by Atomic_kemo on 2009-10-27
Hi everyone I've switched from Windows to Ubuntu 9.04 about a week ago & I already feel very comfortable, actually better!

_***NOTE***_: I'm really lost in the Linux world because I still don't know my way around & my situation will prove it!!

I still haven't removed Windows but I hadn't booted since.

I have 2 NTFS formatted HDDs:
 First: Divided into 75% for storage, 25% for Windows
 Second: Wasn't used until I repartitioned 2 ext3 drives for Ubuntu. But for no good reason I thought I'd try openSUSE (don't ask!!) 

So I made a third drive on the second for SUSE, so far so good?!

Stupidly I partioned the SUSE drive from its Live cd not from my installed Ubuntu ](*,)

Then I ran SUSE, installed all updates & all my hardware ran well, but:

[LIST=1]
[*]I downloaded OpenSUSE KDE - & I really like Gnome
[*]I noticed sth stupid that I didn't know how to change which was that every thing must be accessed in SuperUser mode (e.g there is regular terminal that you can't do much with it & there is SuperUser terminal which is like regualr Ubuntu's)
[*]I liked Ubuntu more (& I liked Kubuntu more than openSUSE)
[/LIST]
Next I restarted to configure updates & there was a surprise; GRUB has changed into a SUSE green theme!!!

I opened SUSE again & after 30 mins. I felt it's LAME & decided to return to Ubuntu :smile:

But when I tried to boot Ubuntu from GRUB it said that the kernel file was missing(& it isn't) so I restarted & tried again but I got the same error so I decided to boot back to Windows (I've only used SUSE for an hour & it was useless for me) & guess what?
After getting used to the speed of Linux, returning to Windows was a bit hard so I rushed it & it crashed so **I restarted manually** (leaving a memory of Windows somewhere as it didn't shutdown properly)

I thouht to use GParted from Ubuntu's Live CD to *format* SUSE's drive & again stupidly I did so! ](*,)](*,)

Continuing this computer fairy tale, NO of the OS booted, acually GRUB didn't boot giving error 17 then after a restart it gave error 22

I'm now using Ubuntu's Live CD to write this post & 
I looked at :
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

& I couldn't do what these posts said (didn't understand) although I tried   ```
find /boot/grub/stage1
```  but I got error 15 from GRUB, although I mounted my partition manually, opened that directory & found that file! :confused:

All I need know is Ubuntu I don't care about Windows but I want my stored files to keep safe & my PC not to be damaged

I was waiting for Ubuntu 9.10 stable release on Oct. 29th
So if it's easier to install the new Ubuntu then please tell me how thoroughly to fix all errors, also if a small distro can solve the problem(DSL,Puppy) I can download & use it 

So please this is very urgent as you can see so note that I'm worse than a newbie because I'm used to Windows so please give **VERY** specific instrunctions & stay in touch.

---

### Post by P4man on 2009-10-27
If you want professional support, and its urgent, perhaps you could consider  this:
[http://shop.canonical.com/index.php?cPath=31_32&osCsid=14559cef877f3a77f91b4efde1a951ca](http://shop.canonical.com/index.php?cPath=31_32&osCsid=14559cef877f3a77f91b4efde1a951ca)

ill read your post at my ease later and provide free amateur support :)

(Im not being cynical or anything here, most ppl dont know you can actually get professional support from canonical even though its not free ).

---

### Post by Anonymousable on 2009-10-27
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) << That was the right way to go.

I had a very similar problem a couple of days ago. It's solved using grub-install.

Use grub-install with the device of the hard drive, then follow those instructions - that should work.

---

### Post by Giblet5 on 2009-10-27
This is how we ALL learned.

Open a terminal window on your LiveCD, run the following command, and post the output in this thread: ```
sudo fdisk -l
```

See if you can identify the Ubuntu / partition. It might be obvious to you. Maybe not.

Also write down which disk drive is listed first.

If you're not sure, pick a likely ext3 filesystem and run ```
sudo mount /dev/sd[COLOR="DarkRed"]XX[/COLOR] /mnt
``` where [COLOR="DarkRed"]XX[/COLOR] is the partition you think is the right one.

Now you can browse that from /mnt and verify.

IF THAT IS CORRECT execute these commands:
```
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /dev /mnt/dev
chroot /mnt bash
sudo grub-install /dev/sd[COLOR="DarkRed"]X[/COLOR]
sudo reboot
```

Where [COLOR="DarkRed"]X[/COLOR] is that first drive listed by fdisk above.

That should boot the old grub menu and everything should be back the way it was.

If not, we're here...

---

### Post by t0p on 2009-10-27
I agree with p4man.  If you want professional help, go pay for professional help.

Everyone who offers help here is a volunteer.  We don't get paid for helping users.  And your thread title is offensive to me.  You want "REAL professional help" as opposed to our unreal amateur help, and you say it's urgent, demanding the help NOW.

Give Canonical a call.  They'll be happy to provide you with REAL professional help.

---

### Post by Atomic_kemo on 2009-10-28
Thanks Giblet5 I followed your instructions after following [catlett]("http://ubuntuforums.org/member.php?u=79105")'s successfully & I'm back to my Ubuntu

Guys I really don't mean PROFESSIONAL I mean someone who knows what he is doing!!

---

### Post by murderslastcrow on 2009-10-28
Great to see you got it solved without getting rid of your partitions. However, if you dislike SUSE you can always delete its partition and resize Ubuntu's stuff. This will take some time, of course, and it would be easier to simply delete all the Linux partitions and install Ubuntu in the freed space if you don't have important files on there. If not, you will need to install GRUB from the LiveCD or edit your menu.lst file to reflect the changes to your partitions.

:3 But yeah, good to see you've already learned so much! Good luck with the rest of your Ubuntu experience (which will be much less stressful, I am sure XD).

---

### Post by Giblet5 on 2009-10-28
> **Atomic_kemo said:**
> Thanks Giblet5 I followed your instructions after following [catlett]("http://ubuntuforums.org/member.php?u=79105")'s successfully & I'm back to my Ubuntu

Guys I really don't mean PROFESSIONAL I mean someone who knows what he is doing!!


Good. You're doing everything right (fearless curiosity is almost always the best policy).

As for all the ire your subject text raised, I assumed you meant "Mad Linux Skillz" and was correct. The others had just guzzled their 20th mug of espresso I think. Don't sweat it.

---

