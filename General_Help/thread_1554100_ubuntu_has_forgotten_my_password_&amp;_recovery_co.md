---
title: "ubuntu has forgotten my password &amp; recovery console is dead"
date: 2010-08-16
forum: General Help
---

### Post by crshbndct on 2010-08-16
yes thats right. last night i changed my logon password for better security. (have a feeling my flatmate knows it)

when i tried to log in today, it wouldnt accept my password. no i know that i got it correct. i know this for a fact.
so after a few tries, i decided stuff this, i am going to reset it using recovery console.

but the recovery console just hangs with the following on the screen:

> [    4.1098198] Console: switching to colour frame buffer device 100x30

i can ctrl+alt f2, and i just get a flashing cursor. 

so thats it then. my ubuntu box is hosed and i am about twenty minutes away from formatting and starting again. 6 months of schoolwork, designs for architectural competitions etc all gone.

so i need a solution to this probably very simple thing really soon.

---

### Post by gradinaruvasile on 2010-08-16
Dont be so dramatic. You can save your stuff with a live cd/USB in the worst case.
BTW, the recovery console doesnt ask for the password (i use Debian now and it asks for my pass to enter single user mode and in older Ubuntus did too)? That is a huge open front door for anyone if you dont have a password protected grub at least...

---

### Post by crshbndct on 2010-08-16
okay
i know that the recovery console allows me to boot to root access with no password
that is what i want to do
but i have this stupid framebuffer message on the screen. which means i cant use the computer at all.
i dont happen to have a live cd handy, and i am on 56k for the next 3 weeks, so downloading a new one is not practical. not to mention the fact that i need to use it tomorrow for university assignments.

so can anyone tell me how to get past that frame buffer message thing? i am pretty sure i can just edit one or other of the grub commands to get it to give me a recovery console.

also, what on earth would possess an operatin system made in 2010 to actually forget a password?
i know that i havent forgotten it. i have been using and changing passwords on ubuntu for 3 years now and i know what i am doing

---

### Post by crshbndct on 2010-08-16
i might just mention this again for those who dont read the whole thread.
I NEED TO USE THE RECOVERY CONSOLE TO CHANGE MY PASSWORD AS UBUNTU HAS COMPLETELY FORGOTTEN IT. BUT THE RECOVERY CONSOLE IS NOT WORKING EITHER I NEED THIS WORKING BY TONIGHT AND I AM ON 56K.

sorry if thats offensive, but for gods sake, i am only looking for replies which actually tell me how to fix the problem. not replies which say "thats a bad idea" or "i use debian" or whatever. UBUNTU FORGOT MY PASSWORD and this has left me totally f***ed. it happened once before on this install and the recovery console sorted it out for me.

i am using 10.04, 2 week old install, all updates applied, this is the second time in two weeks that this has happened, only this time the recovery console just hangs at that message. 

ctrl -alt -del still makes it do its reset thing

---

### Post by kaivalagi on 2010-08-16
Did you create a second home partition for all your data? If so reformat and start again WITHOUT losing your data.

Trouble is whether you re-install or use recovery with only a 56K connection and no install disk it's going to be painful to get where you need to be...you could try a mini iso image (< 10MB) but I am not sure on the tools being available with that...([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

---

### Post by marshmallow1304 on 2010-08-16
1) Relax.
2) Grab yourself a copy of [Damn Small Linux]("http://www.damnsmalllinux.org/").  It's only 50 MB, so it'll be a little less painful to download over dialup.
3) Burn it to a CD and boot it up.
4) Open up a terminal.

```
sudo su
mkdir -p /media/ubuntu
mount /dev/sda1 /media/ubuntu
chroot /media/ubuntu /bin/bash
passwd user
exit
umount /media/ubuntu
reboot
```

Replace user with your username and /dev/sda1 with the partition on which Ubuntu is installed (use fdisk -l (that's a lowercase L) to list all partitions).

---

### Post by crshbndct on 2010-08-16
i dont know how to say this:
]MY ONLY PROBLEM IS THAT I CANT USE THE RECOVERY CONSOLE. I AM LOOKING FOR A SOLUTION TO THIS ISSUE..
A reinstall is not an option. at all.
what do i need to edit in the grub commands so that it will load the recovery console.
that is all i need to know.
please answer the question i am asking not the question i am not asking

---

### Post by crshbndct on 2010-08-16
thank you

thanks a lot. i will do this. 
this is the answer i was looking for.. take note to all the people who started suggesting reinstalls and ****

---

### Post by marshmallow1304 on 2010-08-16
nvm

---

### Post by prshah on 2010-08-16
> **crshbndct said:**
> 
but the recovery console just hangs with the following on the screen:
[    4.1098198] Console: switching to colour frame buffer device 100x30

When you reach the grub menu, select Recovery Console, but don't press enter; press "e" to edit the line instead. Scroll to the line that begins with the text "kernel..", and press "e" again to edit the line.

At the end of the line, remove "--" if present, and add " vga=771" (note the space).

Press "enter" to accept the changes, then press "b" to boot with the changes.

You should have a good recovery menu now. If you still have the same problem, change "vga=771" to "vga=ask" and try again. Now you will be asked for a suitable vga mode: choose an 80x25, non-fb option.

I assume you can proceed properly once the recovery menu is presented.

Please post back if none of these work for you, or if you need some help about recovery mode.

The changes to grub are temporary, and will be discarded once you boot.

---

### Post by libssd on 2010-08-16
Now that you are (presumably) back in business, it's time to have disaster recovery tools in place, including a restorable ISO for your core system, and separate storage for your data files, plus the discipline to do backups at regular intervals -- 6 months is inexcusable. 
[IMG]http://rlv.zcache.com/your_failure_to_plan_mug-p1684359071317663552opcc_400.jpg[/IMG]
Despite your many disclaimers, I strongly suspect that for your password, "problem exists between chair and keyboard."

---

### Post by libssd on 2010-08-16
> BTW, the recovery console doesnt ask for the password (i use Debian now and it asks for my pass to enter single user mode and in older Ubuntus did too)? That is a huge open front door for anyone if you dont have a password protected grub at least...
The BIOS on my computer supports password control, and I set my password there. Of course, I can still use Ubuntu password to lock the screen, but BIOS password protection works regardless of OS. Of course, I'm really screwed if I forget it, but I have a BIOS restore USB (and instructions printed on paper) for that contingency. Not yet tested though -- reflashing the BIOS is not something I like to do casually.

---

### Post by mastablasta on 2010-08-16
unless someone takes the hard drive out and plugs it into another motherboard (BIOS) that has no password.
 
 
to really protect the files, you need disk encryption (or at least for very important files the encrypted folder).

---

### Post by LightningCrash on 2010-08-16
[quote=crshbndct]thank you

thanks a lot. i will do this.
this is the answer i was looking for.. take note to all the people who started suggesting reinstalls and ****[/quote]

Take note... in the future you will receive better help if you drop the attitude.

---

### Post by SoFl W on 2010-08-16
> he BIOS on my computer supports password control, and I set my password  there. Of course, I can still use Ubuntu password to lock the screen,  but BIOS password protection works regardless of OS. Of course, I'm  really screwed if I forget it, but I have a BIOS restore USB (and  instructions printed on paper) for that contingency. Not yet tested  though

Wont reseting the BIOS (taking out the battery) reset the BIOS password?  

Like your coffee mug.

---

### Post by smellyman on 2010-08-16
> **crshbndct said:**
> yes thats right. last night i changed my logon password for better security. (have a feeling my flatmate knows it)

when i tried to log in today, it wouldnt accept my password. no i know that i got it correct. i know this for a fact.


[IMG]http://2.bp.blogspot.com/_B0WrNzDXvyg/TDXwykUEv-I/AAAAAAAAAyA/LQ4_LMO5FbY/s400/paris_giggle.jpg[/IMG]

---

### Post by cdenley on 2010-08-16
> 
Take note... in the future you will receive better help if you drop the attitude.

And the annoying fonts. I tend to ignore people who shout at me when asking for my help.

---

### Post by kaivalagi on 2010-08-16
Is this paid for support? enough said really....

---

### Post by ronnielsen1 on 2010-08-16
> And the annoying fonts. I tend to ignore people who shout at me when asking for my help.

[CENTER]:lolflag:
[/CENTER]

---

### Post by mikewhatever on 2010-08-16
smellyman, :D:D:D

---

### Post by LowSky on 2010-08-16
How would you lose 6 months of school work if you only installed Ubuntu 10.04, 2 weeks ago? 

I like when I notice conflicting information

---

### Post by CharlesA on 2010-08-16
Having a liveCD handy is always a good idea. Even DSL would have worked.

It kind of makes me wonder how exactly they changed their password, as there isn't much information about that..

---

### Post by dFlyer on 2010-08-16
I need to say that Ubuntu didn't forget anything. It can't forget. You either forgot (only you can forget) or you type it in wrong. Another option is to check your hard drive for bad sectors. Please stop shouting if you want help.

---

### Post by Thomas Garman on 2010-08-16
These forums do give everyone a very clear picture of the psychology of learning Linux...
 
Anger
Frustration
Helplessness
More anger
relief
reinstall
reboot
denial
repeat ad infinitum
 
I myself have crashed and burned on the forums a few times somebody should do a psychological study not only of the type of person who is likely try Linux but also the psychological steps of getting immersed in the culture.

---

### Post by Smart Viking on 2010-08-16
Is the forum bug? Does it say that noone have made a thread or post in 8 hours? It does it with me, and i am apparantly the only user too, i'm interrested in if this is just for me or for everybody else, if you have no idea what i'm talking about then it is probably just for me. :)

---

### Post by SoFl W on 2010-08-16
Forums are messed up a bit.

---

### Post by Darkness Des on 2010-08-16
You aren't the only one. Mine says that too.

---

### Post by tubunu on 2010-08-16
To the OP. Grab Ubuntu live CD (the one you installed your copy of Ubuntu from), boot it, mount your drives and there you will see all your files.

---

### Post by cariboo on 2010-08-16
The forum was suffering from a database problem, that is now repaired. 

Please keep this thread on topic. The replies have been bad enough that this thread should be closed, but I'll leave it open just in case the op comes back.

---

### Post by libssd on 2010-08-17
> **dFlyer said:**
> I need to say that Ubuntu didn't forget anything. It can't forget. You either forgot (only you can forget) or you type it in wrong. Another option is to check your hard drive for bad sectors. Please stop shouting if you want help.
About twice a year my father-in-law calls and says "My password doesn't work." I reply, "Check the caps lock key." Always works.

---

### Post by morkar on 2011-06-23
> **prshah said:**
> When you reach the grub menu, select Recovery Console, but don't press enter; press "e" to edit the line instead. Scroll to the line that begins with the text "kernel..", and press "e" again to edit the line.
 
At the end of the line, remove "--" if present, and add " vga=771" (note the space).
 
Press "enter" to accept the changes, then press "b" to boot with the changes.
 
You should have a good recovery menu now. If you still have the same problem, change "vga=771" to "vga=ask" and try again. Now you will be asked for a suitable vga mode: choose an 80x25, non-fb option.
 
I assume you can proceed properly once the recovery menu is presented.
 
Please post back if none of these work for you, or if you need some help about recovery mode.
 
The changes to grub are temporary, and will be discarded once you boot.
 
Hi!
  I'm having the same problem. I'vr tried this solution, but, when I press 'e' after selecting the Recovery Mode, I don't have any "kernel" line. Can someone helps me. The OS is Ubuntu netbook edition. Thank you very much

---

