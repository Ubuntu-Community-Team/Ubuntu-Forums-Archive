---
title: "Please help?  Latest update killed my Ubuntu!"
date: 2009-11-23
forum: General Help
---

### Post by whitefort on 2009-11-23
Plea from panic-stricken Karmic user.

I've had Karmic on my Acer Aspire, and it's been working just fine.  Then about an hour ago I applied the latest updates.  When I restarted as requested,
I got the little ubuntu circle (as usual), then a lot of text flashing on and off (literally) too fast for me to be able to read it.

Then it stops at what seems to be a text login prompt, but with the screen flashing on and off about twice per second.

I've trying typing, but the keyboard doesn't seem to be responsive either.

I really need (I mean REALLY NEED) this computer to be working by tomorrow (so I was perhaps a bit stupid to apply the update, but I thought the days when updates broke the system were a thing of the past).

Anyway, has anyone any ideas what I can do?

My current 'worst scenario' plan is to use a live cd to try to retrieve my data, then do a 'from scratch' re-install.  But if anyone can suggest anything else, I'd be VERY grateful.

I'm not sure what other info to give, as I'm unable to read fast enough to say what's happening with the first messages that appear on the screen.  I've also tried to ssh into the machine to see if I can do anything that way, but it's not working either.

Anyway, please, please, HELP???

---

### Post by mirchichamu on 2009-11-23
I suffered the same on my Toshiba laptop. I am waiting for any suggestion.
I am cursing myself why I did update.

---

### Post by camaron1 on 2009-11-23
> **whitefort said:**
> Plea from panic-stricken Karmic user.

I've had Karmic on my Acer Aspire, and it's been working just fine.  Then about an hour ago I applied the latest updates.  When I restarted as requested,
I got the little ubuntu circle (as usual), then a lot of text flashing on and off (literally) too fast for me to be able to read it.

Then it stops at what seems to be a text login prompt, but with the screen flashing on and off about twice per second.

I've trying typing, but the keyboard doesn't seem to be responsive either.

I really need (I mean REALLY NEED) this computer to be working by tomorrow (so I was perhaps a bit stupid to apply the update, but I thought the days when updates broke the system were a thing of the past).

Anyway, has anyone any ideas what I can do?

My current 'worst scenario' plan is to use a live cd to try to retrieve my data, then do a 'from scratch' re-install.  But if anyone can suggest anything else, I'd be VERY grateful.

I'm not sure what other info to give, as I'm unable to read fast enough to say what's happening with the first messages that appear on the screen.  I've also tried to ssh into the machine to see if I can do anything that way, but it's not working either.

Anyway, please, please, HELP???

For what you say you go past Grub, so you should be able to reboot and when in the Grub screen choose 
a-**recovery mode** option
b-the previous kernel, as you should've updated kernel some time ago.

Hope it's of any help

---

### Post by whitefort on 2009-11-23
> **camaron1 said:**
> For what you say you go past Grub, so you should be able to reboot and when in the Grub screen choose 
a-**recovery mode** option
b-the previous kernel, as you should've updated kernel some time ago.


Thanks, but how do I get into grub?

The single word 'GRUB' appears for a second, then the ubuntu logo appears immediately after, and then everything goes crazy.

I'm hoping this isn't going to cost me all my data - I've tried to get in using a live CD, and because Ubuntu kindly encrypted my home directory (which seemed like a good thing at the time) I can't get in.  I've tried following the instructions, but I just get the message:  ERROR:  Encrypted private directory is not setup properly...

Thanks a lot, Ubuntu...

Sheesh...  I really thought they'd said the days when updates would wreck the system were a thing of the past.  I'm trying hard not to be really angry about this, but so long as I get my data back by tomorrow I suppose I'll get over it.

But for now, I just still need help.

---

### Post by camaron1 on 2009-11-23
> **whitefort said:**
> Thanks, but how do I get into grub?

The single word 'GRUB' appears for a second, then the ubuntu logo appears immediately after, and then everything goes crazy.

I'm hoping this isn't going to cost me all my data - I've tried to get in using a live CD, and because Ubuntu kindly encrypted my home directory (which seemed like a good thing at the time) I can't get in.  I've tried following the instructions, but I just get the message:  ERROR:  Encrypted private directory is not setup properly...

Thanks a lot, Ubuntu...

Sheesh...  I really thought they'd said the days when updates would wreck the system were a thing of the past.  I'm trying hard not to be really angry about this, but so long as I get my data back by tomorrow I suppose I'll get over it.

But for now, I just still need help.
Uff, the encryption of your data is not good news...

Grub is the initial menu where you choose where where to boot into. You say that it disappears quickly. Try this: Reboot. The recovery option is the second option so have your finger in the down arrow ready to press it as soon as you see the grub screen. You have to be quick. 

As for your encrypted data I don't really know it you can recover that from the live cd. Someone else will have to tell you 

[SIZE=5]PD:[/SIZE] [SIZE=5]that an update in ubuntu can cause such a mayhem is serious cause of concern[/SIZE], that goes to whoever needs to listen

---

### Post by confused_user on 2009-11-23
I had this exact same issue on my hpdx2250.  I tried everything i knew and some stuff i didnt.

In the end i rebuilt it :(

This was also the straw that broke the camels back.  I downgraded all but one of my systems back to 9.04 since i could get no support on it.

Sorry dude, hope you have your /home on a seperate partition?

edit: i suppose i should try and help :)

Re getting your databack - if you boot up off the live CD and then mount your /home drive you may be able to get in, perhaps the live cd knows how to decrypt your filesystem, i guess that would make it a crappy encryption schema but hey, worth a shot.

If that does not work then look at booting into recovery mode - can be done from grub - where you get a root login.  from there you should be able to get in.

Failing that we're going to have to find out where the encryption keys are stored and try and grab them for use in another session.

Alternatively, depending on how much your data is worth to you , you can pay to have someone fix this for you, support section - [http://www.ubuntu.com/support/services](http://www.ubuntu.com/support/services)

Cant see them being able to help very quickly though, not if they cant get remote access

---

### Post by fluffman86 on 2009-11-23
First: to get into grub, hold shift.  That might let you boot into recovery mode or into a previous kernel.  The flashing TTY is due to a corrupt video driver.  Do some googling on your model and how to get it working again after something screws up like that.

Second: if that doesn't work, then I'm sure you backed up your private key hash file like you were told to do after you encrypted your drive, right?  RIGHT?

I'm out of time now, but check out [http://blog.dustinkirkland.com/2009/02/jaunty-encrypted-home-directories.html](http://blog.dustinkirkland.com/2009/02/jaunty-encrypted-home-directories.html) and some of the related links for how to un-encrypt your directory from a live CD.  You may need to do some more searches on that blog for more info.

I'm subscribing to this thread and will check back with you tonight and do some more searching on how to get your data back later.

edit: found the link
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)

---

### Post by whitefort on 2009-11-23
OK... Well, this is new.  I'd discovered in the past that updates could break the X window system. I think that was back in the days of Edgy and Feisty?

But now it seems that Karmic can go one better, and lose me all the data on my machine?

Let's be clear - I, the user - have not done anything wrong here.

I installed Karmic.  I went with the defaults all the way, and when it asked me if I wanted an encrypted home directory, I thought yeah, on a laptop that's got to be a good thing.

Fast forward to an hour ago.  The regular updates.

And now, not only do I have a broken system, but it looks like I can wave goodbye to all my data?
(No, I don't have it on a separate partition, because I went with the Ubuntu default.  No I don't have it all backed up, and I admit that bit will be my own stupid fault - but who expects Canonical to kill their computer?)

And I don't have any grub menu - just the  words 'GRUB loading'' for a second or so.

I'm going to hang on for a few more hours, in the hope that someone can provide some help.  After that, I'm going to say goodbye to my data.

One more plea - just on the off-chance that I CAN get into my home directory in console mode, I'd be grateful if someone could tell me what shell commands I'll need to copy the entire directory (recursively and with all the hidden files and folders) across to a USB hard drive?

Seriously... I haven't hated Ubuntu so much since the days of Edgey and Feisty...

---

### Post by camaron1 on 2009-11-23
Your complaints are all fair.
I can't help any more.
Hope someone else helps you
good luck

---

### Post by A_T on 2009-11-23
Today's update killed my Kubuntu. :(

---

### Post by 73ckn797 on 2009-11-23
See if this thread will help: [http://ubuntuforums.org/showthread.php?t=1335346](http://ubuntuforums.org/showthread.php?t=1335346)

---

### Post by ubuntu27 on 2009-11-23
Oh no. I just installed the updates and now that I read this thread, I am afraid to restart the system.

---

### Post by whitefort on 2009-11-23
Fluffman86 - THANK YOU SO MUCH!!!!!

Holding down shift, I got the Grub menu.  I ignored the new '15' kernel and just ran '14', and everything booted up just as usual.

I'm still a total nervous wreck, but you have NO idea how much grief you've saved me (not to even mention the fact that I nearly had to tell a roomful of people that 'Ubuntu ate my data'.)

As I type, I'm backing up my entire home directory on to a usb drive, and I'll be much more serious about backups with this machine in future.  (as is always the way, this is the ONE machine I don't backup on a near-daily basis - though tonight's experience has fixed THAT forever!)

I guess my next project will be to find a way that I can just boot straight into the previous kernel instead of having to Shift+select each time.

And I've made a memo to self - never EVER run an update within a week of seriously needing the computer to work.

I'm all calmed down now, but I have to admit that an experience like this makes me question whether Ubuntu really IS ready for the general public.  If I'd only had one computer, and not been able to access help from you guys, this would really have left me totally screwed.

Anyway, thanks again.  Once more, I'm convinced that this forum is THE single best feature about Ubuntu.

---

### Post by confused_user on 2009-11-23
OK when you get it (note that i said "when" :) )

you can use all sorts of ways to copy it onto your usb drive

I would use rsync since if it cocks up for some reason you can start again and pick up from where you left off to save time.

```
rsync -avr --progress --stats /home /path to usb device
```

to find yoru usb device first check the output of df to see if it was mounted

```
df -ahT
```

It will look different from the rest and will probably have a FAT filesystem and / or a name like the manufacturer of the USB stick

if you dont see it in there check fdisk

```
sudo fdisk -l
``` 

Mine looks like this - you can see that mu USB stick is located on /dev/sdb1

```

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000021

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37423386   83  Linux
/dev/sda2            4660        4864     1646662+   5  Extended
/dev/sda5            4660        4864     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 4060 MB, 4060086272 bytes
125 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0x000e8997

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     3964094    c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(1023, 124, 62) logical=(1022, 124, 62)

```

alternative way of copying files (but inferior to rsync) 

```
cp -r /home /pathtousb
```

---

### Post by t0p on 2009-11-23
> **whitefort said:**
> 

One more plea - just on the off-chance that I CAN get into my home directory in console mode, I'd be grateful if someone could tell me what shell commands I'll need to copy the entire directory (recursively and with all the hidden files and folders) across to a USB hard drive?


The command you want is **'cp -r'**.  That's 'cp' (to copy) with the '-r' flag (to copy recursively).

I know you don't want to hear this: bu your experience is a lesson to all of us on the importance of backing up your files.  You never know when something might go wrong - whether that something is a messed-up update or a thief or... well, anything really.

I mean sure, the update shouldn't have done this - I hope all of you who've suffered this craziness take it up with the devs - but s**t happens.  Wear a hat.  Y'know?

Sorry.

---

### Post by ikacer on 2009-11-23
to get to the grub menu I think you need to press ESC within 3 seconds of the computer starting. From there you can either try another kernel, or if that doesn't work you can use recovery mode.

From here there are 2 different routes:

1) If you have to use recovery mode, you can type "startx" which will start a graphical interface. you will be the root user now. from there you can use your private key (which you should have backed up somewhere), to unincrypt your /home/USERNAME directory and copy over the important files you need.

if 1 doesn't work then

2) you can do all the steps from the command line. I don't know how familiar you are with the terminal, so I'll write a few notes: your external hardrive will probably be "/media/DRIVENAME". the "gpg" command can be used to decrypt your files, and "cp" command can be used to copy. To get instructions on how these commands work use "man COMMAND", eg "man gpg".

If everything above fails,you can boot from a live cd and use your private key to unincryt the drive and copy the files over.

EDIT: ok I posted a bit slow, I guess you already got it. :)

---

### Post by confused_user on 2009-11-23
> **t0p said:**
> The command you want is **'cp -r'**.  That's 'cp' (to copy) with the '-r' flag (to copy recursively).

I know you don't want to hear this: bu your experience is a lesson to all of us on the importance of backing up your files.  You never know when something might go wrong - whether that something is a messed-up update or a thief or... well, anything really.

I mean sure, the update shouldn't have done this - I hope all of you who've suffered this craziness take it up with the devs - but s**t happens.  Wear a hat.  Y'know?

Sorry.

the other lesson is that you must not trust updates from ubuntu (or likely any other distro except perhaps Debian)

They simply do not test these updates on every conceivable system configuration.  I guess this is all part of using an open source operating system.

It does make me step back from soap boxing Ubuntu at work though, we use SUSE on our servers (lots and lot of severs).  I'm always saying how crap SUSE is compared to Ubuntu but after the 9.10 debacle i dont think i would trust Ubuntu in a production environment.  It seems to be getting worse too.

A few versions ago it was solid as a rock, now look at it.

---

### Post by ubuntu27 on 2009-11-23
> **ubuntu27 said:**
> Oh no. I just installed the updates and now that I read this thread, I am afraid to restart the system.

I just restarted Ubuntu and I saw that Grub showed the new Linux Knernel, and I booted from it.

The whole screen was dark and a white " __ " could be seen at the top left corner flashing. 

After a little while I was in the Login Screen (GDM), I typed my password, and I logged in successfully.

I don't see any problems so far.



So, it seems that not everyone has the problems that we are reading in todays threads.

---

### Post by whitefort on 2009-11-23
> **confused_user said:**
> A few versions ago it was solid as a rock, now look at it.

I know what you mean - there was a time in the past when I actually STOPPED doing any Ubuntu updates, because I got tired of how often an update left me with just a console login - and I only had one computer back then, so it was an utter nightmare.

I really thought those days were gone, and in fact I'm pretty sure I read a Canonical proclamation that the situation  where updates broke graphics was well-and-truly fixed.

Among family, friends, and colleagues, I'm annoyingly evangelistic about Ubuntu.  Tomorrow could have been *seriously* embarrassing, and I still might have to take some flak if this killer update affects any of my 'converts'...  At least now I know how to help them!

I'll still use Ubuntu, I still love Ubuntu (well, I will, once we get over this lovers' tiff), but I don't think I'll be so preachy about it for the foreseeable future.

---

### Post by ratcheer on 2009-11-23
The update is not killing anything. It is just that your video driver is not compiled into the new kernel. To fix it, boot into recovery mode (as discussed in several posts, above). Then, log in. Then, install your video driver. Finally, reboot. Your system should then come up, normally.

Tim

---

### Post by whitefort on 2009-11-23
> **ubuntu27 said:**
> So, it seems that not everyone has the problems that we are reading in todays threads.

To be fair, that's true - and now that I know how to fix it, I've run it on three other computers.  Two (desktops) were fine, and the other (another laptop) wasn't.  I wonder if it's something that mostly hits laptops.

Seriously, I'm starting to wonder if you should only really trust Ubuntu if you have a second computer, so you can seek help if this sort of thing happens.

But again, to be fair, it's rare.  I forget the dates of Eft and Fawn, but I don't think I've had any serious update woes since then.

(shiver... I suddenly realise that it's so long ago, and I should probably be ashamed that I don't know a LOT more about Linux than I actually do - I've been using it since Dapper Drake.)

---

### Post by camaron1 on 2009-11-23
So what is the actual upgrade that has caused so much grief? the kernel 2.6.31.15? If it is that I got that updated "ages" ago and I don't thinks it caused so much panic about two weeks ago.

---

### Post by whitefort on 2009-11-23
> **camaron1 said:**
> So what is the actual upgrade that has caused so much grief? the kernel 2.6.31.15? If it is that I got that updated "ages" ago and I don't thinks it caused so much panic about two weeks ago.


Um... Congratulations?

(Edited just to say - please see my apology for this stupid remark just a few messages later!  It's been a stressful night...)

---

### Post by camaron1 on 2009-11-23
>  Um... Congratulations? 	

Not sure you got my point: **IF** it is the same upgrade we are talking about, why is it responding in a different way now?

Anyway, I'm glad you got it fixed

---

### Post by t0p on 2009-11-23
> **confused_user said:**
> A few versions ago it was solid as a rock, now look at it.

Ubuntu is *still* "solid as a rock".  By which I mean: it's no less solid than it was a couple of months ago.

Whenever a new version comes out, *some* people with *some* hardware configurations experience problems.  And that's to be expected: *no* operating system works perfectly with every computer in the world.

And sometimes - and I mean *sometimes* - updates break something.  That's to be expected too: see above.

Maybe more users than normal have experienced teething problems with 9.10.  It's certainly irritating to the users in question.  Even distressing to users who really rely on their computers for work and stuff.  But it is not a reason to suddenly cease trusting Ubuntu.  Ubuntu *hasn't* suddenly gone down the tubes.  In a couple of months, no one's going to even remember this.  Everything will be hunky-dory. Honest.

When 10.04 is released, some people's computers will have a dump.  And users will be crying: *OMG Ubuntu was solid as a rock until Lucid!  Why can't it be nice and stable like Karmic?!!*

Wait and see.

---

### Post by whitefort on 2009-11-23
> **camaron1 said:**
> Not sure you got my point: **IF** it is the same upgrade we are talking about, why is it responding in a different way now?

Anyway, I'm glad you got it fixed

Apologies.  I think I did take your message the wrong way, and clearly I'm still not as 'calmed down' yet as I thought!  Sorry!

Anyway, I'm fixed (or at least my computer is), the data is all backing up, and I can breathe again.

I've marked the thread as 'solved', and I'm going to bed now - if I post anymore tonight I'll probably only badmouth Ubuntu in ways that I'll regret in the morning!

BUT SERIOUSLY - THANKS AGAIN EVERYONE.

---

### Post by camaron1 on 2009-11-23
> **whitefort said:**
> Apologies.  I think I did take your message the wrong way, and clearly I'm still not as 'calmed down' yet as I thought!  Sorry!

Anyway, I'm fixed (or at least my computer is), the data is all backing up, and I can breathe again.

I've marked the thread as 'solved', and I'm going to bed now - if I post anymore tonight I'll probably only badmouth Ubuntu in ways that I'll regret in the morning!

BUT SERIOUSLY - THANKS AGAIN EVERYONE.

No worries mate, good sleep, I'm going to bed too ;)

---

### Post by keypox on 2009-11-23
> **whitefort said:**
> Fluffman86 - THANK YOU SO MUCH!!!!!

Holding down shift, I got the Grub menu.  I ignored the new '15' kernel and just ran '14', and everything booted up just as usual.

I'm still a total nervous wreck, but you have NO idea how much grief you've saved me (not to even mention the fact that I nearly had to tell a roomful of people that 'Ubuntu ate my data'.)

As I type, I'm backing up my entire home directory on to a usb drive, and I'll be much more serious about backups with this machine in future.  (as is always the way, this is the ONE machine I don't backup on a near-daily basis - though tonight's experience has fixed THAT forever!)

I guess my next project will be to find a way that I can just boot straight into the previous kernel instead of having to Shift+select each time.

And I've made a memo to self - never EVER run an update within a week of seriously needing the computer to work.

I'm all calmed down now, but I have to admit that an experience like this makes me question whether Ubuntu really IS ready for the general public.  If I'd only had one computer, and not been able to access help from you guys, this would really have left me totally screwed.

Anyway, thanks again.  Once more, I'm convinced that this forum is THE single best feature about Ubuntu.

You should have backups of important data. But your OS should not be the problem for losing your data. That said maybe you should use a more reliable OS for crucial data... you know what im talking about.

---

### Post by ubuntu27 on 2009-11-23
> **whitefort said:**
> To be fair, that's true - and now that I know how to fix it, I've run it on three other computers.  Two (desktops) were fine, and the other (another laptop) wasn't.  [U]I wonder if it's something that mostly hits laptops.
[/U]


From what I read, most if not all the people who got affected were using laptops.

The one I upgraded was a "HP Pavilion Entertainment PC" (_Laptop_).

I must have been "lucky".

---

### Post by confused_user on 2009-11-23
> **t0p said:**
> Ubuntu is *still* "solid as a rock".  By which I mean: it's no less solid than it was a couple of months ago.

Whenever a new version comes out, *some* people with *some* hardware configurations experience problems.  And that's to be expected: *no* operating system works perfectly with every computer in the world.

And sometimes - and I mean *sometimes* - updates break something.  That's to be expected too: see above.

Maybe more users than normal have experienced teething problems with 9.10.  It's certainly irritating to the users in question.  Even distressing to users who really rely on their computers for work and stuff.  But it is not a reason to suddenly cease trusting Ubuntu.  Ubuntu *hasn't* suddenly gone down the tubes.  In a couple of months, no one's going to even remember this.  Everything will be hunky-dory. Honest.

When 10.04 is released, some people's computers will have a dump.  And users will be crying: *OMG Ubuntu was solid as a rock until Lucid!  Why can't it be nice and stable like Karmic?!!*

Wait and see.

I've been waiting and seeing for a very long time now.  I'm not saying i will stop supporting Ubuntu.

I read in another thread.  There is a cycle with Ubuntu and it goes something like this

works/doesnt/works/doesnt/works/doesnt

I'm also not referring directly to this bug, there are many more, this forum is full of them.  If it was just this then i would agree with all of your comments, but it's not, and i dont.

If a system works fine and is then killed by updates, something is wrong.  No if's and but's, no "oh your just being a dick", something is wrong.

if the aim of ubuntu is to 

  >  1.  Every computer user should have the freedom to download, run, copy, distribute, study, share, change and improve their software for any purpose, without paying licensing fees.
   2. Every computer user should be able to use their software in the language of their choice.
   3. Every computer user should be given every opportunity to use software, even if they work under a disability.


 
then they are failing, 9 versions is long enough to get driver support right.  Note that they say "every computer user".

I despair when something that was working perfectly well does not anymore.  And when i read comments from Ubuntu developers on this site saying that they do not really read these forums nor do they consider this a reliable source of feedback i despair even more.

I, like everyone else just want to enjoy Ubuntu without having to cringe and worry as i hit the update button.

sorry for ranting but as you may have noticed, i have a chip on my shoulder about 9.10.  I'm just angry at them for breaking something i used to love.

ps - and whitefort's problem is not fixed at all, he's just booting the older kernel, the one that works.  the problem is still there

---

### Post by fluffman86 on 2009-11-23
You're welcome, whitefort.  Glad you got it working.  

To prevent this from happening on really important computers, you might want to disable all of your repositories or updates except those from "main".

For example: a few months ago, during Jaunty, I was running the most up-to-date testing kernels.  For quite a while, a certain kernel screwed with my sound.  But I kept getting updates for it as it filtered down to the main channel.  By then, it worked fine.

Go to System > Administration > Software Source, then the Updates tab, and uncheck everything except for the Important Security Updates (karmic-security).  That way, everything is well tested as safe, and only updates if it's for security reasons...in other words--VERY IMPORTANT. 

The other sources are for testing.  :)

---

### Post by xjbullx on 2009-12-06
> **fluffman86 said:**
> You're welcome, whitefort.  Glad you got it working.  

To prevent this from happening on really important computers, you might want to disable all of your repositories or updates except those from "main".

For example: a few months ago, during Jaunty, I was running the most up-to-date testing kernels.  For quite a while, a certain kernel screwed with my sound.  But I kept getting updates for it as it filtered down to the main channel.  By then, it worked fine.

Go to System > Administration > Software Source, then the Updates tab, and uncheck everything except for the Important Security Updates (karmic-security).  That way, everything is well tested as safe, and only updates if it's for security reasons...in other words--VERY IMPORTANT. 

The other sources are for testing.  :)

After searching on various permutations of what I think my problem is I stumbled across this thread. My diagnosis seems similar:

[LIST=1]
[*]Installed updates, one of which was the ...-15 kernel.
[*]Rebooted
[*]Get Kubuntu splash screen, then a blank screen forever
[*]Hit F10 during splash, noticed the only message before "crashing" was from fsck
[*]Spent a whole bunch of time trying to figure out if fsck is causing my computer to fail while booting : (
[/LIST]

So, learning that I can hold down shift to get a boot menu from grub is super helpful. However, booting into ...-14 or in safe mode does not seem to remedy the problem for me.

What does remedy the problem is powering off over and over again until the computer randomly decides to boot. Sometimes this happens after 5 or so shutdowns, sometimes 15.

One user recommended manually updating the video drivers. I looked in my hardware driver profiles and I am not using any proprietary drivers for my Dell Inspiron 1525. I have no idea how to change or remedy this, or whether it is even appropriate. For now my strategy is to leave my computer running and keep installing updates in hopes that something coming down the line will fix the issue.

A few notes:

[LIST=1]
[*]This forum is awesome, and if it wasn't for you folks I would not have been running Kubuntu for the past 18 months. I would have bought a Windows CD and said to hell with it. Thank you.
[*]If anyone has any ideas for how I can remedy the issue that I'm having, if the diagnosis is different than that of the OP, I would REALLY appreciate it
[*]Can anyone offer an "update philosophy" that will minimize the pain for noobs like me? I only use "main," but my inclination is to upgrade every single thing that comes along, including my distro version, which caused me to re-install from scratch when Karmic dropped. Spending several days backing up gigs of digital photos and important docs via wireless to my girlfriend's computer is almost enough to make a person throw in the towel. And no, I did not know that Karmic comes with ext4 and upgrading from ext3 would be an issue.
[/LIST]

Thanks, all!

---

