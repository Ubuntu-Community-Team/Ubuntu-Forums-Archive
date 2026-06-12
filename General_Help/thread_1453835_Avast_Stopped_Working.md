---
title: "Avast Stopped Working"
date: 2010-04-13
forum: General Help
---

### Post by Kid Charlemagne on 2010-04-13
I'm running Ubuntu 8.04 and use avast anti-virus software. I never had a problem with avast until today. While it was updating it became unresponsive, and I received the following error message:"An error occured in avast! engine: Invalid argument." Now it won't open, and I can't seem to even uninstall avast. Any help you could offer in resolving this problem would be greatly appreciated.

---

### Post by tjp264 on 2010-04-13
Go to this thread:
[http://ubuntuforums.org/showthread.php?t=1448803](http://ubuntuforums.org/showthread.php?t=1448803)

---

### Post by Kid Charlemagne on 2010-04-14
I followed the directions to the letter, but I'm still getting the same error message.

---

### Post by 98cwitr on 2010-04-14
why are you running avast?

---

### Post by Kid Charlemagne on 2010-04-15
Any other suggestions?

---

### Post by scottuss on 2010-04-15
> **98cwitr said:**
> why are you running avast?

This

---

### Post by Kid Charlemagne on 2010-04-15
> **Kid Charlemagne said:**
> I'm running Ubuntu 8.04 and use avast anti-virus software. I never had a problem with avast until today. While it was updating it became unresponsive, and I received the following error message:"An error occured in avast! engine: Invalid argument." Now it won't open, and I can't seem to even uninstall avast. Any help you could offer in resolving this problem would be greatly appreciated.

I followed a link to repair, and now when I boot up my computer I receive the following message. "error: "kernel.shmax" is an unknown key". Is there any way to fix this? I can't access anything at all at this point.

---

### Post by Trilby on 2010-05-25
> **Kid Charlemagne said:**
> I'm running Ubuntu 8.04 and use avast anti-virus software. I never had a problem with avast until today. While it was updating it became unresponsive, and I received the following error message:"An error occured in avast! engine: Invalid argument." Now it won't open, and I can't seem to even uninstall avast. Any help you could offer in resolving this problem would be greatly appreciated.

I was using avast on Karmic but since upgrading to Lucid, I have exactly the same issue.

---

### Post by dino99 on 2010-05-25
clamav work fine (8 packages to install, see with synaptic)

---

### Post by 98cwitr on 2010-05-25
again I ask...why are you running AV software in Linux?

---

### Post by David Deu on 2010-05-25
Hey, I was sure there is no need in AV on linux.

---

### Post by 98cwitr on 2010-05-25
> **David Deu said:**
> Hey, I was sure there is no need in AV on linux.

unless you want to scan Windows machines on another partition or via the network...there isn't. Even then, it's completely unnecessary b/c avast is only going to protect a windows machine within it's scope of limitations and functionality...so even then it's pointless to have avast on a linux box.

---

### Post by Nightstrike2009 on 2010-05-25
I also use "ClamTK" (ClamTK is a GUI for ClamAV) I find it easy to use and its also open-source. 

You do have to run "sudo freshclam" in terminal to install new definitions but that aside its great. :-)

PS: Check out: [http://sourceforge.net/]("http://sourceforge.net/") for the latest ClamTK GUI (.deb file) if thats what you want to use (the ones in the repos seem to be a version out of date).

UPDATE 30-05-2010 - Trilby is right > You mean "sudo freshclam" I did mean "sudo freshclam" sorry about that. (I originally posted "sudo-freshclam" which doesn't work) thanks for spotting that Trilby I must have been having an off day LOL ;-)

---

### Post by Trilby on 2010-05-26
> **98cwitr said:**
> again I ask...why are you running AV software in Linux?
I dual boot. Amongst other things, it's useful to be able to scan my windows partition without rebooting.

---

### Post by Trilby on 2010-05-26
> **Nightstrike2009 said:**
> You do have to run "sudo-freshclam" in terminal to install new definitions but that aside its great

You mean "sudo freshclam"
"sudo-freshclam" doesn't do anything

---

### Post by wilee-nilee on 2010-05-26
```
Sudo sysctl -w kernel.shmmax=100000000
```

will get it going I got this from the avast forums I don't have the link so if you want confirmation you will have to find it. This is a session by session fix.

---

### Post by Trilby on 2010-05-26
> **wilee-nilee said:**
> ```
Sudo sysctl -w kernel.shmmax=100000000
```

will get it going I got this from the avast forums I don't have the link so if you want confirmation you will have to find it. This is a session by session fix.

What will this do to the kernel?

---

### Post by wilee-nilee on 2010-05-26
> **Trilby said:**
> What will this do to the kernel?
As I remewber it doesn't change the kernel it just makes it so avast will work as I said go to the avast forum and look at what they say. I don't use avast always but when I have, this command has never caused a problem.

Really you don't need avast but it is not a bad av for Linux but trying to figure what it means if it gets a hit is the hard part, it is more likely to mess your system up deleting a false positive then the command will.

---

