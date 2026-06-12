---
title: "Does the u equal the u?"
date: 2011-08-02
forum: General Help
---

### Post by bradlees on 2011-08-02
Sorry for the harsh words, but I need help. I have tried to load my hd with ubuntu a bunch of times. got a 80g hd with xp on it now. Have another hd 150g with xp too, would like to put ubunto on the small hd. I have formatted clean, put xp back on, tried to boot from usb, tried to boot from live, tried the wubi and nothing f'ing works. 

All i want is ubuntu running on my pc clean and I will gladly join the community.

Give me some guidance, please, I know my media was getting burned bad the past few attempts, but now I have a live install cd running that has not moved in hours, and I verified it with the menu options before trying to boot from the disc.

---

### Post by Furball588 on 2011-08-02
So maybe some specifics about what fails or isn't working..

If it's any easier, maybe temporarily removing the 150 gig drive would be the way to start out.

---

### Post by Rubi1200 on 2011-08-02
Please post the full specifications for the computer in question and, as suggested above, details on what steps you have taken and what is going wrong at each stage.

Also provide details about other operating systems on the computer and especially if you already have 4 primary partitions (the maximum allowed in most cases).

The more you tell us, the better we can help you.

---

### Post by bradlees on 2011-08-02
Thank both of you. I have disconnected the other hd, so thats it. 
Has and emachines 2.93 ghz pentium 4 processor, with the 81g and150g. Both have working version of sp. Wubi gives a message about ntldr not being there. The live cd goes nowhere, freezes during intsalll. Let me know how I make this u something else.

Let me know,

---

### Post by EkuquoL on 2011-08-03
So you want to boot Ubuntu from a external hard drive?
Well you can extract an ISO to a external hard-disk using Winrar in Windows XP.

If you are trying to install Ubuntu too the external hard disk via a USB port

You will have to first go to your BIOS... Set up the Advanced configurations for boot --
 Boot from CD as your first option... 
Boot from USB as your second option ..
 Boot from Hard disk as your third.

Then when you install Ubuntu select the external drive as your storage device. 

Once you restart your computer you should have it load ... As long as you set up your computer Bios to boot from a USB.

To get to your BIO .. You will have to restart your computer and press DELETE at the *very* first startup screen. Before Window loads.

---

### Post by Furball588 on 2011-08-03
> **bradlees said:**
> I have disconnected the other hd, so thats it. 

From the way you sound, there's nothing you need to save on that HD.  Just set the boot order in your bios to boot from the CD Rom first and let the livecd start from there.  When in there, there will be a short cut to actually install on the HD.

---

### Post by Wim Sturkenboom on 2011-08-03
> **EkuquoL said:**
> So you want to boot Ubuntu from a external hard drive?
I did not see that mentioned; what did I miss?

> **EkuquoL said:**
> So you want to boot Ubuntu from a external hard drive?

To get to your BIO .. You will have to restart your computer and press DELETE at the *very* first startup screen. Before Window loads.Or <F2> or ... Depends on the BIOS

---

### Post by bradlees on 2011-08-03
the u equals nothing right now, null set some ****. Tried with an internal hd, a usb and generideviec and not a one works. the media was faulty at some point, but through process of elimination, a man will stand. Unite the tribes.

---

### Post by bradlees on 2011-08-03
I know how to get into bios and select boot order, etc. And I don't mean to sound like a ****, but things are starting to get annoying. i don't care about the hd, restored xp to it bc it wouldn't do anything with a wiped hd at all. Basically, got a system with a blank os, would like a linux-based set up on my c: drive. Anyone?

---

### Post by Furball588 on 2011-08-03
> **bradlees said:**
> I know how to get into bios and select boot order, etc. 

So what's stopping you from setting the boot order to boot to the CD first and then allowing that to actually boot the CD? :)  Obviously, you're seeing the disk because you were referring to Wubi earlier.

Unless there's something wrong with the drive, I see no reason why this wouldn't boot to the CD.

---

### Post by new_tolinux on 2011-08-03
> **bradlees said:**
> I know how to get into bios and select boot order, etc. And I don't mean to sound like a ****, but things are starting to get annoying. i don't care about the hd, restored xp to it bc it wouldn't do anything with a wiped hd at all. Basically, got a system with a blank os, would like a linux-based set up on my c: drive. Anyone?

How about just booting from the CD-ROM and install it?
As for what I read, you don't care about any data on the attached harddisk, also, what could go wrong?

---

### Post by bradlees on 2011-08-03
Exactly why I am so perplexed. The drive was re formatted and nothing would install on it. I tried all media on the hd, cds and usbs through different windows, torrentys, etc. Couldn;t get anything to work. Finally, last night, I discovered that the media, which I thought was good, was also viable as my friend tried to upgrade his existing membership in the public circuit.

Seems like everything i have downloaded and formatted to disk to boot or to usb, or disk as a legacy drive, has failed. Please let me know if you see a simple keystroke or setting I have missed Let me know what these guys are waiting for....:confused::confused:

---

### Post by new_tolinux on 2011-08-03
> **bradlees said:**
> Seems like everything i have downloaded and formatted to disk to boot or to usb, or disk as a legacy drive, has failed.
That's exactly why it's advised to check the MD5-hash of the ISO before burning it....

---

### Post by bradlees on 2011-08-03
I didn't check that, at the ubuntu options at the first screen I ran a check disk and that came back good. Also, my seat was really hots.:(

---

### Post by bradlees on 2011-08-03
Dudes, nothing seems to work the way its supposed to. I'm gonna let ubunt run right now for 5 hours and see if it boots tomorrow morning. See if it works with that great big helmet hairpiece that salesman has. 

Godspeed.

---

### Post by jocko on 2011-08-03
> **Furball588 said:**
> Just set the boot order in your bios to boot from the CD Rom first and let the livecd start from there.

> **Furball588 said:**
> So what's stopping you from setting the boot order to boot to the CD first and then allowing that to actually boot the CD?

> **new_tolinux said:**
> How about just booting from the CD-ROM and install it?

Can't you guys just read bradlees' posts before you reply? 
If you did you would see that he do know how to boot from cd, but the installer freezes:

> **bradlees said:**
> ...The live cd goes nowhere, freezes during intsalll.

But this could be a good thing to check:
> **new_tolinux said:**
> That's exactly why it's advised to check the MD5-hash of the ISO before burning it....
If you've downloaded a bad iso, you can burn it or make install USBs a hundred times, it will still fail in the same way every time if the iso you start with contains corrupted data.
I don't think the live cd boot menu option to check the disk will actually verify every bit of data, so it may very well miss things that a md5 sum check on the iso would detect...

---

### Post by bradlees on 2011-08-03
Considering the amount of sources and different medium i have used fo r the iso, I don;t think that this can be the source of the problems.  I have tried p2p, torrents, live cd downloads, lies, cds, dvds, usb drives, ota's, etc. And nothing seems to shine through. Who else is getting to this u?

---

### Post by jocko on 2011-08-03
Bradlees:
You say you have tried both cd and usb, but you haven't told us if they both fail in the same way (i.e freezes during install) or if the usb fails in some other way.

If they both fail in the same way, there is either something wrong with the iso you make your install media from, or there is a bug in the installer or live cd system that makes it freeze on your computer.

The first option you can detect by checking the md5 sum of the iso. If the md5 sum is bad, download a new iso, check the md5 sum on that, make a new install usb and try again. 
The second could possibly be solved by passing some advanced options to the live cd kernel. Press F6 when you see the live cd boot menu and try setting one or both of "noapic" and "nolapic". That can solve some hardware-related bugs that can make the os freeze.

Edit: Ok, I see you have tried several isos, so the md5 sum check will probably not help...

---

### Post by bradlees on 2011-08-03
the cd's freeze, at least that's what it seems. my systems old and a little slow. I'm gonna give it some extended time after this message to see. The usb gets me nowhere whidch I think is me not being able to rock out!

---

### Post by Furball588 on 2011-08-03
> **jocko said:**
> Can't you guys just read bradlees' posts before you reply? 
If you did you would see that he do know how to boot from cd, but the installer freezes:

I did miss where he said he was freezing with the livecd and in hindsight they're now reinforcing that

Truthfully though, there's a lot of dancing around between installing XP  to do something with installing linux (at least that's the impression I  get)

---

### Post by Furball588 on 2011-08-03
@Bradlees

Have you tried the alternative installation disks from the link below?

[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

It is a text based installer rather then a GUI installer.  Still fairly easy to follow and work though. :)

---

### Post by 3Miro on 2011-08-03
A bit of a guess here, but how much is the RAM on your machine. For Pentium 4, it may be 256MB. LiveCD doesn't run well on 256MB (installed version would run, but the live one would not). If you have 256MB of RAM, then you should get the "Alternate" installer, it is less shiny and even a bit clumsy, but it does the job (it even has more options than the regular installer and it can be more confusing).

---

