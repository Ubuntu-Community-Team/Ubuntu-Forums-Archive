---
title: "No ALT-CTRL-F1 Terminal"
date: 2010-06-07
forum: General Help
---

### Post by oboonto on 2010-06-07
Hi,  I have installed Ubuntu 9.10 on a Laptop and upgraded to version 10.04 Lucid Lynx.   I'm missing the ALT-CTRL-F1 .. F6 terminals. All I see is a pattern of vertical lines and bars in the colors of my gnome desktop. Each time I switch from graphic mode to textmode the pattern shows a different variation of these colors.  Also the boot splash screen does not appear but I don't really miss it.     What I've tried so far:      - re-installed packages and updates     - started the kernel with vga=792, vga=791 and vga=773 (1024x768 LCD)     - changed shared memory size and APG aperture in the BIOS settings (I'm using a laptop with framebuffer video), currently I have 16MB shared and 64MB aperture.     How do I get the text mode terminal?    Best regards,  oboonto                                                                                                                                                                                                   ps: how do I insert line feeds into my posting?

---

### Post by #!/bin/bash on 2010-06-07
Make sure you have the correct framebuffer module for your video card. The [Framebuffer HOWTO ](http://www.faqs.org/docs/Linux-HOWTO/Framebuffer-HOWTO.html) might help.

I just press <Enter> at the end of a line.

---

### Post by oboonto on 2010-06-07
I could boot Knoppix or Ubuntu from a live CD - how do I find out what frame-buffer module it uses? --------------------------------------------------------------------------------------------------------------------------------------------   ------------------------------------------------------------------------------------------------------------------------------------------- I'm using the ENTER key but it doesn't insert line feeds. BTW, I'm using Firefox under Windows. Is there a trick to generate the Linux-code for linefeeds?

Ubuntu 9.10 Live CD:
> VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03) Kernel modules: vt8623fb

Installed Ubuntu 10.04:
> VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03) Kernel modules: vt8623fb, **viafb**

Should I get rid of **viafb** and how do I?

> Framebuffer drivers are generally buggy and poorly-supported, and cause
# suspend failures, kernel panics and general mayhem. For this reason we
# never load them automatically.
blacklist aty128fb
.
.
blacklist viafb
blacklist vt8623fb[FONT=Arial][SIZE=2]Framebuffer drivers are blacklisted but viafb and vt8623fb are still being loaded.[/SIZE][/FONT]
> root@G320:~# lspci -k | grep -A2 -i vga
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)
    Kernel modules: vt8623fb, viafbWhere are Ubuntu's textmode settings and how can I change them in order to work correctly?

---

### Post by zion2k on 2010-08-11
Hi,

I have the same probleme. Do you have solved it?
I got the previous versions (8.06 - 9.10) working with the boot option fb=false, but since 10.4 it is not working anymore.

---

### Post by oboonto on 2010-08-11
No, I didn't solve it. Same thing happened again with a new 9.10 installation and subsequent 10.04 upgrade on an similar laptop.  Must be the upgrade. I shall now try a new installation of 10.4.

---

### Post by Cabalbl4 on 2010-08-12
Maybe it is an error of non-started tty.
Try
```
sudo stop tty1
sudo start tty1
```

Then try ALT-CTRL-F1

Btw, i did get some problems with TTY garbadge because of bootlogo. May be a good idea to disable it in grub.

---

### Post by Gone fishing on 2010-08-12
I had a similar problem - with a clean install of 10.04. However, after the first update it resolved itself.

---

### Post by oboonto on 2010-08-12
No, stopping and re-starting didn't change anything.  So I'd better do a fresh install of 10.4 and update. What exactly did you update?

---

### Post by Gone fishing on 2010-08-13
Just  through update manager.

Also you could have a look at [http://ubuntuforums.org/showthread.php?t=1480015](http://ubuntuforums.org/showthread.php?t=1480015) and [http://ubuntuforums.org/showthread.php?t=1480015](http://ubuntuforums.org/showthread.php?t=1480015) 

are you also using the latest video driver?

---

### Post by robsoles on 2010-08-13
> **oboonto said:**
> Hi,  I have installed Ubuntu 9.10 on a Laptop and upgraded to version 10.04 Lucid Lynx.   I'm missing the ALT-CTRL-F1 .. F6 terminals. All I see is a pattern of vertical lines and bars in the colors of my gnome desktop. Each time I switch from graphic mode to textmode the pattern shows a different variation of these colors.  Also the boot splash screen does not appear but I don't really miss it.     What I've tried so far:      - re-installed packages and updates     - started the kernel with vga=792, vga=791 and vga=773 (1024x768 LCD)     - changed shared memory size and APG aperture in the BIOS settings (I'm using a laptop with framebuffer video), currently I have 16MB shared and 64MB aperture.     How do I get the text mode terminal?    Best regards,  oboonto                                                                                                                                                                                                   ps: how do I insert line feeds into my posting?

hi oboontu, to answer one of your easier questions first up: please insert line feeds to your 'postings' each time ;)

Did you read everything the first responding user linked to in his post?
> **#!/bin/bash said:**
> Make sure you have the correct framebuffer module for your video card. The [Framebuffer HOWTO ]("http://www.faqs.org/docs/Linux-HOWTO/Framebuffer-HOWTO.html") might help.

I just press <Enter> at the end of a line.

When they wrote "I just press <Enter>" they were referring to to your very last question ;)

Have you resolved this problem?

---

### Post by oboonto on 2010-08-13
Where's the ENTER key?  I just got a Carriage-Return key like the one that typewriters used to have. And I'm using Windows, maybe that's the cause. I can't boot Linux every time I answer to this thread just for the shortcomings of a poorly configured vBulletin installation. Other BBSes do understand my END-OF-LINE codes.

---

### Post by robsoles on 2010-08-13
LOL.

Soz, though I get the feeling I must be in a game thread - honestly!!!!

Yes, ummmm, "Carriage Return"==[Enter]

but it sounds like you are operating some equipment from about 1955 there (LOL, alright maybe it's from 1995!!!!)

Umh - If you can't boot '''''linux'''''' every time you answer to this thread then i wonder if I am not really in a joke thread - I will be back in about 8 hours very sober and very ready to be real serious, will you?

---

### Post by oboonto on 2010-08-13
> **robsoles said:**
> LOL.

Yes, ummmm, &quot;Carriage Return&quot;==[Enter]

[...]I will be back in about 8 hours very sober and very ready to be real serious, will you?
 Sure will I. At least e-messaging works with this board, unlike with many other BBSes. 

 Answering with quoted text displays HTML codes. Perhaps I'm supposed to use the <br /> code in absence of the ENTER (==LINEFEED) key

appears to work
appears to work
appears to work
appears to work
appears to work
appears to work
appears to work
appears to work...

@robsoles

I invested a lot if time in the framebuffer issue. Please have a look at posts #4 and #5. Gnome is working correctly with these drivers. Where do I find the tty-console settings?

---

