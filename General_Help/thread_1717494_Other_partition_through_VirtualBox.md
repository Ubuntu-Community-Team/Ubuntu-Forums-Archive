---
title: "Other partition through VirtualBox?"
date: 2011-03-29
forum: General Help
---

### Post by higashi on 2011-03-29
I'm dual booting ubuntu with Windows7 and i'm trying to boot into my Windows7 partition through virtualbox (so that i dont have to restart and boot into it).
I tried following the instructions in t[his thread]("http://ubuntuforums.org/showthread.php?t=769883"), but i couldn't understand them. I kept getting error messages that i didnt know how to fix. Can someone give me some easy to follow instructions on how to do this please?
thanks in advance.

---

### Post by Mark Phelps on 2011-03-30
Just a word of caution ...

Don't do this myself, but have read other threads where folks have tried similar stuff -- and it causes Win7 to become deactivated!  Because it's a different image running in a virtual environment, Win7 thinks it's a different version.

So, while you MAY be able to get this to work, just realize that you could be risking deactivating your Win7 instance in doing this.

---

### Post by supershin on 2011-03-30
May I ask why you're trying to boot into Win7 from virtualbox? I'm just wondering why you'd want to do something like that since it seems to defeat the purpose of virtualisation.

If you need access to files there you can mount the partition in ubuntu and then enable shared folder in virtualbox to access the files on your Win7 partition.

---

### Post by higashi on 2011-03-31
The only reason I kept win7 on my laptop in the first place was because completely changing operating systems would void my warranty.

I want to run it through virtualbox because sometimes I feel like playing a game or something that wine doesn't run very well, but it's never worth actually going into my windows partition.

---

### Post by supershin on 2011-04-09
Then you should image the windows partition and install that image in virtualbox. This way you will have your original windows partition and using virtualbox you can run its image and do whatever you want with it.

---

### Post by SeijiSensei on 2011-04-09
> **higashi said:**
> I want to run it through virtualbox because sometimes I feel like playing a game or something that wine doesn't run very well, but it's never worth actually going into my windows partition.

If all you want to do is play the occasional Windows game, just dual-boot.  If you really want to use VirtualBox, you'll need to create a new virtual machine and install Windows into it using the original CD/DVD you got with your computer.  You may still encounter licensing issues though.  For your needs, it's not worth the hassle.

VirtualBox doesn't provide a "window" into the other operating system already existing in another partition.  It's like you have a whole other PC running inside your Ubuntu OS.  Just like you'd have to install Windows from a disc onto a new PC, you have to install it into a VirtualBox VM the same way.

---

