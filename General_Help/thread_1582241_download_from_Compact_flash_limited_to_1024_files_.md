---
title: "download from Compact flash limited to 1024 files in Nautilus?"
date: 2010-09-26
forum: General Help
---

### Post by nzcarrick on 2010-09-26
Hello,
I just got an 8 gig compact flash card for my SLR camera. When I open the card (using a card reader) in Nautilus (Ubuntu 10.04) it will only list about 1024 files and not the rest. It does not provide any warnings so one could easily think all files have been copied when in fact they haven't. This could be a real issue if the user does not notice.
Using another app called rapid photo downloader in Ubuntu does not seem to list/preview all the files either.

I duel boot to win xp 32 bit and I can see all the photos and can copy them to the harddrive without any issues so I don't think it is hardware related.
I'm currently in Kathmandu with dodgy internet so apologies if this topic has been covered before - I did do a couple of searches! 
  
Any ideas on getting Nautilus to allow the copy of all files?

Thanks in advance

nzcarrick

---

### Post by ngaio on 2010-09-26
> **nzcarrick said:**
> I just got an 8 gig compact flash card for my SLR camera. When I open the card (using a card reader) in Nautilus (Ubuntu 10.04) it will only list about 1024 files and not the rest.

In the same session, did you also plug in your SLR camera with a memory card with the same name as the memory card in the card reader? That can cause serious problems. 

There are sadly quite a few bugs related to libgphoto2 and Gnome's GIO.

But then again, without more description of the problem, it's very difficult to understand what problem you have run into. Can you replicate the problem, detailing how to replicate it?

---

### Post by nzcarrick on 2010-09-28
Hi Ngaio,

Thanks for your reply, no I did not plug the camera in using a usb cable first. 

The process to repeat the issue:

1) plug usb reader in to netbook using std usb cable. 
(lsusb identifies the card reader as Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External))
2) push 8 gig Compact flash card into card reader. Make sure there are at least 1400 photos on card.
3) Nautilus then presents some options -> I choose to "Open Folder" but choosing rapid photo downloader has the same result - missing photos.
4) After some time, the previews are loaded and I scroll to the bottom of Nautilus. The last item listed is photo 1022 even though there are many more photos on the card which I can see when the card is in the DSLR by looking at the review screen on the DSLR. No warning is given.

I assume a nautalus or gnome error as ( i hate to say it but ) windows previews and copies all photos using the same hardware and process above.

Regards

nzcarrick

---

### Post by nzcarrick on 2010-10-01
...bump

---

### Post by ngaio on 2010-10-04
I suggest taking a look to see if there are any messages generated via the command dmesg (run from the command line) or in ~/.xsession-errors.

Another thing to try is doing a directory listing from a terminal window. If you have access to another incarnation of Linux, e.g. I'd try it in that too (something that is not running Gnome). 

These are simply different ways to try to narrow down the problem. I have never come across the problem you describe. I've not had 1000+ images on a single card before, but I have had about 30GB worth on a single card.

---

