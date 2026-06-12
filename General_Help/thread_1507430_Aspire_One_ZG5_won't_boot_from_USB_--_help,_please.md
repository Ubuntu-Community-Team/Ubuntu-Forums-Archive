---
title: "Aspire One ZG5 won't boot from USB -- help, please!"
date: 2010-06-11
forum: General Help
---

### Post by mailman1175 on 2010-06-11
Honestly, I don't know if this issue begins with hardware, software, BIOS, GRUB, or something else. There's a lot of detail here, in hopes that one of you old hands will have some ideas.

I have an Acer Aspire One ZG5 that I'm trying to upgrade to a Lucid spin of some kind (from Karmic), but it won't boot from USB -- flash media or optical media -- with one exception. That exception is going to take a bit of explaining, though, I'm afraid.

USB flash media are a total fail. I have three different flash drives -- different brands, different sizes; two are brand new, bought because I thought the problem might be bad flash media (my old one had a bad superblock). The machine will boot from none of them, given several different methods of preparing the drives. My external optical drive (an LG DVD burner) does some funny things. For instance, when I load a blank disc in the drive while using Karmic on my machine, it never spins up and recognizes that there's blank media in the drive. It will, however, spin up and recognize blank media if I connect it to my sister's Aspire One, running exactly the same distro. [SIZE=1]*[There are a couple of differences between her machine and mine: Hers was originally an XP machine, with the 160GB HDD (mine was Linpus/SSD), and hers hasn't ever had the BIOS flashed (mine is updated to v.3310). Also of note is the fact that the optical drive also won't spool up and show the presence of media when connected to my MacBook, running Snow Leopard.]*[/SIZE]

So, the exception to the rule is if I connect the optical drive to her machine first, let the drive spin up, then connect it to mine before booting. Flash media mount, read and write just fine in Karmic. The machine recognizes the flash drive on boot, but when I select it from the BIOS menu, it immediately boots to the native OS.

I've spent some time binging around the internet for folks with similar issues, and haven't found a thing. A post on [Aspire One User Forums]("http://www.aspireoneuser.com/forum/viewtopic.php?f=5&t=20609") has generated a lot of views, but not a single response. I thought maybe it was an issue with the optical drive's firmware, but LG doesn't even show the drive on their site anymore, let alone a firmware update. If it were strictly an issue with the optical drive, though, I would expect flash media to work properly. If it were an issue with the hardware on the AAO itself, I wouldn't expect any USB device to function properly in the OS, either.

That leaves me thinking it might be a BIOS issue or a GRUB issue. But I don't have the foggiest idea how I could troubleshoot that. So, some questions (aside from the obvious, "What the heck is going on here?!"):


[LIST]
[*]How can I create a bootable FreeDOS CD to try reverting to an earlier BIOS version? I've used unetbootin before to create bootable USB sticks, and I typically use dd to create Live distro discs. Can I just download a FreeDOS image, dd it to a CD-R, then copy the BIOS files over to it? I can get access to my sister's AAO for an afternoon to try a few things...
[*]If reverting to an earlier BIOS doesn't do the trick, what's next? or, What are the other possible roots to this issue?
[/LIST]
I know there's a lot of info here, but I'm stumped. And a netbook that won't boot from USB except under very strict circumstances is a very strange beast, indeed. If I were completely happy with Karmic, it wouldn't be an issue. But one of the joys of Linux is being able to try out different spins and releases as they come out.

Furthermore, I'd like to upgrade the machine's SSD to a larger, faster unit. My best bet is to do a fresh install after I do that, but even if I just imaged my current drive, I'd still have to boot from USB to re-install that image on the new drive.

So, thanks in advance for any help y'all can give! :popcorn:

---

### Post by wyliecoyoteuk on 2010-06-11
couple of questions:
1. how are you creating the USB bootable image?
I usually use Unetbootin, having had some issues with the ubuntu USB disk creator
2.How are you trying to select USB boot?
It works for me only if I press F12 to select the boot device, what ever I tell it in the bios.

---

### Post by mailman1175 on 2010-06-11
> **wyliecoyoteuk said:**
> couple of questions:
1. how are you creating the USB bootable image?
I usually use Unetbootin, having had some issues with the ubuntu USB disk creator

I have tried unetbootin, ubuntu's USB disk creator, and a  simple dd.

> **wyliecoyoteuk said:**
> 2.How are you trying to select USB boot?
It works for me only if I press F12 to select the boot device, what ever I tell it in the bios.

F12. I don't bother with modifying the boot order in BIOS.

---

### Post by mailman1175 on 2010-06-13
Solved:

Operator error. :oops:  I had formatted my USB sticks as ext2 instead of FAT32. Doh!

---

