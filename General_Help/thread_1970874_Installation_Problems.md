---
title: "Installation Problems"
date: 2012-05-01
forum: General Help
---

### Post by Musicmaker384 on 2012-05-01
So it's been a while since I've used Ubuntu, and I'm starting to miss it. I want to install it so I can fall back on it if Windows decides to explode (which it seems to have a habit of doing). Anyway, I'm trying to have my computer multiboot Windows 7 and Ubuntu 12.04. I have the image burned to a disk and ready to go. I have a new partition (Drive "U" 8) ), 165gb, that is nice and clean. I want to get Ubuntu on it, but I'm having problems installing...

I understand you have to restart the computer with the CD in the disk drive in order to install Ubuntu.

First, here is a screenshot of what was burned to the CD. Is it correct?

[ATTACH]217065[/ATTACH]

If that's right, then I have no idea what's going on. For some reason, when I restart my computer, the computer will not boot from the CD. It will just boot into Windows like it normally does. **Yes, I have used Google** extensively in order to try to solve this problem. It gave me this solution:

Go into the computer's BIOS to see if it is set to try to boot from the CD drive first. I was told to press the Delete key or F2 upon startup to get into the BIOS. I have tried this multiple times. Neither worked. Scratch that idea.

I tried to install the Ubuntu CD Boot Helper, but every time I try I get this error:

[ATTACH]217064[/ATTACH]

I'm new at this, so I have no idea what that means. Anyway, scratch that idea too.

If anyone can tell me what I did wrong here, I'd really appreciate it...

---

### Post by jerrrys on 2012-05-01
Quote"Go into the computer's BIOS to see if it is set to try to boot from the  CD drive first. I was told to press the Delete key or F2 upon startup to  get into the BIOS. I have tried this multiple times. Neither worked.  Scratch that idea."

You can't scratch that idea, it has to boot from CD/DVD in your BIOS.

---

### Post by Musicmaker384 on 2012-05-01
Quote "it has to boot from CD/DVD in your BIOS."

I know that. That's what I'm having trouble doing. I have no way of getting to the BIOS configuration tool, nor am I able to boot from the CD/DVD. I'm trying everything I know how. Like I said, I'm new at this.

---

### Post by jerrrys on 2012-05-01
What make/model of computer is it?

---

### Post by holycow131415 on 2012-05-01
When your computer turns on, at the splash screen it says which button to push to enter the boot menu. Each computer/model is different. Mine for instance is F10

---

### Post by Musicmaker384 on 2012-05-02
I have an HP Pavilion G6-1d60us notebook PC.

As for the boot splash screen, all I get is "Press ESC for boot options menu" or something along those lines. I can get there, but the Windows Boot Manager gives me nothing about the BIOS, only options for booting into Windows like Safe Mode and boot logging.

---

### Post by jerrrys on 2012-05-02
According to HP PDF you have to use "Setup Utility" and F10.

[ATTACH]217104[/ATTACH]

Chapter 6; page 86

Also can look thru here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=HP+Pavilion+G6&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=HP+Pavilion+G6&sa=Search&cof=FORID:9)

---

### Post by Musicmaker384 on 2012-05-02
Alright, thanks. I'll check this out and see if the BIOS is configured to boot from the hard drive first. Chances are it's not, and my CD image was a bad burn, but I'll look anyway.

---

### Post by Musicmaker384 on 2012-05-02
While your information wasn't entirely accurate, jerrrys, I was able to get into the BIOS configuration menu (I had to press F10 immediately after startup). The boot priority was indeed to set to boot from the hard drive first, not the DVD/CD drive. I changed it and rebooted, and was able to boot from the CD. But now I have a different problem - setup hangs. I see a few words: Loading ISOLINUX, and a few other things. The screen then goes blank, and stays that way. _I am immediately led to believe this is because of a bad burn._ From what I've heard, bad burns are common. Is this a possible cause?

---

### Post by jerrrys on 2012-05-02
You can checksum and checkdisk.  Also burn at low speed, I burn at 8x.

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

---

### Post by Musicmaker384 on 2012-05-02
I guess I should have considered burning slower than 'maximum speed'. I'll burn at 7x. That should do the trick.

I'm marking this thread as solved, since the initial problem has been resolved. 

Thanks for all your help.

---

