---
title: "Lost grub after upgrade"
date: 2009-10-31
forum: General Help
---

### Post by ST3ALTHPSYCH0 on 2009-10-31
I don't mean to spam the forums, but I'm not sure of the right one to put this in, so here goes again.

Alright, I did an in place upgrade from Jaunty to Karmic with zero problems. But, not being one to leave well enough alone, I wanted to install the new grub. I followed these instructions: [http://mdzlog.alcor.net/2009/06/21/s...ing-to-grub-2/]("http://mdzlog.alcor.net/2009/06/21/smooth-sailing-to-grub-2/"). I had no problems using the chain loader, but had a brain fart when replacing the legacy grub. I forgot about my win7 and ubuntu installs being on physically separate drives, and now when I try to boot all that comes up is a black screen with the word "Grub" and a flashing cursor.
I have a Jaunty Live CD and a Karmic beta CD. I'd rather not have to reformat and totally reinstall, but if I have to please tell me what directories I'd need to back up and recopy in order to not have to spend hours reconfiguring Gnome. 
Thanks so much, I feel like a retard.

---

### Post by ST3ALTHPSYCH0 on 2009-10-31
Can I use the 0.97xx super grub disk to fix this, or do I have to use the 1.9x? I only ask because the Super Grub server seems to be down, but I don't want to bork up my system any further.

---

### Post by Plumtreed on 2009-10-31
Can you clarify what you want to achieve? I don't really know what you want to do.

You can boot via Grub 0.97.and dual boot etc

---

### Post by ST3ALTHPSYCH0 on 2009-10-31
I *could* dual boot with legacy grub... until I attempted to replace it with grub 2. Now I can't boot anything, and I want to make sure that I;m not going to do further damage if I use a version of super grub that features legacy grub.

---

### Post by ST3ALTHPSYCH0 on 2009-10-31
Alright, I downloaded the grub rescue cd from the super grub disk site, and can now access my Karmic install, but have yet to figure out how to repair my grub install.
Hopefully one of you gurus out there knows how to fix my screw up.

EDIT
This screen is all I get if I don't use a boot disc:
[IMG]http://i94.photobucket.com/albums/l93/ST3ALTHPSYCH0/IMG00057.jpg[/IMG]

---

### Post by ST3ALTHPSYCH0 on 2009-10-31
Alright, I used an older copy of SGD to repair my Windows MBR, so I can at least now boot without some sort of CD, but my Ubuntu install is totally inaccessible with a SG2D in the drive during boot. 
I uninstalled all grub packages with synaptic and ran 
sudo apt-get install grub
to reinstall legacy grub, but my machine still boots straight to Win7.

Do I have to reconfigure grub now? I still don't want to do a full reinstall. Would it be easier to activate the windows boot loader? I don't care what boot loader I'm using just so long as I have the ability to dual boot.

I have learned the lesson of the old idiom "if it ain't broke, don't fix it" through this fiasco.

---

### Post by Plumtreed on 2009-10-31
I had a similar problem and used the SGD after 'sudo update-grub' and after rebooting things were OK.

I am still using Grub not Grub 2

I'm not sure this is helpful but it is all I can suggest?

---

### Post by ST3ALTHPSYCH0 on 2009-10-31
I'll try that tomorrow... well later today. Thank for your input. I should've left well enough alone while I had a grub that was customized to match my desktop theme and worked. At least I can boot my machine into a working OS now!

---

### Post by ST3ALTHPSYCH0 on 2009-10-31
I got it FINALLY!!!! I ran the instructions on reinstalling grub legacy here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2), and installed grub to both HDDs. Thanks to all who looked!

---

### Post by Plumtreed on 2009-10-31
> **ST3ALTHPSYCH0 said:**
> I got it FINALLY!!!! I ran the instructions on reinstalling grub legacy here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2), and installed grub to both HDDs. Thanks to all who looked!

Nice going!

Just to clarify, are you running on Legacy Grub?

---

