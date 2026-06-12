---
title: "Used KoalaTerm on Win, what do I do on Ubuntu?"
date: 2010-03-29
forum: General Help
---

### Post by Xendric on 2010-03-29
Hi there

I used to have Win Vista on my work laptop and used KoalaTerm to connect to my work's server that is running Linux.

Now I've switched over to Ubuntu and I've trouble running the office's application.

I've managed to connect to the server via telnet, remote desktop, pretty much everything, but after logging in and trying to run the application, i get an error message like this:

**FRM-40918: Internal error: unable to initialize Toolkit**

The support guys told me it's probably an emulation issue (Koalaterm is using VT220) but I tried using the setenv command but I'm getting the same error when I try to load the app again.

I really am at a loss here because I'm only using this OS for 2 days so I can't think of anything right now.

If you have any ideas, I'd really appreciate it because I'm enjoying Ubuntu too much to go back to windows :(

---

### Post by Brandon Williams on 2010-03-29
It's hard to help without knowing more details about the app that you're trying to run. If it really is the emulation issue and simply setting TERM=vt220 in your environment before establishing the connection doesn't help, then you might want to try using putty as your client software (sudo apt-get install putty). I don't know whether it will solve your problem, but putty does have functionality that is similar to koala term.

---

### Post by Xendric on 2010-03-30
It's a custom ERP app for a super market firm, so I can't really give more details to help you identify the problem. It's written for linux so I was expecting it to work without any modifications or emulations.

The TERM command didn't work unfortunately.

I'm gonna try Putty now, see how it pans out, thanks :)

---

### Post by Xendric on 2010-03-30
No dice, same thing happens with Putty.
TBH I didnt notice a difference whether i was using the console or putty.

---

### Post by Brandon Williams on 2010-03-30
Did you try changing any of the putty settings to get it to run in vt220 mode?

You might also want to consider trying to run koala term under wine, at least until you get the problem figured out. I don't know whether it will work, but it's worth a try. There is information about setup and use [here](https://help.ubuntu.com/community/Wine).

---

### Post by Xendric on 2010-03-31
Ok, it loaded with Wine, and it works great, up to the point where I need to switch to Greek.

I can type English fine, but when I switch to Greek, all i get is an ? for every character i type in greek.

Any ideas?

PS: On Win, I was using a .fon greek font, that i tried to convert to TTF with Fontforge, but FF crashes the moment I try to generate the font. It crashes every time i try to convert a font, no matter what type I'm trying to export. Tried removing and reinstalling FF, but no good.  

Here is the msg I get from FF

"*** stack smashing detected ***: fontforge terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0x206bed8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0x206be90]
/usr/lib/libgunicode.so.3[0x7a77c4]
/usr/lib/libgunicode.so.3[0x7a6304]
[0x36312c33]
======= Memory map: ========
00110000-002ff000 r-xp 00000000 08:05 305        /usr/lib/libpython2.6.so.1.0
.
.
.
.
.
00be2000-00be3000 r--p 00022000 08:05 2830       /usr/lib/libpng12.so.0.37.0
00be3000-00be4000 rw-p 00023000 08:05 2830       /usr/lib/libpng12.so.0.37.0
00be4000-00bf8000 r-xp 00000000 08:05 676        /lib/libz.so.1.2.3.3
00bf8000-00bf9000 r--p 00013000 08:05 676        /lib/libz.so.1.2.3.3
00bf9000-00bfa000 rw-p 00014000 08:05 676        /lib/libz.so.1.2.3.3Aborted"

---

### Post by Brandon Williams on 2010-03-31
You may want to ask the font question in a separate thread so that people more knowledgeable about running wine apps will notice it. You do have a fully functional Greek language installation for the rest of your linux environment, right?

As for the other problem, if you just continue running koalaterm in English, does the application run correctly? If so, then we should be able to figure out what is different about the remote session when you log in using koalaterm vs. standard ssh.

---

### Post by Xendric on 2010-04-01
Yes Greek works perfectly fine for everything else on my Linux installation.

As it is now, I haven't had any long sessions on the work application under Linux, because I have to use Greek very often, so it's not functional. But for the little I've tried it, it seems to work perfect in English, all the functions are there. 
So, to answer your question, yes, I believe it works fine in english and the only problem i have now is when i switch to greek.

---

### Post by Brandon Williams on 2010-04-01
Hmmm ... I wonder what's different between koalaterm and a standard ssh session. The next step will be to check for differences in the remote session when you log in using the two different methods. Use printenv to look compare the environment and 'stty -a' to check the terminal settings.

Also, regarding the display of Greek fonts in koalaterm, are you able to get any other remote apps to display Greek characters correctly in koalaterm. I'm curious whether it's a problem with the specific app or all apps. It's probably the later, but it's worth checking.

---

### Post by Xendric on 2010-04-02
It would be nice to try, but we don't have any other remote apps, just this one.

But let's suppose it's like that in all apps, what would you have me looking for in that case?

---

### Post by Brandon Williams on 2010-04-03
As a first step, run printenv and 'stty -a' when logged in using koalaterm and then again when logged in via a linux native method, like ssh in a terminal. Are there any differences in either the environment or the terminal settings?

---

