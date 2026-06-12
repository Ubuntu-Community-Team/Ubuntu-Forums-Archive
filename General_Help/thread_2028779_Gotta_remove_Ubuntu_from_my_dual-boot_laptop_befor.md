---
title: "Gotta remove Ubuntu from my dual-boot laptop before the Windows Police catch me!"
date: 2012-07-18
forum: General Help
---

### Post by t0p on 2012-07-18
I bought a Packard Bell laptop 2 weeks ago.  It came with Windows  7 already installed, along with a bunch of apps, eg Photoshop Elements 8.  I thought it was okay, so I did a side-by-side installation of Ubuntu 12.04.  Everything's been working fine... until now.  For no apparent reason the touchpad and buttons have stopped working - in Windows as well as in Ubuntu, so I figure it's a hardware problem.  A breakdown so soon after purchase, I should be able to go get a replacement, right?

But I don't know if that *is* right.  I live in England, so we're talking English law.  I can remember seeing stuff on the web about how people have been refused proper service cos they had installed Linux on their computers and apparently voided the warranty or some such ridiculousness.  I can't remember where these folk lived, so I dunno... should I remove all traces of Ubuntu from the laptop before I take it back to Comet (big UK electrical goods chain)?  And how would I even do that?  All the Windows stuff was already installed, right? So I don't have a Windows 7 DVD.  I made myself a Windows system repair disk soon after purchase (as advised by the initial Windows 7 "first use" wizard), but can that help?  And when I did the side-by-side Ubuntu installation, it used grub, so that's gonna have screwed the Windows MBR or whatever it's called, right?

Or am I worrying about nothing?  In English law, a retailer has to make sure any goods he sells you are "of merchantable quality" or something, basically it's gotta be fit for purpose (the Sale of Goods Act, I think).  And a laptop whose touchpad dies after a fortnight of careful use sure as heck *isn't* fit for purpose, right?  But but but... what about the Ubuntu thing?

Anyone who has advice, whether technical (how to make the laptop look like it never even *seen* Ubuntu) or IANAL "legal advice" (maybe from personal experience?) will be oh so welcome.  The laptop works with a USB mouse, but that's not the point, right?  Heck, the EeePC 701 I'm using to post this right now is about 5 years old, and nothing's broke on it yet.

Cheers.

---

### Post by pe7er on 2012-07-18
I don't have much knowledge of the UK legal system,
and I haven't had the need myself to remove Ubuntu from my dual boot laptop, but I found: 
[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/)
[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

With [https://www.google.com/#hl=en&q=uk+warranty+void+laptop+linux](https://www.google.com/#hl=en&q=uk+warranty+void+laptop+linux) I found some claims from people who seem to have their warranty voided by installing Linux :(

I don't know how far the EU law applies in the UK regarding warranty, but to save time & hassles, maybe you'd indeed better remove Linux (& assign all space to Windows again) before returning it...

---

### Post by blackflame2996 on 2012-07-18
to get rid of ubuntu, you should be able to run a ubuntu live disk, open GParted on it, and eliminate your ext4 and linux-swap partitions, and the extended partition in which they are located, if applicable. after that, extend the windows NTFS partition to fill the resultant empty space. now remove grub and restore the windows bootloader: [http://blog.eukhost.com/webhosting/howto-remove-grub-loader-and-restore-windows-7-and-vista-bootloader/]("http://blog.eukhost.com/webhosting/howto-remove-grub-loader-and-restore-windows-7-and-vista-bootloader/")
boot windows 7, it will run CHKDSK, which may take several hours, depending on how much is in the NTFS partition. Your computer should now seem to have never been altered.

---

### Post by Primefalcon on 2012-07-18
forget chkdsk the command to fix th mbr (main boot record) is fixmbr

to make a point and stand I'd say stand up to them...

to be sensible, I'd say use that system disk you made to restore windows to factory condition.... 

what I'd recommend to use alive disk o delete the ubuntu partition and then resize your windows partition to full usage again...

then just boot up from that disk that you made and boot to a recovert prompt and run the command fixmbr, and you should be good to go

---

### Post by Mark Phelps on 2012-07-18
Removing Ubuntu will also remove a legitimate reason for them refusing to honor any warranty -- but standing up to them serves no useful purpose.  The Seller makes the conditions under which warranties are honored, NOT the buyer.

Sure, you MIGHT be able to sue them.  But, here in the "states", taking even a simple case to trial costs upward of $30,000 -- and my guess would be that in the UK, the cost would be much the same, except in Pounds, not dollars.

Would be a lot cheaper to buy another machine.

---

### Post by greenpeace on 2012-07-19
Well, it sounds like whether or not you've installed ubuntu onto it, it's a hardware problem... it's not a problem with software or the OS.

Check the terms of your warranty with Comet, or even ring one of their Technical Services departments (anonymously if you prefer) and ask them if they have seen it with other laptops, or if they would be prepared to replace it/fix it.

Be aware that they may want to *fix* it, rather than give you a brand new one.. which could mean a few days without your box.

---

### Post by t0p on 2012-07-19
> what I'd recommend to use alive disk o delete the ubuntu partition and then resize your windows partition to full usage again...

then just boot up from that disk that you made and boot to a recovert  prompt and run the command fixmbr, and you should be good to go

As I am pretty clueless when it comes to Windows, can someone please verify that after I've deleted the Ubuntu partition and resized the Windows partition, will I then be able to boot from my Windows Repair Disk?  ie. the act of removing Ubuntu this way won't make the computer unbootable?  A noob question, I know, but I don't want to end up bricking the thing!

---

### Post by Megaptera on 2012-07-19
After removing Ubuntu, you'll have to ensure the BIOS is set to boot from cd/dvd and then boot to your first restore disc. The guide at link shows 'Install' disc but I used its equivalent for Vista using restore discs to fixmbr. You only need the first part of the guide.
[http://www.howtogeek.com/?post_type=post&p=32523](http://www.howtogeek.com/?post_type=post&p=32523)

---

### Post by t0p on 2012-07-19
OK, using gparted on ubuntu live disk, I deleted /dev/sda4 (the ubuntu partition), and now it's shown as "unallocated space".  But I can't resize the windows partition (/dev/sda3) to enlarge it - It will only let me shrink it.  

Do I have to do something to the "unallocated space" before I can enlarge /dev/sda3?  When I select /dev/sda4 then look at the Partition menu, everything is greyed out except Resize/Move, Manage Flags and Information.

How do I enlarge /dev/sda3 into the unallocated space of /dev/sda4?

EDIT: here's a screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=221495&stc=1&d=1342707153[/IMG]

---

### Post by cool110 on 2012-07-19
As sda4 is an extended partition you need to delete sd5 (most likely encrypted swap) inside it before being able to properly delete sda4 to gain proper unallocated space (which will merge with the 1.02MiB at the end). Then you can increase the size of sda3.

---

### Post by arpanaut on 2012-07-19
You will need to remove the sda5 partition that is within the extended part.
Then you will have to delete the extended partition to make it unallocated space.
Then you will be able to add that space to the partition above it.

---

### Post by Merrattic on 2012-07-19
Once you have sda5 and the extended partition deleted. I would advise that you stop there and reboot with your repair dvd to repair the mbr so you can boot windows. Once in windows use the computer management tool to resize the windows partition. This is much safer than doing it through gparted.

---

### Post by t0p on 2012-07-19
Oh wow, I have to thank *everyone* who offered advice.  I got it done through gparted (before I saw your post Merrattic) then used command line on my Windows 7 System Repair Disk to recreate the MBR.

The Free software community *rocks!!!*

:guitar:

---

