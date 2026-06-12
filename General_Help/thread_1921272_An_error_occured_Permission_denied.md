---
title: "An error occured: Permission denied"
date: 2012-02-06
forum: General Help
---

### Post by pzykotik on 2012-02-06
When I try to instal Ubuntu 10.10 from the CD directly from my windows XP OS, I get this error:

[U][B]An error occured:

Permission denied

Fore more info, check the file...................... .log[/B][/U]

So, I check the file, but don't quite know what to look at, so here it is:

*[http://pastebin.com/zVW2JFCS](http://pastebin.com/zVW2JFCS)*

Also, if I try to boot directly from the CD I get this error:

_**(process:316): GLib-WARNING**: getpwuid_r(): failed due to unknown user id (0)**_

---

### Post by philinux on 2012-02-06
> **pzykotik said:**
> When I try to instal Ubuntu 10.10 from the CD directly from my windows XP OS, I get this error:

[U][B]An error occured:

Permission denied

Fore more info, check the file...................... .log[/B][/U]

So, I check the file, but don't quite know what to look at, so here it is:

*[http://pastebin.com/zVW2JFCS](http://pastebin.com/zVW2JFCS)*

Also, if I try to boot directly from the CD I get this error:

_**(process:316): GLib-WARNING**: getpwuid_r(): failed due to unknown user id (0)**_

Does the livecd boot ok. If so I would try out ubuntu using that. Wubi was created as another way to explore ubuntu. If your machine can boot from usb a live usb stick install would be a better alternative to try out ubuntu.

---

### Post by pzykotik on 2012-02-06
> **philinux said:**
> Does the livecd boot ok. If so I would try out ubuntu using that. Wubi was created as another way to explore ubuntu. If your machine can boot from usb a live usb stick install would be a better alternative to try out ubuntu.


I just can't boot from anywhere, but I will try a USB stick. I'll write again after I tried.

---

### Post by pzykotik on 2012-02-06
> **pzykotik said:**
> I just can't boot from anywhere, but I will try a USB stick. I'll write again after I tried.

I tried using the usb creator from the CD, I got this error:

[U][B]An uncaught exception was raised:
[Errno 13] Permission denied

[/B][/U]I'd like to point out that I'm using XP, so there's no need to "run as admin".

What are my options?

---

### Post by Rafterman414 on 2012-02-06
If you are trying to install using wubi then try to download the Ubuntu iso and place it in the same directory as the wubi.exe installer. I read some other post where there was a user having a permission denied error and it was fixed by downloading the wubi installer and the ubuntu iso then placing them both in the same directory.

Here is a link to the post I was referring to: [URL="http://ubuntuforums.org/showthread.php?t=1144599"]http://ubuntuforums.org/showthread.php?t=1144599
[/URL] 
If you are trying to create a live usb stick try using unetbootin. Ive used it for several linux distros including ubuntu and it has worked great every time!

---

### Post by pzykotik on 2012-02-06
> **Rafterman414 said:**
> If you are trying to install using wubi then try to download the Ubuntu iso and place it in the same directory as the wubi.exe installer. I read some other post where there was a user having a permission denied error and it was fixed by downloading the wubi installer and the ubuntu iso then placing them both in the same directory.

Here is a link to the post I was referring to: [URL="http://ubuntuforums.org/showthread.php?t=1144599"]http://ubuntuforums.org/showthread.php?t=1144599
[/URL] 
If you are trying to create a live usb stick try using unetbootin. Ive used it for several linux distros including ubuntu and it has worked great every time!

I will first try downloading the ISO, but this is 11.10, my CD is 10.10. If it doesn't work, I will try unetbootin, which I don't know how to use, but Google is my friend I guess.

EDIT: downloaded, installed. I got the reboot invite. Will reboot, and report if it's a success.

---

### Post by pzykotik on 2012-02-06
Once booted up, this screen appears.

[IMG]http://i43.tinypic.com/14j0mzk.jpg[/IMG]

Yeah. The square is the cursor.

---

### Post by pzykotik on 2012-02-06
> **pzykotik said:**
> Once booted up, this screen appears.



Yeah. The square is the cursor.

That was with the downloaded ISO and wubi. I will now try unetbootin... feedback in a few.

---

### Post by pzykotik on 2012-02-06
> **pzykotik said:**
> That was with the downloaded ISO and wubi. I will now try unetbootin... feedback in a few.

That didn't work either. I'll try downloading another version ISO, and wubi, again.

---

### Post by bcbc on 2012-02-06
That looks like a graphics card issue (nvidia or radeon). Try booting with nomodeset: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by pzykotik on 2012-02-06
I've installed with the 10.10 ISO (the one that gaves the graphic problem was 11.10) and it works fine. Only problem I have now, it won't install the graphic card pilots (radeon). But my main problem has been solved. I just don't get why the CD I own wouldn't work.

---

### Post by pzykotik on 2012-02-06
> **pzykotik said:**
> I've installed with the 10.10 ISO (the one that gaves the graphic problem was 11.10) and it works fine. Only problem I have now, it won't install the graphic card pilots (radeon). But my main problem has been solved. I just don't get why the CD I own wouldn't work.

Once runnning 10.10, I've been prompted to update to 11.04, which I tried. It gave me the same graphic problem I posted earlier. Another problem was that any kind of media wouldn't work. Oh well, thanks for trying to help me out, but I won't be using Ubuntu for now. 

Thanks for your help..

---

### Post by bcbc on 2012-02-06
> **pzykotik said:**
> I've installed with the 10.10 ISO (the one that gaves the graphic problem was 11.10) and it works fine. Only problem I have now, it won't install the graphic card pilots (radeon). But my main problem has been solved. I just don't get why the CD I own wouldn't work.

There are many cases where CD's fail due to bad burns. It happens. Chuck it out and burn another.

If you were trying to install Wubi from a usb stick (which it looks like you were) then don't bother. It doesn't work (in a few limited circumstances it does, but for most cases it will fail). This is due to a fundamental design flaw in Wubi.

But forgetting Wubi..., boot from that USB stick, when you see the little keyboard icon/man, hit the space bar for the extended menu, and then override the boot with 'nomodeset' as described in that link I posted earlier. See if that works.

Of course, if you've made up your mind not to try - then I understand. But you've spent a long time already and I think you're pretty close to succeeding. My opinion.

Also, post your radeon model so I can search on that. Thanks.

---

### Post by pzykotik on 2012-02-08
> **bcbc said:**
> There are many cases where CD's fail due to bad burns. It happens. Chuck it out and burn another.

If you were trying to install Wubi from a usb stick (which it looks like you were) then don't bother. It doesn't work (in a few limited circumstances it does, but for most cases it will fail). This is due to a fundamental design flaw in Wubi.

But forgetting Wubi..., boot from that USB stick, when you see the little keyboard icon/man, hit the space bar for the extended menu, and then override the boot with 'nomodeset' as described in that link I posted earlier. See if that works.

Of course, if you've made up your mind not to try - then I understand. But you've spent a long time already and I think you're pretty close to succeeding. My opinion.

Also, post your radeon model so I can search on that. Thanks.

_***RADEON AMD: ASUS HD 5450 ***_

I have tried: 

{10.10 
-  Original CD boot **(**[B]WHICH ACTUALLY WORKED ON AN OLDER PC....
It was P4 1.7ghz 768mb ram, integrated video-audio XP pro sp2
This is a P4 3.0ghz 2gb ram integrated audio & radeon hd 5450 video)[/B] - _Gave me errors_
-  Wubi original CD installation - _gaves me errors_
-  USB stick from USB creator on the original CD - _didn't work at all_}

{11.10 
-  Downloaded ISO + wubi_ - this is where the screen went crazy._
 - Downloaded ISO on USB stick - _didn't work at all_}

{10.10 
-  Downloaded ISO + wubi} <--- This worked, but wasnt flawless (audio/video wouldnt work, they would have no sound and be played at 48x, even youtube vdeos, w/e) so I used the update manager, did all the updates, rebooted. Then It wasnt fixed, so I updated with the manager, from 10.10 to 11.04, and then I got the screen, again. This is where I gave up.

---

### Post by Rafterman414 on 2012-02-08
That issue with the display is very odd. I am running 11.10 on a system with a Radeon 5550 HD and everything looks just fine. I wouldn't think that there would be that much of a compatibility difference between the two cards since they are all in the same family of chipsets I believe.

---

