---
title: "tv out with ati radeon 7000 (hoary)"
date: 2005-03-10
forum: General Help
---

### Post by robofetus on 2005-03-10
Hello.

I hope this is not a question that has been asked too frequently around here, but I have searched quite a bit and not found anything, so I think I've got no choice but to ask:

is there any way to get tv out working with X with this card (radeon 7000)?  atitvout does detect that my TV is connected; however, I don't think my TV was connected or on when I installed ubuntu.  Could that be related to the problem, or no?  Right now my TV displays a whole bunch of rapid flickering when X is up, and a flickering, unreadable mirror of the screen when X is killed.  

I know that the fglrx drivers do not support this card, and I had just about given up when I saw that atitvout can see that my tv is there.  I tried running dpkg-reconfigure xserver-xorg with the TV on and activated by atitvout and all that, but the resulting X configuration didn't do anything with the TV (and I don't recall it asking me about a second monitor).  

If anyone has a solution to this problem I'd be much obliged.  Even just an xorg.conf file for me to copy/paste and try would be greatly appreciated.  So far Ubuntu is working out extremely well for me, and if I can overcome this hurdle, it will be my only OS for the foreseeable future.  

Thanks for reading.

edit:  a related question I would also pose:  if indeed there is no solution to the above problem, could somebody recommend a (preferably) cheap, decent video card for which tv-out in ubuntu is easy (or at least guaranteed to work when all is said and done)?  if it's not too expensive i'm willing to go that route, since I was thinking of doing some computer upgrades anyway.  thanks again.

---

### Post by deBaas on 2005-03-10
I've been searching a lot for the same card/problem. It would be very nice if someone could help us.

---

### Post by krusbjorn on 2005-03-10
i have the exact same problem/card, and have been searching for a sulotion without success.

edit: just took a closer look and found out that as long as i'm not in X, the TV out works perfectly. But as soon as X starts, that insane flickering also starts. 

btw, i'm on Warty.

---

### Post by sunscape on 2005-03-10
I think you can!

Well maybe... I was using a radeon 7500 not too long ago and I somehow made tv out work (sorry I switched to a 9600 and no longer have the xorg.conf to post).

But, if the 7000 is anything like my 7500 then you don't need to do anytning to your xorg.conf file. Simply configure your system as a single display and change your resolution and refresh rates to coincide with your television. If your tv is hdtv then it will just work in clone mode. If not, then you must find your correct horizontal and vertical refresh rates. I believe they are (something like) 30-60, and 50. But don't quote me on those numbers. I believe you can find the standard refresh rates via google. 

In my experience using options such as notvout = no did not help at all.

If you do not want clone mode, then go fish! :-P. If that is the case then you can fidle with your xorg.conf file until you turn blue.


VERY IMPORTANT!!! Check your video card for a jumper. If you live in the US, then make sure it is set to NTSC. If you have no jumper then goody for you!

---

### Post by Biffy on 2005-03-10
If you have fglrx installed, check the "ATI control" thingie, its located in the KDE-menu if you use KDE. There you can change to different modes such as PAL and NTSC.

If you dont have fglrx, and are getting that flickering, then why not just play your videos in the console? It should work fine, cause i did it on my suse box. No need for X at all. :)

Use fbxine and/or mplayer to play videos. Use a good video driver, such as Vidixfb so you dont get any tearing. Use fbi to watch pictures in the console. Just install fbi in synaptic.

Edit: btw, why does not fglrx work with Radeon 7000 cards? I copied this from the fglrx driver found in apt:

```
This version of the ATI driver officially supports:
 * ATI Radeon 8500, 9000, 9100, 9200, 9250 (R2xx)
 * ATI Radeon 9500, 9550, 9600, 9700, 9800, X300, X400, X600 (R3xx)
 * ATI Radeon X700, X800 (R4xx)
 * ATI Mobility 9000, 9600, 9800
 * ATI FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2, 5100, 7100, 7200
 * ATI Mobility FireGL 9000, T2, T2e
```

Maybe you are just doing something wrong.

---

### Post by robofetus on 2005-03-10
[QUOTE=Biffy]If you have fglrx installed, check the "ATI control" thingie, its located in the KDE-menu if you use KDE. There you can change to different modes such as PAL and NTSC.

If you dont have fglrx, and are getting that flickering, then why not just play your videos in the console? It should work fine, cause i did it on my suse box. No need for X at all. :)

Use fbxine and/or mplayer to play videos. Use a good video driver, such as Vidixfb so you dont get any tearing. Use fbi to watch pictures in the console. Just install fbi in synaptic.

Edit: btw, why does not fglrx work with Radeon 7000 cards? I copied this from the fglrx driver found in apt:

```
This version of the ATI driver officially supports:
 * ATI Radeon 8500, 9000, 9100, 9200, 9250 (R2xx)
 * ATI Radeon 9500, 9550, 9600, 9700, 9800, X300, X400, X600 (R3xx)
 * ATI Radeon X700, X800 (R4xx)
 * ATI Mobility 9000, 9600, 9800
 * ATI FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2, 5100, 7100, 7200
 * ATI Mobility FireGL 9000, T2, T2e
```

Maybe you are just doing something wrong.[/QUOTE]

Oh, I am certain I am doing something wrong.  That's what gave me the thought to come here.  As for the official support list you posted, I don't see the 7000 on there anywhere.  Then again, maybe I am misunderstanding it.

I installed fglrx again (I had it on here once before, in a previous installation--was trying it before I realized my card was unsupported), but I don't use KDE so I don't know how to find the ATi control panel you referred to.  fglrxconfig only invokes a text-based utility, even though the fglrx-conrol package claims to install something that's compiled with qt3.  

I like the idea of the framebuffer thing, though.  I will try it.  However, as I mentioned before, even the console flickers and jerks about uncontrollably on my TV.  Anyone have any idea how that could get fixed?

Thanks again.

---

### Post by Biffy on 2005-03-11
Im sorry man, i tought you meant a 9700 card. I was very tired. :)

It is indeed weird that even your fb-console flickers. When i used Suse, i could get tv-out in X. It was impossible, but it worked very fine in a console.

When you start your computer, do you have the cable connected to the TV? Cause if you got that, it should initialize everything by itself.

---

### Post by Nadir on 2005-03-11
[QUOTE=robofetus]Hello.

is there any way to get tv out working with X with this card (radeon 7000)? atitvout does detect that my TV is connected; however, I don't think my TV was 
[/QUOTE]

Here is what I do to get output on my TV with a Radeon 7000. Note: the tv is the only screen attached to the card.
I turn the pc on with the PC already connected to the card, I use a plain text console (no vesa, no fb), and then I have configured Xorg to use the vesa driver at 800x600.
Everything works fine. mplayer and xine also allow you to get accelerated video playing without xv by using something called vidix and the radeon backend scaler.

The box is a plain Ubuntu Hoary with Freevo installed by hand and I use it for DVD, DivX, OGG/MP3, Internet Radio and Photo viewing.

Tristan

---

### Post by Biffy on 2005-03-11
Hope Nadir's tip works for you.

If not, maybe you should consider buying a card that is supported? I mean, then you will get 3D-acceleration as well. If you have the money, think about it.

---

### Post by krusbjorn on 2005-03-11
[QUOTE=Nadir]Here is what I do to get output on my TV with a Radeon 7000. Note: the tv is the only screen attached to the card.
I turn the pc on with the PC already connected to the card, I use a plain text console (no vesa, no fb), and then I have configured Xorg to use the vesa driver at 800x600.
Everything works fine. mplayer and xine also allow you to get accelerated video playing without xv by using something called vidix and the radeon backend scaler.

The box is a plain Ubuntu Hoary with Freevo installed by hand and I use it for DVD, DivX, OGG/MP3, Internet Radio and Photo viewing.

Tristan[/QUOTE]

Thanks a lot for the input, mate!

---

### Post by Biffy on 2005-03-11
Yes, use vesa with vidix for a great rendered video.

[http://vidix.sourceforge.net/](http://vidix.sourceforge.net/)

Compile and install.

---

### Post by mat24 on 2005-04-26
I am a linux beginner ...
can you give me more information  about how you make it work ???
like more details 

thanx

---

### Post by kenberto on 2005-04-27
So it seems then that it is impossible to get X working with the TV out of a Radeon 7000, right?  Mplayer and the like will work from conosle (worked for me without tweaking) but no matter what you do you will never ever get GUI running?  Is this for xorg only, or xfree86 also?  
If anyone has gotten a Radeon 7000 TV out to display X please please tell me how, explicitly. Don't worry about dumbing it down too much....I'm none too savvy.

Otherwise, back to robofetus' original question, can someone recommend a cheap video card that *will * do TV out with X?

Thanks

---

### Post by onxy on 2005-05-04
I've had the same problem with an ATI all in wonder / Radeon 7500 and 8500. The fgrlx drivers do not work for them (no devices detected) and the standard X radeon driver does not seem to support tv out (I get flickering when starting X, but console is fine).

I went out and bought an nVidia GeForce MX 4000 but the svideo out gets me only black and white output. I'm not sure what to do about either video card, but I am starting to regret turning my windows driven PVR into a Linux box. =(

---

### Post by Huub on 2005-05-06
[QUOTE=mat24]I am a linux beginner ...
can you give me more information  about how you make it work ???
like more details [/QUOTE]

I've had the same problem (no TV-out) today and yesterday, using a PCI Radeon 7000 card. Since I'm making a PC thats only connected to the television I needed it to work ;). 

For those (like me) who couldn't escape the graphical interface of Xorg in the beginning: ctrl-alt-f1 (or F2 - F6) gives you a console screen where you can login and play around. After that you can edit the xorg.conf file with (for example) "vim /etc/X11/xorg.conf" (changing things works with the "insert" key, saving+quitting with ":wq" after pressing escape to close editting).

After changing the driver setting from "ati" to "vesa" in xorg.conf, plus changing the refreshrates (to be sure) to the ones Knoppix uses (H: 20-96, V:50-75 if I'm not mistaken) I restarted KDE (am using Kubuntu) and it worked :).

To restart KDE without rebooting, type "killall kdm" (or gdm for gnome) to close a (possibly still running) KDE Desktop Manager, and type "kdm" to start it again ("Xorg also works).

I hope this helps a bit.

---

### Post by kenberto on 2005-05-10
Helps a lot Huub.  I got everything to work with Knoppix and, sick of dealing with this problem, settled for that and installed it to the hard disk.  Still I have this haunting doubt that I must be missing something with a one disc installation...good to know how you got it to work with (k)ubuntu.

---

### Post by jdog on 2005-06-13
Thanks Huub, I got my Radeon 7000 tv out working in gnome. But I still have one problem. I can not use the X11/XV driver to player movies in mplayer. If i use one of the other drivers in mplayer and I goto full screen the movie sits in the middle of the screen and is very small.

---

### Post by dwaldie on 2005-07-11
I just stumbled upon this thread, on most 7000 cards there is a jumper on the video card to switch it between PAL and NTSC, the default is PAL.  Switching it help, since linux can't do the auto switch like windows yet.

David

---

### Post by remmelt on 2005-10-09
[QUOTE=jdog]Thanks Huub, I got my Radeon 7000 tv out working in gnome. But I still have one problem. I can not use the X11/XV driver to player movies in mplayer. If i use one of the other drivers in mplayer and I goto full screen the movie sits in the middle of the screen and is very small.[/QUOTE]

Please share with us how you did this!

---

