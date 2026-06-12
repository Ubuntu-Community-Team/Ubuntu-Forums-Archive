---
title: "How can I put Windows Vista &amp; Ubuntu in one DVD?"
date: 2009-12-05
forum: General Help
---

### Post by checoimg on 2009-12-05
Thanks for your very valuable help.
I do not have a clue on how to do this. 

I have DL DVD 8.5 GB and I want to burn it with the Open Artist distro along with the Vista DVD so it tells me wich Operative System I want to install or if I want to dual boot any of this options are good for me. Just in case that distro is based on Ubuntu. Thanks agains.

---

### Post by ankspo71 on 2009-12-05
Hi,
I never used a Dual Layer burner before so I don't know the answer to your main question. However, I have not been able to burn two iso's on a regular 4.7gb dvd before.

According to the following link, OpenArtist is based on Ubuntu Hardy (Ubuntu 8.04).
[http://www.blendernation.com/new-linux-distro-for-artists-openartist/](http://www.blendernation.com/new-linux-distro-for-artists-openartist/)
James

---

### Post by checoimg on 2009-12-05
I am glad for your aswer and you are right on pointing that. What I thougt is that if it is possible to make partitions on a hard disk maybe there could be found some commando or application that would handle both ISO before installation as grub loader does. I know its not the same but that is the part I did not write so well.

Thankyou very much I wil wait for your response.

---

### Post by fluffman86 on 2009-12-05
Try looking into Grub4Dos, ubcd, and ubcd4win.  When I installed UBCD4Win onto my thumbdrive (or a CD, I suppose), it creates a grub loader called grub4dos.  grub4dos is actually able to point to and mount an ISO file on the spot.

Currently, I have what I call my Ultimate Boot USB drive.  First, I installed UBCD4Win, which installed grub4dos and lots of nifty windows tools that run in a windows pre-install environment (like Bart PE or WinPE).  Then, I used usb-creator in Ubuntu to install Ubuntu.  You can edit a config file in the syslinux folder (text.cfg?) which contains the options that you see when you boot the CD (Try the Live Version, Install Ubuntu, MemTest, etc.) and add an option that points to the grub4dos install as a new "kernel."

After that, you could do the same for Open Artist, again pointing Ubuntu to the Open Artist kernel.  Or maybe the other way around...

Now, I'm not sure how you would go about getting all of this on the CD, or if it would even be possible.  But most computers now boot off of USB, and that's definitely faster.  And if the BIOS doesn't boot from USB, then you can also look into Plop Boot CD, which boots the computer from CD, then lets you select your USB drive and boot from that.

Sorry that this is all kinda vague, but it's just my ideas on the matter.  You'll come up with your own system, I'm sure.  If you need any more ideas/help, just holler.  I'm subscribing to this thread.

---

### Post by checoimg on 2009-12-05
I have DL DVD 8.5 GB

I wil look for a way to make the ISO without burning it so I can test it on virtualbox. Any help on that is pretty good. Thanks again. :)

---

### Post by fluffman86 on 2009-12-05
Ah, just had another idea.  Start with doing the USB as I did, then I'm sure there'll be a way to convert all of the files on the USB to an ISO.

---

### Post by checoimg on 2009-12-07
Any clue on how to do that I have been looking for answers on the forum and now googling.

Thanks again. :)

---

### Post by fluffman86 on 2009-12-07
actually, just burning all of the files onto the DVD might work, or if you want the image you can use the mkisofs command from a terminal:
[http://www.granneman.com/techinfo/linux/burningcds/makeanisoimage.htm](http://www.granneman.com/techinfo/linux/burningcds/makeanisoimage.htm)

---

### Post by checoimg on 2009-12-14
OK I will do it this way andl be back to telll what happened.

---

### Post by ST3ALTHPSYCH0 on 2009-12-14
Can't you open .isos with the archive manager (if not you can with 7zip)? You could just combine everything into separate folders in one iso, then you just have to write a bootable menu. Just a thought.

---

