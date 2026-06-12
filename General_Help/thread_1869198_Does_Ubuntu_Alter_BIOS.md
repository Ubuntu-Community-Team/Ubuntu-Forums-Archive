---
title: "Does Ubuntu Alter BIOS?"
date: 2011-10-25
forum: General Help
---

### Post by rs321 on 2011-10-25
Re: 10.04.2

Folks,

I want to run a dual boot Windows/Ubuntu and felt the best approach in my case would be to have the HD formatted and start from scratch, so yesterday I took it to a shop where they did it for me.  When trying the re-installation later I got the following message:

error: unknown filesystem
grub recovery>

Just for practice I also tried to re-install Ubuntu at that point and it also failed.

It seems to me that unless Ubuntu alters the BIOS the error message means the shop did a sloppy job of formatting because Windows doesn't use grub but before I take the HD back for them to do it right I think it would be good to check here.  Any thoughts?

-Randy

---

### Post by satanselbow on 2011-10-25
The grub error message comes from the mbr on the hdd (master boot record) which is where the bios hands over to in the initial stages of firing up your (or any) computer.

If you took it in and asked them to format the disk - they have done exactly as asked. Formatting an HDD does not include "wiping" the mbr per se.

Ubuntu cannot and does not alter the bios settings.

To reinstall you may need to enter the bios yourself to change the order that bios looks for boot devices. Set it so CD and/or USB take precedence to the hdd. You can then - when you have installed all your OS - go back into the bios and change it back so the hdd comes 1st ;)

---

### Post by searchfgold6789 on 2011-10-25
Your BIOS (completely unaffected by Ubuntu) looks for a boot device.
Your boot device looks for an MBR.
Your MBR loads and looks for a boot loader.
Your boot loader looks for an OS.
You are getting this message because the GRUB MBR is there but the boot loader is not. (drs305 will probably correct me on this later if I am wrong.)
Your best bet is to run [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair").
Good luck,
 - search

---

### Post by Mark Phelps on 2011-10-25
So what was SUPPOSED to be the state of the drive when you got it back:
1) Formatted -- No OS
2) Formatted, but with Windows installed only
3) Formatted, but with Ubuntu installed only
4) Formatted, but with both Windows and Ubuntu installed.

All of these will present different problems.  Unless you provide more details of what SHOULD be there, it's going to be impossible to provide you detailed advice to make that happen.

---

### Post by rs321 on 2011-10-25
Folks,

Thanks for the suggestions but unfortunately none of them worked.  The cd drive will not work nor will the usb drive so the recommended fixes are to no avail.  When trying to configure it manually the system came to a halt with the word sudo, so that's out.

I'm not sure what to do at this point other than to say spending more money is pretty well out of the question.  I might add that more information than what I have already given seems to me to be unnecessary; a formatted HD is a formatted HD in my book and to have anything else on it is rather a silly assumption.  It's rather pointless to check around for more fixes than have already been offered but if anybody knows what Ubuntu wants me to type in at the grub rescue prompt I'm all ears.

Thanks again for the help you've all given so far.

-Randy

---

### Post by lisati on 2011-10-25
We feel your frustration. 

The reason that people sometimes ask for more information is that everyone's computer system is different. Asking for more information helps us get a clearer picture of what you were trying to do, what you were expecting, and what might have gone wrong.

---

### Post by oldtimer7777 on 2011-10-25
I hear your frustration..  

What kind of computer are you trying to install Ubuntu onto?

What are the specs?  

What else is installed on your computer? 

It is all helpful so we can figure out why it isn't working for you.

Maybe we can cross reference this problem that someone else has experienced before to find a good solution.

> **rs321 said:**
> Folks,

Thanks for the suggestions but unfortunately none of them worked.  The cd drive will not work nor will the usb drive so the recommended fixes are to no avail.  When trying to configure it manually the system came to a halt with the word sudo, so that's out.

I'm not sure what to do at this point other than to say spending more money is pretty well out of the question.  I might add that more information than what I have already given seems to me to be unnecessary; a formatted HD is a formatted HD in my book and to have anything else on it is rather a silly assumption.  It's rather pointless to check around for more fixes than have already been offered but if anybody knows what Ubuntu wants me to type in at the grub rescue prompt I'm all ears.

Thanks again for the help you've all given so far.

-Randy

---

### Post by mcduck on 2011-10-25
> **rs321 said:**
> Folks,

Thanks for the suggestions but unfortunately none of them worked.  The cd drive will not work nor will the usb drive so the recommended fixes are to no avail.  When trying to configure it manually the system came to a halt with the word sudo, so that's out.

I'm not sure what to do at this point other than to say spending more money is pretty well out of the question.  I might add that more information than what I have already given seems to me to be unnecessary; a formatted HD is a formatted HD in my book and to have anything else on it is rather a silly assumption.  It's rather pointless to check around for more fixes than have already been offered but if anybody knows what Ubuntu wants me to type in at the grub rescue prompt I'm all ears.

Thanks again for the help you've all given so far.

-Randy

The shop did exactly what you asked them to do, as you can't format a hard drive, you can only format a filesystem. And that's what they probably did. (low-lever formatting of hard drives hasn't been possible for ages, although you could zero out a drive to get rid of all data including the partition table if you wanted to).

Doesn't matter, though, as your problem isn't with the contents of the drive, or lack of them. It's simply a question of getting your computer to boot from a device you can use to install an operating system. And that's something that should happen before the computer system should even access the hard drive, so it make absolutely no difference if the drive is formatted or not, has any partitions or not, or has any data in the MBR or not.

Now, if you can't boot from a CD or DVD, may I ask what were you planning on doing with the system if it doesn't have a working CD drive or USB connector? Or do you mean that the drive's work, but you can't get the machine to boot from them? That would leave only two things to consider, making sure the boot order is set correctly in BIOS, and making sure you have a suitable installation media to boot from (error-free disc image burned to CD as an image, or bootable USB drive created using uNetBootin, Ubuntu's Startup Disc Creator or any similar tool. Or the original Windows disc if that's what you were planning to install).

---

### Post by Slim Odds on 2011-10-25
> **mcduck said:**
> <cut>
Doesn't matter, though, as your problem isn't with the contents of the drive, or lack of them. It's simply a question of getting your computer to boot from a device you can use to install an operating system. And that's something that should happen before the computer system should even access the hard drive, so it make absolutely no difference if the drive is formatted or not, has any partitions or not, or has any data in the MBR or not.
<cut>
In addition, it doesn't even matter whether the hard drive is connected or not.

mcduck is correct, you need to be able to boot from something other than your hard drive. Then you can go from there.

---

### Post by searchfgold6789 on 2011-10-25
You need to get a Live CD or something, but This might help clarify the situation a bit more:
[https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting](https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting)
I'll keep an eye on this thread, cuz I hope things turn out well for you!
 - search

---

### Post by kurt18947 on 2011-10-25
> **satanselbow said:**
> The grub error message comes from the mbr on the hdd (master boot record) which is where the bios hands over to in the initial stages of firing up your (or any) computer.

If you took it in and asked them to format the disk - they have done exactly as asked. Formatting an HDD does not include "wiping" the mbr per se.

Ubuntu cannot and does not alter the bios settings.

**To reinstall you may need to enter the bios yourself to change the order that bios looks for boot devices. Set it so CD and/or USB take precedence to the hdd. You can then - when you have installed all your OS - go back into the bios and change it back so the hdd comes 1st** ;)

This sure seems like a good first step.  If there is an failed boot process on the first device, it won't look for any better boot devices further down the chain. I've left my machines' BIOS set for

[LIST=1]
[*]USB HDD
[*]CD
[*]Hard Drive.
[/LIST]
That doesn't add 5 seconds to the boot time and gives me the option to boot a Live device prior to the hard drive.  Making the hard drive the first boot device would be required if you didn't want others to be able to install portable bootable devices on the machine.

---

### Post by dcstar on 2011-10-26
> **rs321 said:**
> Folks,

Thanks for the suggestions but unfortunately none of them worked.  **The cd drive will not work nor will the usb drive** so the recommended fixes are to no avail.
........

Yeah, then how did you do the "re-installation" you said you did in your original post?

Someone obviously does not understand either what they are trying to achieve or what they are doing in the process.

---

### Post by satanselbow on 2011-10-26
Hey rs321,

In my experience your average computer shop bod will have "join the dots" (ie follow step by step instructions) on how to fix windows, would like to have more mac experience but doesn't see enough broke ones to actually get anymore practice and - if they have heard of linux at all - have zero linux experience.

A "problem" like yours, keeping in mind that there are no problems - only opportunities to learn, does rather require knowing a little more about the machine you are working on, exactly what you are trying to achieve (you stated w7 + Ubu dualboot) and what the state of play is at the moment.

It does rather sound like the shop you sent the drive to did half a job - or at least followed instructions (ie format this) that they did not look at the drive more closely and find multiple partitions. If I had been given this drive I would have come back to you and asked exactly what you want doing with the additional partitions. I guess that they didn't look and didn't ask.

Could you maybe let us know exactly where we are at currently?


1) Can you / do you know how to enter the bios
2) If you have entered bios what "boot options" or "boot order" selections do you see?
3) Do you have an original W7 DVD and/or Ubuntu LiveCD 
4) What is the exact message you are seeing when you boot the machine at the moment (remove all CD/DVD and USB bootable media)

Let us know where we are at and we will be able to get you up and running - and probably get you enough ammo to go reclaim your money back from the shop :D

---

### Post by westie457 on 2011-10-26
Hi, taking into consideration that you want to set up a dual-boot system and you still have Grub in the MBR it looks like the 'shop' only formatted the partition/s as already suggested. They did not completely wipe the drive by creating a new partition table.

In a dual-boot system ideally Windows should be installed first as it rewrites the MBR, also Windows does write to the BIOS and changes the boot order to boot from the HDD that Windows is installed to.

Do you have your Windows install DVD to hand?
This is the only install media I am aware of that overrides the BIOS settings and gives you the chance to 'Press Any Key to Boot From CD/DVD.....' before allowing the HDD to be accessed.

If your original Windows is still on the HD the install disc will find it. If it is not there then you will have to install Windows, which you want to do anyway.

Once that is done and you want guidance on the next steps come back here and ask or search the Forum. There are many threads asking about dual-booting and partitioning.

Hope this helps and good luck.


ps Apologies to all if you think I have stated the obvious. Sometimes it needs to be done if only to provide a sanity check.

---

### Post by satanselbow on 2011-10-26
> **westie457 said:**
> also Windows does write to the BIOS and changes the boot order to boot from the HDD that Windows is installed to.


I'm sorry but that is misinformation. Windows does not and cannot change the bios. This would be considered virus behaviour. Whilst I would love to be able to state that windows is itself a virus - this simply is not true.

Windows NTLDR receives basic hardware info from the bios it does not and cannot write to or change the bios.

---

### Post by westie457 on 2011-10-26
> **satanselbow said:**
> I'm sorry but that is misinformation. Windows does not and cannot change the bios. This would be considered virus behaviour. Whilst I would love to be able to state that windows is itself a virus - this simply is not true.

Windows NTLDR receives basic hardware info from the bios it does not and cannot write to or change the bios.

On the first part of your post I do have to disagree with you. It may only happen on my pc however it does happen. The Bios has been set to boot from CD, Windows is installwd and at reboot the bios has been reset to boot from the 1st hard drive. This has happened, at least to me, every time Windows has been installed/reinstalled for the last 8 years or so.

This behaviour would and is considered virus activity only if that option has been enabled to alert to BIOS writing events.

---

### Post by mastablasta on 2011-10-26
i suppose windows tells you to remove windows install cd before first reboot after the install just for the fun, huh? :-D
 
i also never seen that behaviour though i have to admit a this point do not have windows 7 experience.

---

### Post by kurt18947 on 2011-10-26
> **westie457 said:**
> On the first part of your post I do have to disagree with you. It may only happen on my pc however it does happen. The Bios has been set to boot from CD, Windows is installwd and at reboot the bios has been reset to boot from the 1st hard drive. This has happened, at least to me, every time Windows has been installed/reinstalled for the last 8 years or so.

This behaviour would and is considered virus activity only if that option has been enabled to alert to BIOS writing events.

I don't doubt for a moment that what you say did indeed happen.  I suspect thought that it's from some "customization" done by the manufacturer.  I've installed retail Windows versions many times on different machines and have never seen that behavior.

---

### Post by westie457 on 2011-10-26
> **kurt18947 said:**
> I don't doubt for a moment that what you say did indeed happen.  I suspect thought that it's from some "customization" done by the manufacturer.  I've installed retail Windows versions many times on different machines and have never seen that behavior.

In this case it is a home built pc on its third mobo, each from a different manufacturer and standard Bios. Though cannot remember if the behaviour ever happened on my Acer laptop. No intention of reinstalling Windows on it ATM to prove a point. Shall we agree to differ on this. I will concede that it might have something do with Windows OEM installs though.

Enjoy your day. Everyday.

---

### Post by Mark Phelps on 2011-10-26
Have been installing Windows OSs for years on lots of different PCs and have never encountered the situation where, as a byproduct of Windows installation, the BIOS boot default is "switched" from CD to Hard Drive.  In fact, after the install is done and Windows goes to reboot for the first time, I still see the "press any key to boot from ..." at the top of the screen.  It then boots from the hard drive because I did NOT press any key, not because the boot order got changed.

Maybe this is a new custom settings in the newer BIOS's -- although the latest one I have is six months old and does not do this switching.

---

### Post by rs321 on 2011-10-29
Folks,

Thank you all for the wealth of information you have supplied.  I certainly owe everyone an apology for not responding more quickly but between a foot of wet snow falling on trees that still have their leaves, clearing broken trees from the roof and fence and yard, power outage, and personal sloth I haven't gotten back to you yet.  I shouldn't happen again.

My goal is to set-up a dual boot Windows XP (ugh!) and Ubuntu 10.04.2, both of which I have on CD.  I've done this in the past with no problems but this time Windows was not on the HD when it was formatted, which is why I thought Ubuntu might have changed the bios.  I have as boot options the HD or floppy drive because it says CD and USB are not available.  I also have boot repair on a USB stick if it would be recognized but is too large (350 megs) to fit on a floppy.  I could write the bios onto a floppy but I don't know what to write.  I suppose I could do an online search for it with a different computer and put it on a floppy from there but I haven't gotten to that point yet.

I have tried the boot rescue steps suggested in an attachment from one of you but the only command it recognizes is "set".  I've used it to set normal colors and pager and when I entered only "set" I got:

     prefix (0,1)/boot/grub
     root=hd0,1

I see that as a place to start and haven't given up and appreciate that you haven't either.  Keep the suggestions coming and I'll continue responding with my progress.

-Randy

---

### Post by rs321 on 2011-11-10
Folks,

The biggest problem was that I was using a broken CD drive and didn't know it.  I swapped it out this morning with a spare I had around and Ubuntu began installing immediately.

What took so long is that I had just bought a used Dell that was supposed to have just been refurbished but wasn't, and in my naivety I believed them when they told me it had.  I guess shops sometimes lie.  No, the biggest problem was it was a Dell to begin with and didn't get any better with age, but that still doesn't explain why mbr didn't recognize "sudo" or almost every other command I tried but I suppose that has become irrelevent.

I want to thank again everyone who put so much time and effort into helping me get through the last three weeks without resorting to a BFH to rid myself of the problem.  I deeply appreciate your efforts.

-Randy

---

