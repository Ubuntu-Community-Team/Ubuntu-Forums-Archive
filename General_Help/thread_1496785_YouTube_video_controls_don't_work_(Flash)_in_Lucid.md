---
title: "YouTube video controls don't work (Flash) in Lucid"
date: 2010-05-29
forum: General Help
---

### Post by Cavsfan on 2010-05-29
I have been using Lucid 64 bit since beta and no problems whatsoever, except playing YouTube videos.
I can only change the HD option (e.g. change from 360 to 720 etc.), but none of the other controls do anything.
I cannot change the volume, stop or pause the video, make it go full screen or any of that.
Everything else works with no problems.

I have the latest version of Java installed via the instructions in my sig.
This was happening also in 9.04 and 9.10 and everything else worked flawlessly.

Everything I have tried doing in Lucid works perfectly, except this one thing - no ability to control flash videos.

Anyone that might have a clue as to why this is I would appreciate hearing from you.  ](*,)
Thanks!

---

### Post by Spr0k3t on 2010-05-29
A quick search came back with this:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

WORKAROUND 1: Disable compiz
WORKAROUND 2: Remove flashplugin-nonfree / flashplugin-installer and install from adobe
WORKAROUND 3: Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

---

### Post by Cavsfan on 2010-05-30
> **Spr0k3t said:**
> A quick search came back with this:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

WORKAROUND 1: Disable compiz
WORKAROUND 2: Remove flashplugin-nonfree / flashplugin-installer and install from adobe
WORKAROUND 3: Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

Thank you very much for this! :)   I will look into it.

I really appreciate the reply! I was beginning to think it was just me!

---

### Post by Cavsfan on 2010-05-31
> **Spr0k3t said:**
> A quick search came back with this:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

WORKAROUND 1: Disable compiz
WORKAROUND 2: Remove flashplugin-nonfree / flashplugin-installer and install from adobe
WORKAROUND 3: Open a terminal and enter:

gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text

I did the workaround 3 and now everything looks great in YouTube!!!! I edited the npviewer file last night 
and did not check to see if it fixed anything, but this morning after a re-boot, it works great!!! I am one happy camper! :)
Close captioning works, full screen works, pause and play works and this is just like it should be - flawless! 
Now, I have absolutely no (not a single) complaint about Lucid Lynx 10.04 64 bit! It is by far better than windows 7 64 bit!
Thanks !

---

### Post by Cavsfan on 2010-05-31
I am going to go ahead an resolve this thread as my problem is fixed!
Just Workaround 3 was all I did and youtube flash works great now!

---

### Post by mal205 on 2010-06-08
Workaround 3 fixed this up for me. Thanks!   :guitar:

---

### Post by Neezer on 2010-06-08
I look forward to giving this a shot after work today. Thanks for the great work everyone!

It was a minor inconvenience that might go away. I'm very excited about it. I'll post back to let you know if it works for me.

---

### Post by Neezer on 2010-06-08
#3 worked great for me!!!

thanks for the answer spr0k3t!

---

### Post by itsjpg on 2010-09-11
Had same problem, 
Workaround #3 worked.

Thanks :)

---

