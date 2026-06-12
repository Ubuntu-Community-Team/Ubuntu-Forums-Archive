---
title: "Won't start anymore after grub!  :confused:"
date: 2010-11-24
forum: General Help
---

### Post by mathgirl on 2010-11-24
I've been using Wubi Ubuntu and XP for quite a while now.  Today XP starts fine, but if I choose Ubuntu, it flashes

hd(0,) NTSF5
error: not found

extremely fast and restarts again.  I can't quite read it because it flashes so quickly.  The only two other forum mentions I can find are right after people installed Wubi and the advice given is to just reinstall.  But I use ubuntu all the time and have lots of data I don't want to throw away.  Can somebody help me?

---

### Post by The Decrypter on 2010-11-24
Hi,

This has happened to me once before with some other boot software. I downloaded Ultimate Boot CD and used some of the tools under the Boot Management menu. I was able to get back into Ubuntu Desktop install and move all the data to a USB drive.

Hope this helps.


[SIZE=2][/SIZE]

---

### Post by bcbc on 2010-11-25
Are you on Lucid Lynx 10.04? If so, then this applies:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

Note, in future, it's advisable to avoid updating grub-pc and grub-common unless you know specifically a reason for doing so. Most of them are unnecessary and just seem to break wubi installs.

---

### Post by isaac_23 on 2010-11-26
hi, I'm using 10.10 ubuntu, downloaded from wibu, and im experiencing the same problem. your link is very useful, but a little unclear as to whether downloading a live CD is necessary in the case of 10.10, or just copying the wubildr file should suffice. incidentally i have just copied the file across, and the problem persists. thanks in anticipation
isaac

---

### Post by Hippytaff on 2010-11-26
Wubi is intended for evaluating ubuntu. If you intend using ubuntu long term then it is probably best to do a 'real' install, and dual boot with windows. Wubi brakes after a bit...doesn't take well to updates :-)

---

### Post by bcbc on 2010-11-26
> **isaac_23 said:**
> hi, I'm using 10.10 ubuntu, downloaded from wibu, and im experiencing the same problem. your link is very useful, but a little unclear as to whether downloading a live CD is necessary in the case of 10.10, or just copying the wubildr file should suffice. incidentally i have just copied the file across, and the problem persists. thanks in anticipation
isaac

That wubildr trick seemed to work for the upgrade from 10.04 to 10.10. If there was a grub-update released for 10.10, then it doesn't necessarily mean it would work. It's always a good idea to have a live CD - use Ubuntu for any length of time and you'll see it's a necessary item.

I'd go for the edit of the grub.cfg as it seems to work on any broken wubi install - it's just the wubildr fix is much easier as you can do it from windows so it's worth trying before hand.

> **Hippytaff said:**
> Wubi is intended for evaluating ubuntu. If you intend using ubuntu long term then it is probably best to do a 'real' install, and dual boot with windows. Wubi brakes after a bit...doesn't take well to updates :-)

I'm having a hard time defending wubi these days, however, I don't think it's fair to say it 'breaks after a bit... doesn't take well to updates'. What is fair to say is that the grub developers (aka Colin Watson) has known about problems in grub that adversely affect Wubi installs, and yet he persists in pushing out grub updates without bothering to fix them. So if you want to say, that's Wubi. Then fine, you're right. But I am puzzled as to what Mr Watson is thinking - brilliant though he most probably is - because it makes no sense to me. He knows the bugs are still there, therefore he knows that users will have broken installs, yet he feels the update is OK.

I understand his latest update was a cosmetic fix targeted at wubi installs only and though the fix works, it doesn't actually do anything (being cosmetic) yet comes at great expense to all the other newbie Ubuntu users who probably don't (and shouldn't) have to know what grub is.

I absolutely agree you shouldn't use Wubi long term - but I think you should be able to install it, and run updates without it breaking the first time.

---

### Post by Hippytaff on 2010-11-26
Fair enough, I don't know that much about it, thanks...I've learned something :-) grub updates break wubi installs :-)

---

### Post by bcbc on 2010-11-26
> **Hippytaff said:**
> Fair enough, I don't know that much about it, thanks...I've learned something :-) grub updates break wubi installs :-)

I am pretty frustrated with all the broken wubi installs from the latest grub update. ](*,) To the new ubuntu user there isn't a distinction between grub and wubi, so to be fair, I am splitting hairs. :)

---

### Post by Hippytaff on 2010-11-26
I know the difference, but I wasn't aware that it was grubs fault, I thought it was that wubi wasn't very good :-)

Thanks to you I now know better :-)

---

### Post by isaac_23 on 2010-11-30
hello again, 
I had some troubles getting a live CD to work, and noticed that your username was also involved in those threads, so thankyou twice. however, im afraid i have a new problem. i couldnt locate the root.disk, so just ploughed through with your instructions at:
[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)
assuming (?) that /dev/sda1 was the place to go but, perhaps unsurprisingly, happened upon this error:

sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
/media/win/ubuntu/disks/root.disk: No such file or directory

now as mentioned, i had to get through some hurdles to get the live CD to work, and there is a chance i fundamentally altered the ubuntu part in my frustration. do you think this is the likely cause, and is there a possibility of recovering data?

thanks again
Isaac

---

### Post by isaac_23 on 2010-11-30
incidentally, the C:/ubuntu directory, whilst having the folders expected, is empty of files, apart from the winboot folder, which contains the wubi ldr and bootstrap files.

---

### Post by bcbc on 2010-11-30
> **isaac_23 said:**
> incidentally, the C:/ubuntu directory, whilst having the folders expected, is empty of files, apart from the winboot folder, which contains the wubi ldr and bootstrap files.

If the c:\ubuntu\disks directory does not exist, then you have some other problem. Sometimes Windows will automatically fix and move corrupted files to a hidden c:\FOUND.000 directory. This might happened if you did a hard shutdown. But unless you can find these and restore them so you have a c:\ubuntu\disks\root.disk you won't be able to boot Ubuntu. (Do a search for root.disk - might help find it).

Also running check disk is a good idea (My computer, right-click on C: drive, Properties, Tools, Check disk for errors, Fix automatically - reboot to complete).

---

### Post by mathgirl on 2010-11-30
bcbc:  I'm not quite fixed yet, but you've got me on the right track.  I understand what's happening now and for that I thank you!  After editing as per your instructions, I'm able to get the grub menu to actually accept the choice of Ubuntu.  But then it says ```
error: unknown command 'drivemap'
``` and then immediately restarts in Windows.  Would it help if I copied my file?  Or is there an example file I could just copy verbatim?

Thanks again for helping me get this working again!

P.S.  I didn't realize Wubi was thought of as a temporary install.  Canonical sells it as "a great way to get Ubuntu on your windows computer."

---

### Post by bcbc on 2010-11-30
> **mathgirl said:**
> bcbc:  I'm not quite fixed yet, but you've got me on the right track.  I understand what's happening now and for that I thank you!  After editing as per your instructions, I'm able to get the grub menu to actually accept the choice of Ubuntu.  But then it says ```
error: unknown command 'drivemap'
``` and then immediately restarts in Windows.  Would it help if I copied my file?  Or is there an example file I could just copy verbatim?

Thanks again for helping me get this working again!

P.S.  I didn't realize Wubi was thought of as a temporary install.  Canonical sells it as "a great way to get Ubuntu on your windows computer."

The drivemap command is usually part of booting windows. You actually only need a single "menuentry" block to boot Ubuntu. You should take the very first one and then you can remove the rest.
e.g. it could look something like this (with values for your install):
```
menuentry "Ubuntu" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set xxxxxxxx
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro  quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
```

If you want more help boot from a live CD and then download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"), and paste back the results here.

There are a lot of opinions about Wubi out there. Some valid, some not. This is what the creator thought about it: [http://agolb.blogspot.com/2007/06/why-wubi-is-important-for-linux.html](http://agolb.blogspot.com/2007/06/why-wubi-is-important-for-linux.html)
In my view, it is quite ingenious (if you tried installing linux not even 10 years ago you'd know how difficult it was then), but there is a huge disconnect between Canonical's support for it front-and-centre on their home page, and their development support for it. They should either get their developers to take it seriously or relegate it to a unsupported fringe. 

Anyway - if you've monitored these forums since the 10.04 release you'd see that grub2 has destroyed many normal dual boot installs too. It overwrote windows boot sectors and it took a month and a half for the developer (Colin Watson) to even respond to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724"). So... I don't think it's all about Wubi :)
Here's what Colin said in late June about the problem that started in April with 10.04's release:
> The reason why I haven't dealt with it until now is essentially that I've been buried trying to get grub2 into a decent state for Maverick, but I'm finally getting around to looking at the upgrade issues.

And that in a nutshell is the problem. Developers are so focused on the next release that they don't maintain the real one - which is a bizarre approach for a mainstream OS - the one that is actually being used is left broken while they work on the next one! And then the bugs in the next one will be ignored while they work on the following release.

---

### Post by mathgirl on 2010-12-01
I'm going to try this again this evening when I get home from work.  Thank you for all the help!

<political wubi discussion>
Regarding Wubi and grub, it seems like if Wubi is officially supported at all, synaptic or upgrade manager or whatever should just hold back grub updates until somebody's confirmed that they work.  Wubi is like a separate distribution (like Xubuntu, Kubuntu, Edubuntu, etc.) whose *only* distinguishing feature is the bootstrap method.  When that breaks, the entire 'distro' is ruined.

At the very least Wubi is meant to unterrify Windows addicts from the horrors they probably saw their older brother's dealing with in the 90's: completely wiped disks just from upgrades.  This exact kind of mysterious problem is what may reterrify them!
</political wubi discussion>

---

### Post by mathgirl on 2010-12-02
Thank you from the bottom of my heart!  Everything's working again!

I just misread

[blockquote]Delete all lines up to (not including) the first line that starts with "menuentry"[/blockquote]

as saying deleter everything from line 1 to the line with "menuentry".  When I turned my brain on and realized you meant everything from the *last* line back to the first menuentry block, everything worked fine.

Thanks again!

---

### Post by aiiee on 2010-12-02
BCBC hit the problem precisely and with devastating effect :D

It's not Wubi, it's NOT TESTING Wubi when upgrading.  Grub2 has always been a bad decision IMHO, and now you see why.  Why they let it in when it was obviously buggy is beyond me, and if it ever is exposed will make a great study in how bad decisions are made in modern corporations.  

Thanks again for being on top of this folks, it's people like you that make Ubuntu a viable alternative.  Upgrades that prevent you from using your computer?  Not so much.:guitar:

---

### Post by bcbc on 2010-12-02
> **mathgirl said:**
> Thank you from the bottom of my heart!  Everything's working again!

I just misread

[blockquote]Delete all lines up to (not including) the first line that starts with "menuentry"[/blockquote]

as saying deleter everything from line 1 to the line with "menuentry".  When I turned my brain on and realized you meant everything from the *last* line back to the first menuentry block, everything worked fine.

Thanks again!
OK Great!

So that fix is a temporary workaround. grub.cfg gets regenerated automatically e.g. if you install/remove a kernel.

Here's a summary of the issue and fix from Drs305 ([http://ubuntuforums.org/showpost.php?p=10183394&postcount=87](http://ubuntuforums.org/showpost.php?p=10183394&postcount=87)) and here is a thread I put together with instructions that seem to get things back to normal ([http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78))

---

### Post by bcbc on 2010-12-02
> **aiiee said:**
> BCBC hit the problem precisely and with devastating effect :D

It's not Wubi, it's NOT TESTING Wubi when upgrading.  Grub2 has always been a bad decision IMHO, and now you see why.  Why they let it in when it was obviously buggy is beyond me, and if it ever is exposed will make a great study in how bad decisions are made in modern corporations.  

Thanks again for being on top of this folks, it's people like you that make Ubuntu a viable alternative.  Upgrades that prevent you from using your computer?  Not so much.:guitar:

I did some more digging. The person that verified the fix only did so because he had another grub bug fix pending, and was told that the wubi fix had to go in first. He even had to ask whether the testing required Windows! Then he stumbled to a single successful test case - which I doubt, since it seems to fail 100% whenever I try it.

Anyway - what is strange is that there is no formal system development life cycle model employed - no independent QA signoff. Just some random developer with no experience running a quick test, to unblock an unrelated fix. Then it's checked off as 'verification done' and released to the general public.

This is really out of control. I think what irks me the most is that they don't even respond when you point out that there's a problem. They just bury their heads in the sand and keep on as though it's all good. It's not.

---

### Post by bcbc on 2010-12-02
Here are the details from my 'digging around'. Just so you know I am not making this stuff up!!! :P

16 November - Comment from bug [671097]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/671097/comments/8") (bug 671097 is one that smoser was working on - some issue with grub when running ubuntu in the cloud)
> Just mentioning here, that cjwatson said this upload will wait for bug 581760 getting tested and moved to -updates.

16November #ubuntu-devel on IRC
> [20:49] <smoser> cjwatson, is bug 581760 testable without a windows installation ?
[21:52] <cjwatson> smoser: no

19November #ubuntu-devel on IRC
> [22:25] <smoser> cjwatson, i tried to verify the fix for bug 581760 but apparently missed something. see my comments there.

19 November Comment from bug [581760]("https://bugs.launchpad.net/wubi/+bug/581760/comments/5")
> I tried above again, this time disconnecting the network cord.
- Installed from the same media mentioned.
- rebooted, hitting escape at the grub loader after windows loader and verified it was 1.98-1ubuntu5
- let the install run to completion
- reboot, verify still at 1.98-1ubuntu5
- did not add -proposed, 'apt-get install grub-pc' and saw confusing prompt (installing 1ubuntu7)

Then, I uninstalled wubi and repeated above except for this time *did* add -proposed.
I did *not* see the confusing prompt going from 1.98-1ubuntu5 to 1.98-1ubuntu8, verified that on reboot 1.98-1ubuntu8 was installed, and that reboot succeeded.


20November #ubuntu-devel on IRC
> [01:26] <smoser> cjwatson, so, if you see this, i've now (i think) sufficiently verified bug 581760
[01:28] <smoser> now we can get on to important bugs like bug 671097


20 November Comment from bug 581760
> Sounds good to me. Thanks!
[Fix released on 20 November]

---

### Post by mathgirl on 2011-02-24
One day when I made sure I had lots of spare time, I tried to carefully follow the 'megathread' about this problem and stop grub from updating.  Then I let synaptic loose and recreated the problem -- I came back to this thread to carefully put ubuntu back together again.

How will I know when I can let my updates happen again from synaptic without my having to hack around?  I think I'm waiting for grub to be fixed upstream?

P.S.  Thanks so much for this thread and the megathread.  Wubi is definitely only for super-hackers.

---

### Post by bcbc on 2011-02-24
The developers are working furiously on 11.04 Natty Narwhal, the next release of Ubuntu. And grub2 is up to revision 3092 (that's over 200 revisions since October when maverick was released). But it appears no one is working on the current release bugs. I even emailed a "real fix" to one of the grub devs to try and get things kick-started, but no luck. 

Even if they do fix these bugs, it's likely that they'll first be fixed in Natty - and only after they'll be put into Lucid.

So, in basically, the only workaround is the Permanent Fix (in the wubi megathread) and permanently locking grub-pc and grub-common. For those that install fresh - hopefully they'll browse the Wubi Guide and see the [Warning]("https://wiki.ubuntu.com/WubiGuide#Warning") and lock grub-* right from the get go.

I don't agree that Wubi is for super hackers. I think there's simply a flaw in Canonical's development model. It appears to give the developers too much decision-making power for prioritizing bugs. This is the 'open-source' model, which makes sense for things like the kernel etc. or independent apps where they have no control. But they should control their 'employed' devs a bit better, and then maybe these simple but serious bugs would get dealt with quicker.

---

### Post by Hippytaff on 2011-02-24
> **bcbc said:**
> The developers are working furiously on 11.04 Natty Narwhal, the next release of Ubuntu. And grub2 is up to revision 3092 (that's over 200 revisions since October when maverick was released). But it appears no one is working on the current release bugs. I even emailed a "real fix" to one of the grub devs to try and get things kick-started, but no luck. 

Even if they do fix these bugs, it's likely that they'll first be fixed in Natty - and only after they'll be put into Lucid.

So, in basically, the only workaround is the Permanent Fix (in the wubi megathread) and permanently locking grub-pc and grub-common. For those that install fresh - hopefully they'll browse the Wubi Guide and see the [Warning]("https://wiki.ubuntu.com/WubiGuide#Warning") and lock grub-* right from the get go.

I don't agree that Wubi is for super hackers. I think there's simply a flaw in Canonical's development model. It appears to give the developers too much decision-making power for prioritizing bugs. This is the 'open-source' model, which makes sense for things like the kernel etc. or independent apps where they have no control. But they should control their 'employed' devs a bit better, and then maybe these simple but serious bugs would get dealt with quicker.

Maybe a wubi sticky is in order for the Absolute beginner talk part of the forum to highlight the DANGERS and point them to the WUBI MEGATHRERAD!?

---

### Post by bcbc on 2011-02-24
> **Hippytaff said:**
> Maybe a wubi sticky is in order for the Absolute beginner talk part of the forum to highlight the DANGERS and point them to the WUBI MEGATHRERAD!?
We added the [Warning]("https://wiki.ubuntu.com/WubiGuide#Warning") to the Wubi Guide as it's more likely Wubi users would see that - they probably only come to ubuntuforums.org *after* they have problems. Also now that ubuntu.com is offering 10.10 wubi.exe by default, we shouldn't see as many problems.

The only issue with adding a sticky to the beginner forum is they have a few there already - but the mods can offer a more informed opinion on that.

---

