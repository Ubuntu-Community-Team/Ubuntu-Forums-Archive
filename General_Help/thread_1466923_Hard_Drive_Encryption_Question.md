---
title: "Hard Drive Encryption Question"
date: 2010-04-30
forum: General Help
---

### Post by gunksta on 2010-04-30
I'm using a fully updated Lucid install.

I am going to be doing a lot of travel in the next few months and I would like to increase the physical security of my laptop. I don't encrypt my home directory, because of the performance penalty, but I do encrypt individual, sensitive files. Usually these are large SPSS, Access or Text files with lots of private information.

I am confident that these files are secure, but in general would like to up my security.

I am considering using a BIOS/Hard-Drive password. I know the BIOS is capable to locking both on this model of Dell. But, I've got two questions - 

1) Will setting the hard-drive password mess up Grub2? I'd rather not damage my installed system.

2) Is there an obvious way around this protection that I am over-looking. I know BIOS only security was widely panned, because it could be easily circumvented by removing the hard-drive from the system, rendering the BIOS lock moot. A hard-drive password seems to me to be more secure, but I may be over-looking something equally obvious.

Thoughts, suggestions, etc. welcome.

---

### Post by pcura on 2010-04-30
if you really want a secure files without even using encryption just get a usb flash drive and keep your private file there, this way, you know nobody will be snooping/hacking thru your computer

just my 2 cents

---

### Post by gunksta on 2010-04-30
I'm not worried about personal files, I'm concerned about system security / protecting our clients. Most of the personal stuff I need to access from work I get via ssh -X or Google Docs.

Besides - a USB key doesn't address the security issue at all. I want to secure the system from accidental loss / theft. A USB key is no more secure in this way than a laptop.

---

### Post by pcura on 2010-04-30
i could only say is 10.04 is very new and still in the bug/glitches process.

---

### Post by psusi on 2010-04-30
If you set the disk password then your bios will have to prompt you for it to unlock the disk before you ever get to grub.  Grub won't know or care that you had to enter a password to get that far.  Of course, the data is still on the disk so if someone were motivated enough, they could get take the drive apart to get around the password.

---

### Post by gunksta on 2010-05-01
That's what I was hoping. I thought I had read somewhere that setting the password could fiddle with the MBR, which worried me. I can redo the system, but that doesn't mean I want to.

Of course someone could remove the platters and move them to another drive, but no security is perfect. My goal is to minimize the # of people with the technical skills to beat my security.

---

