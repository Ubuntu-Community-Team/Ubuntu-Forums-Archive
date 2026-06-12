---
title: "blinking underscore while booting"
date: 2011-05-14
forum: General Help
---

### Post by dorado29 on 2011-05-14
My parents just upgraded from their 8+ year old desktop to a newer dell. The old one has XP on it and would barely run, lots of bloatware, viruses, etc.. I tried putting an ubuntu 10.10 disc to boot from it but the old desktop suddenly stopped recognizing mouse and keyboard input so I couldn't change the boot preferences. I took the hard drive out and plugged it into my desktop, copied all the useful files to my hard drive, then wiped it. I then installed ubuntu on the old -and now empty- hard drive by having it plugged into my computer. 

I put the hard drive back in the old desktop and found that the keyboard now works. I can press F2 or F12 and change things around and whatnot. However, when I let it pass the screen that prompts me to press F2 or F12, it goes to a screen with a blinking underscore in the top left of the screen and gets stuck there.

Any ideas on what's causing it to get stuck on this screen?

---

### Post by Hedgehog1 on 2011-05-14
Flashing Cursor, Blank Screen.


Please follow the 'blank screen problems' thread below. 

You will be changing the 'nomodeset' boot parameter.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

You might need to to enter other boot parameters There are 6 of them. You may have to do them one-by-one until you get video.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)  (Common Kernel Options Section)


***The Hedge***

:KS

---

### Post by linuxuser12345 on 2011-05-14
Try using Ubuntu 10.04.2. It is much more stable and reliable, in most cases.
You can also give 11.04 a shot. Just sometimes, the LiveCDs aren't always perfectly compatible. That is why you got to try different versions.

---

### Post by dorado29 on 2011-05-14
EDIT: I'll download 10.04.2 and try that too^^^^

I tried pressing and holding "shift" several times but it didn't trigger the grub menu. 

I just stuck the ubuntu disc in and now i'm trying to boot from it on this old desktop.. now that my keyboard works, i can change the boot settings around. 

however, i can't figure out what will make it boot from a disc. i pressed f2 to enter set-up then went into "boot sequence" and saw that there are things that look like square root signs (or maybe they're check marks?) next to "IDE CDROM Device", "diskette drive" and "hard-disk drive c:". I changed it so the only thing with the check mark/sqr root sign next to it is "IDE CDROM Device. unless i'm completely going in the wrong direction, it should boot from whatever is in the disc tray?

are some old computers unable to boot from discs or should a dell dimension 4550 be okay?

---

### Post by dorado29 on 2011-05-14
I'm 95% sure it's trying to boot from the disc. The drive spools up and starts whirring for a second or two then it lets off. It does that like 5 times then the screen says "strike f1 to retry boot, or f2 for setup utility"

maybe there's an issue with the iso image and the computer being so old?

---

### Post by RedRat on 2011-05-14
Consider that the desktop is 8+ years old. Really, things do wear out and burn out. I have had DVD drives that are only 2 or 3 years old crap out on me. BTW, sometimes controller cards (for the HD and CD/DVD drive go bad. Maybe when you removed the old hard drive you knocked something loose. Check all the cards and make sure they are inserted tightly. 

You just may be pushing it for such an old machine.

---

