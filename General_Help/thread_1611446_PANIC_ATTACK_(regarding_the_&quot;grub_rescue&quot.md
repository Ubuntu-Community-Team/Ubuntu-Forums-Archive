---
title: "*PANIC ATTACK* (regarding the &quot;grub rescue&quot; problem..."
date: 2010-11-01
forum: General Help
---

### Post by therealhehaw on 2010-11-01
Guys, I know this is long, but please bear with me.
This is because there's a popcorn smiley, so, if you want, get the popcorn ready for my epic tale...:popcorn:

Ok, so here's the deal:
I installed Ubuntu 9.10 a while ago, and I just recently updated my video card. Today, I tried installing a patch (I don't know what to call it) that upgrades the system to version 10.04. Though, at the same time, I was also installing the drivers needed for my video card. Now, I don't know if it was the BEST way, but I used terminal to execute the .run file... This part will be pure speculation because I have no idea what the heck happened :S So I think I may have typed something wrong in terminal, and something happened, so I got a screen (a black screen with command prompt on it) and it asks me for my ubuntu 9.10 account and password (which I typed in multiple times, but failed :P) Then, it tells me to give it my 10.04 password (which, I guessed would be the same as my 9.10 password) but I failed again! :O The system tells me to reboot, and when I rebooted, the message:
"error: no such device
grub rescue>_" (the underscore is flashing, just like in a command prompt)

I have already googled (yes, I already searched, so no more lmgtfy.com links) and searched a bunch of threads for my problem. While there are alot of threads SIMILAR to my problem, NONE of them are actually USABLE in any way for me. My desktop is manufactured my Acer, it has the American Megatrends Bios (which, some dude there locked so I can't change my boot priority :() which means that I can't access my LiveCD or my backup disk for vista :(

Now, I know I can do a full system restore, BUT, if I DO, I will lose a CRAAAZZYYY amount of important data (like schoolwork, stuff that I made such as music compositions, and some video game saved data ;D, though it might take a while to get the game files back, I really don't care about them)

So, I am wondering, if there's an environmental way to restore my Vista Booter?

Edit: Ok, my friend managed to get it back :D thanks for your support people!

---

### Post by wilee-nilee on 2010-11-01
If you want to boot a cd use the key-prompt not for the bios, but the choice of boot menu, mine is f12 yours could be different but probably not. 

With a acer-aspire-one I own I had to unlock the f key prompt from bios I believe.

It is unusual to have a vendor lock the bios I would fix that right away if possible, if this is really the case.

---

### Post by therealhehaw on 2010-11-01
Well, I don't know what you mean by vendor lock, but I seem to only have "visitor" powers in my BIO setup.
And I just found out I can't access the boot menu, because the "Username and password does not match"
I think that may still be from my failed driver update.

---

### Post by therealhehaw on 2010-11-02
OK, I think there won't be any way to get back my Vista... So now, can you guys recommend a system recovery program?

---

### Post by jroa on 2010-11-02
Let me get this straight.  You can not access the BIOS settings in order to change the boot order, or you can access the BIOS settings, but you can not change the boot order?

---

### Post by matt_symes on 2010-11-02
Hi

Have you considered trying to clear the BIOS back to the factory defaults by either removing the CMOS battery or checking out you MB jumpers? 
With that you may them be able to change the boot order and boot from a live disk and fix everything. 
If you do that make a note of _all_ you current BIOS settings.

Kind regards.

---

### Post by alphaamanitin on 2010-11-02
SuperGrub should let you boot into your Vista.  Just boot from the CD.  Also, do what was suggested earlier and take the CMOS battery out.  

AlphaA

---

