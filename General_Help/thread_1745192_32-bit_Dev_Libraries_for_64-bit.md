---
title: "32-bit Dev Libraries for 64-bit"
date: 2011-04-30
forum: General Help
---

### Post by -tr on 2011-04-30
Hi there. Think I finally found the root of all the problems I've been having in 11.04. While trying to run one 32-bit program, and trying to install another, I get 'Cannot build a 32-bit program, you need to install 32-bit development libraries.'. I already have ia32 shared libraries installed, so what other libraries do I need, and where might I install them?

Thanks for any help.

---

### Post by 3Miro on 2011-04-30
You probably need the multilib libraries for gcc.

---

### Post by -tr on 2011-04-30
Well that seemingly got me a little farther, and yet still stuck.. =s

---

### Post by 3Miro on 2011-04-30
Copy and paste the exact error message.

---

### Post by -tr on 2011-04-30
This is what I get when trying to run the program: [http://pastebin.com/jME3W2Gy](http://pastebin.com/jME3W2Gy). 

And when trying to install it returned like 3 new packages that needed to be installed after installing multilibs, then just said config failed and aborted after installing the last.

---

### Post by 3Miro on 2011-04-30
I am missing something here. Are you trying to run World of Warcraft under wine or are you compiling a 32-bit application. For wine related problems, your best bet is the winehq forum:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

If you are trying to compile a 32-bit program, then post the info form that.

---

### Post by -tr on 2011-04-30
> **3Miro said:**
> I am missing something here. Are you trying to run World of Warcraft under wine or are you compiling a 32-bit application. For wine related problems, your best bet is the winehq forum:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

If you are trying to compile a 32-bit program, then post the info form that.

I'm trying to do both, and I have already tried there. I'm under the conclusion that the solution is the same for both. 

The info from the 32-bit application I posted, the only thing it said was that the configuration failed and installation was aborted.

---

### Post by 3Miro on 2011-05-01
The WoW error suggests a sound issue to me, but I cannot be sure since I don't know much about WoW and wine. You can check the wine forum, the people there really know wine.

You can check to see if you have the 32-bit libraries for ALSA and Pulseaudio installed and this could resolve the problem. However I doubt the wine and compilation issue are the same (it is possible, I just don't think so).

Could you post the error from the compilation. (also make sure you have multilib installed for both gcc and g++).

---

