---
title: "A Newb In Need"
date: 2006-04-26
forum: General Help
---

### Post by Trance on 2006-04-26
No, I'm not a n00b who can't type for crap, I'm a newb who is trying to get the LiveCD to work. Let me explain my dilemma:

Well, I downloaded the LiveCD version of it and burnt it to a disc. I know how to do that simply. Problem is, when I rebooted with the disc inside, nothing came up in the BIOS or anything to actually use it. Window just loaded up normally and opened up in the Windows OS.

I'm sure it was something done wrong on my part, but I'm not completely knowledgable about the whole thing, so I need some direction. Do any of you know what's going on?

---

### Post by guru369 on 2006-04-26
You need to verify that the first boot device is your cdrom.
The setting exist in your bios.

Enter your bios and check the boot priority section.

---

### Post by Nano Geek on 2006-04-26
Did you burn it as an iso image?

---

### Post by steve.horsley on 2006-04-26
A popular misake is to burn the iso file to disk as a data file. If you open the CD in windows and see the .iso file there, it has been put on as a data file. It should be burned as an **image** file. If you do this right, then when you open the CD in windows, you will see several files and folders on the CD.

Once the CD is burned correctly, you just have to make sure the PC boots the CD, by setting the BIOS to try and boot the CD before the hard disk, and then rebooting the PC. 

Make sure you hve backed up our data first, just in case.

---

### Post by Trance on 2006-04-26
[QUOTE=guru369]You need to verify that the first boot device is your cdrom.
The setting exist in your bios.

Enter your bios and check the boot priority section.[/QUOTE]

How, exactly do you get to the bios? Are you talking about during start-up?:-|

---

### Post by IYY on 2006-04-26
Yeah, during startup. There is always a key you can press when the computer starts up to get to the BIOS. Nowdays that key is often 'Delete', but it can also be one of the function keys.

---

### Post by oyvindaa on 2006-04-26
Normally you push F2 or F8 or whatever during boot-up and you'll get into the BIOS. It might say what button you need to push.

---

### Post by Trance on 2006-04-26
Yeah, I got it figured out. I got into BIOS and told it to boot from CD-ROM. Well, after that, it did. But this is what happened:

Boot from CD-ROM: 

Boot from CD-ROM:

And it'd be blank after the both of them. After, it asked me what OS to boot from, and it never mentioned anything about Ubuntu. I'm quite sure it's not a data disc, either because I didn't find the .iso file you told me of.

---

### Post by sinkxdie on 2006-04-26
You were probably supposed to press a key during the time one of those Boot from Cd-Rom messages came up.

---

### Post by Trance on 2006-04-26
Yes, but what key, do you think it would want me to press? =P

---

