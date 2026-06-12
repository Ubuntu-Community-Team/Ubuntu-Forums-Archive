---
title: "I'm trying to get Windows XP..."
date: 2011-02-19
forum: General Help
---

### Post by lynchster93 on 2011-02-19
... back on to my PC, and have successfully downloaded and burned the .iso file to a blank disc. So what happens when I try to start this >>

- I right click the CD-R icon on the desktop, then click the choice that says, "Open With Autorun Prompt". 

- Afterward I get a message at the top that says, "This medium contains software intended to be automatically started. Would you like to run it?" at the bottom it says, "The software will run directly from the medium "GRTMUPD_EN". You should never run software that you don't trust."

- I proceed and push run, then get a message that says, "Error Autorunning Software" at the bottom it says, "Cannot find the Autorun Program".

What can I do in this situation? I do not want to run Windows XP alongside Ubuntu, even though I like the simplicity of it, it just doesn't have what I want. Help please & thank you! :)

---

### Post by PaulReaver on 2011-02-19
to install XP on your computer you will need to select cd/dvd as your boot device on starting the PC

it won't install from inside ubuntu...

---

### Post by lynchster93 on 2011-02-19
> **PaulReaver said:**
> to install XP on your computer you will need to select cd/dvd as your boot device on starting the PC

it won't install from inside ubuntu...

OH, just like I had to when using my flash-drive as a boot disk when installing Ubuntu!? Ok, wow. I'm sorry for the pointless thread, I probably could have thought of that if I actually THOUGHT. I'm 17, can't really expect me to off the bat, thank you!!

---

### Post by PaulReaver on 2011-02-19
not a problem.... Good luck

---

### Post by lynchster93 on 2011-02-19
> **PaulReaver said:**
> not a problem.... Good luck

Ok, disregard my last. I started up the PC, tapped F12 to open the boot menu, clicked on CDR/DVDR drive icon, it began to spool up then stopped. Then got a message across the top of the screen that says.

udevd-work [282]: open /dev/null/ failed: No such file or directory

...and the most recent attempt the [282] was replaced with [271].

So.... whats the thought on this?

---

### Post by PaulReaver on 2011-02-19
> **lynchster93 said:**
> Ok, disregard my last. I started up the PC, tapped F12 to open the boot menu, clicked on CDR/DVDR drive icon, it began to spool up then stopped. Then got a message across the top of the screen that says.

udevd-work [282]: open /dev/null/ failed: No such file or directory

...and the most recent attempt the [282] was replaced with [271].

So.... whats the thought on this?


/dev/null ??? udev???

are you sure you burned a xp disc?  this looks to me that this is a unix or linux disc....

---

### Post by lynchster93 on 2011-02-19
> **PaulReaver said:**
> /dev/null ??? udev???

are you sure you burned a xp disc?  this looks to me that this is a unix or linux disc....

Yeah, I was on the microsoft/windows site when I downloaded the .iso file. I'm not a computer prodigy, but I am aware of what I'm doing most of the time. lol

---

### Post by PaulReaver on 2011-02-19
sorry if i sounded a bit condescending. I didn't mean to come across that way....


its just that "udev" manages the linux kernelspace... so you must be booting into linux somehow.   
?is confused?


If you booted into a windows disc then I'm as stumped as yourself.

sorry

---

### Post by lynchster93 on 2011-02-19
> **PaulReaver said:**
> sorry if i sounded a bit condescending. I didn't mean to come across that way....


its just that "udev" manages the linux kernelspace... so you must be booting into linux somehow.   
?is confused?


If you booted into a windows disc then I'm as stumped as yourself.

sorry

If you know someone who could be of help, could you please refer them to me PLEASE!!! You did your best to help me, and I'm ver appreciative!! Thank you...

---

### Post by mikewhatever on 2011-02-19
> **lynchster93 said:**
> Yeah, I was on the microsoft/windows site when I downloaded the .iso file. I'm not a computer prodigy, but I am aware of what I'm doing most of the time. lol

So you downloaded an .iso of Windows XP from a Microsoft site? Can you post a link.
Regardless, installing Windows is not the specialty of this forum, try a Windows forum for better help.

---

### Post by lynchster93 on 2011-02-19
> **mikewhatever said:**
> So you downloaded an .iso of Windows XP from a Microsoft site? Can you post a link.
Regardless, installing Windows is not the specialty of this forum, try a Windows forum for better help.

Yeah, heres the link to the download. 

[http://www.microsoft.com/downloads/en/details.aspx?FamilyId=2FCDE6CE-B5FB-4488-8C50-FE22559D164E&displaylang=en](http://www.microsoft.com/downloads/en/details.aspx?FamilyId=2FCDE6CE-B5FB-4488-8C50-FE22559D164E&displaylang=en)

---

### Post by cariboo on 2011-02-19
This thread has nothing to do with Ubuntu, if you need help installing old versions of Windows , you may be better off asking your question [here]("http://forums.cnet.com/windows-xp-forum/")

This thread is closed.

---

### Post by gerowen on 2011-02-19
Some pirated copies of Windows implement a heavily modified Linux bootloader at startup to bypass activation.  Where you got your copy of Windows isn't our business, but if it's pirated then this is a possibility, and could explain the weird error you're getting from the startup CD.

---

