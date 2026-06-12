---
title: "(ish) HD Failure - &quot;MANY BAD SECTORS&quot; and &quot;Missing data blocks&quot; NO BOOT!"
date: 2010-02-10
forum: General Help
---

### Post by MugOTea on 2010-02-10
**This is more of a Ubuntu support story with hopefully useful information for anyone who's screens gone blank and Ubuntu won't boot.**

I'm a techie by proffession but work is all Win2k server, and XP, where my expertise lies. Ubuntu is my home favourite and installed on my server, desktops (only one Microsoft PC left Hehe), and my laptop. **So I cannot provide a proper Ubuntu support** answer to this but hopefully someone will comment and shed light or better instructions. I only post this because I am back online after a complete disaster last night and I found no definitive answer / fix to the errors I did receive (after a lot of black screens).

It was/is my HP (Compaq 6720s) running Ubuntu 9.10 with all automatic updates switched on and allowed to proceed. Actual version unknown... I had been using it heavily all day working (playing some classic games) and finally relented and passed it over to my bro to browse youtube. He watched one video and tried for the next and it died! I've never seen anything like it before either; it just faded out as if the screen saver was coming on or the batter was flat, even though it was plugged in. I swear it should have sighed audibly and made my life! Anyways, after that it wouldn't boot, showed me a startup screen with the Kubuntu logo then a blank screen and did nothing. Something bad?

Well, I thought memory burnt up so I used GRUB (hit escape at boot time when prompted by GRUB) and went to the bottom of the list for Memcheck. This found no problems and worked fine on the battery power. I even got a light back when I plugged the charger in again. So I figure the memory, battery and charger are all o.k.

I tried a few of the other boot options with GRUB but none worked, but without the logo I did find a way to a terminal prompt. This highlighted a couple of things;

 - Firstly, it was before any login procedure and WAS on the one and only hard drive in the laptop.

 - There were some errors before I got the prompt: "mount exited with exit code XXX - mount failed!"

 - It wasn't 'my' file-system, it was a very basic unix / linux prompt with limited commands available. I wish I could remember all the folders but it was late at night. The obvious 'etc', 'var', 'usr' (which contained nothing), and a few others.

So at this point it dawned on me (somewhat slowly) that the system would work fine if I booted on the LIVE CD again and choose the 'Try Ubuntu' option.

When the GUI booted up I could see my HD in the 'Places' menu but couldn't mount it. I got the error that it was the wrong file system. I could get online so I searched and found loads of horror stories telling me to send the disk to a data recovery expert etc. 

The error was something like:
```
UNABLE TO MOUNT DATA: Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
``` 

See: [http://ubuntuforums.org/showthread.php?p=8416468](http://ubuntuforums.org/showthread.php?p=8416468)

It's recommended on there that they run fsck but it ends with an error. Mine didn't, instead it detected several problems with the file system and asked to overwrite, I said yes, and a little later on it asked if I wanted to continue despite losing some data (I gave up) I said yes again, and left it to it. A few minutes later it pinged up with checking directory structure (a small smile grew), then examining files!?! (happy dance)...

Unfortunately, for tired eyes and my nerves, this isn't quite the end of this story. I could now mount and browse my recovered file system (still on the live CD), and I checked that the files I wanted back the most were there... all good! But then Ubuntu piped up with an error message "ONE OR MORE HARD DISK MAY BE FAILING", "Many Bad Sectors Detected".

I've looked for some sort of software to mark bad sectors and allow me to use the rest of the drive, or even tell me the extent of the bad sectors but not found anything that makes sense to me. However, I did find quite a few posts about the failing hard disk message, all blaming a BUG: [http://ubuntuforums.org/showthread.php?t=1299556](http://ubuntuforums.org/showthread.php?t=1299556)

Rebooted though and everything seems fine, the disk utility now passes all tests and reports that the disk is "HEALTHY"???

I really don't know to be sure, so I'm on borrowed time and typing this while backing up to various online providers.

I would love to know how far off the official Ubuntu recovery track I trailed and if there'd have been an easier way to diagnose / fix the problem. Or even any more information on the original fault if anyone has had a similar thing happen. It'd be good if Ubuntu did give out a final *sigh* before dying out properly like that lol.

---

### Post by MugOTea on 2010-02-10
Oh yeah, I forgot to put what I actually typed to fix the HD:
**sudo fsck /dev/sda1**

Where **sda1** is the location of my hard disk under linux.

---

