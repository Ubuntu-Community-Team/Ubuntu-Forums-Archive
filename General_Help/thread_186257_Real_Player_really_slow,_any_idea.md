---
title: "Real Player really slow, any idea?"
date: 2006-06-01
forum: General Help
---

### Post by turbojugend_gr on 2006-06-01
Hey, I got Real Player installed through the "realplay" Synaptic package.

The problem is very , very slow!!!

I believe to have nvidia drivers installed, through th repos. I get high , very high FPS numbers in openGL games....

It seem to act like it's "laggy" or something, don't get confused though the movies are in my HD (rmvb movies) and are playing gracefully in Windoz...

Any help?](*,)

---

### Post by Loffe_ on 2006-06-02
I have the same problem, if I click anywere in it when playing it takes seconds to react.

The same problems appears when watching video. I get about one frame every 5 - 10 second while the sound is working as expected.

/Loffe

---

### Post by angkor on 2006-06-02
Another one here.

Strange thing is, it worked flawlessly with .rmvb files yesterday. However today I've reinstalled Ubuntu (32bit version) on a AMD 64 x2 3800+ and it refuses to play nice. I'm using the nvidia drivers, dma enabled and I'm running the k7 kernel.

Let's file a bug or something.

---

### Post by turbojugend_gr on 2006-06-02
[QUOTE=Loffe_]I have the same problem, if I click anywere in it when playing it takes seconds to react.

The same problems appears when watching video. I get about one frame every 5 - 10 second while the sound is working as expected.

/Loffe[/QUOTE]
Yeah that's a more accurate approach to my problem actually, it is just like that for me to.

[QUOTE=angkor]Another one here.

Strange thing is, it worked flawlessly with .rmvb files yesterday. However today I've reinstalled Ubuntu (32bit version) on a AMD 64 x2 3800+ and it refuses to play nice. I'm using the nvidia drivers, dma enabled and I'm running the k7 kernel.

Let's file a bug or something.[/QUOTE]

Again, like that, I also use the k7-SMP kernel...Weird, Please give us some help here... ](*,)

---

### Post by angkor on 2006-06-03
[QUOTE=turbojugend_gr]Yeah that's a more accurate approach to my problem actually, it is just like that for me to.



Again, like that, I also use the k7-SMP kernel...Weird, Please give us some help here... ](*,)[/QUOTE]

I'm circumventing the problem atm by using mplayer to play the .rmvb files. At least I get to see my scrubs episodes now. :) No luck yet in fixing realplayer.

> Again, like that, I also use the k7-SMP kernel

I checked the default i386 kernel btw, same problem.

---

### Post by blackjack6.21.91 on 2006-06-03
Try getting the helix player, also available at the repos.  I believe it's supposed to be less troublesome

---

### Post by turbojugend_gr on 2006-06-03
[QUOTE=angkor]I'm circumventing the problem atm by using mplayer to play the .rmvb files. At least I get to see my scrubs episodes now. :) No luck yet in fixing realplayer.[/QUOTE]

Hey you get smooth playing with mplayer? If yes what do I need to use mplayer, I use totem-xine. And if I need to do any tricking to get it playng please say so...

---

### Post by angkor on 2006-06-03
I downloaded the essential-codec package from the mplayer website:

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

And copied the contents to /usr/lib/win32

After that I could play .rmvb's using mplayer.

Still don't know what is wrong with realplayer though...

---

### Post by hajk on 2006-06-03
It's not a new problem, I tried both the RealPlayer 10 deb-package from the Marillat repository and the direct install of the RealPlayer 10 bin-file (dated March 2006) downloaded from the helix DNA site. Still the same problem, indeed both using i386 and (later) k7-smp kernels. 

I am now using gxine or totem-xine to run my Real audio and video feeds. Both gxine and totem-xine complain sometimes about "redirection" of http websites. This can be overcome by first running "wget http://......" in a terminal, which creates a small .ram or .rm file containing the stream address. If you then point gxine or totem-xine at this file, the streams play perfectly. Add them to favourite media , then you preserve the address for future reference. Needs installing the w32codecs package from the Marillat site for the real codecs...:D

---

### Post by turbojugend_gr on 2006-06-04
[QUOTE=hajk] Needs installing the w32codecs package from the Marillat site for the real codecs...:D[/QUOTE]

How do I do so? Sorry for being green on this, but I got all my codecs installed following the tutorials on the official site, or those on the wiki, or in some cases with Easyubuntu.

Is there a package that I download? (.deb)?

---

### Post by turbojugend_gr on 2006-06-10
Success!! (for now..I will w8 a couple of days to sign for this one... :-) )

Here is what I did, I removed the "realplay" package through synaptic, I installed the "gstreamer0.10-gl" package, which Easyubuntu (I believe so) should add this too, and then I downloaded the following ```
wget -c ftp://ftp.nerim.net/debian-marillat/pool/main/r/realplay/realplayer_10.0.7-0.0_i386.deb
```
I installed it and all is fine!

If you lack the same gstreamer-gl library, be sure to check if you get fixed after installing it, before removing the repo realplayer.

---

### Post by schoo on 2006-07-17
I am also having the similar problem after installing "realplay" from Synaptics. I tried playing rmvb files and the video runs but with about 3 seconds slower... I hope I can watch videos with Real Player because I have my machine connected to my TV.

---

### Post by schoo on 2006-07-18
My problem is solved by using Mplayer rather than using Real Player to play my RMVB files.... Mplayer rocks!:p

---

### Post by Coops on 2006-07-25
any one had any more ideas about this problem?
I use mplayer as much as I can but stuff like the BBC Radio listen again service only fully works with the proper realplayer.

I've tried the above gstreamer0.10-gl trick, but no luck.

It was working fine until two days ago when I reinstalled (breezy->dapper).

Coops.

---

### Post by turbojugend_gr on 2006-07-25
are you sure you did what I suggested in my past posts???

If not follow the last post of mine (from now on, second last). It works fine for me. Note that there should be a newer package so make your checks for it (an ftp browse to the last catalogue should clear things out for you).

---

### Post by unlivingrolan on 2006-09-16
Hello there, this might help:
[http://blogorrhoea.wordpress.com/2006/03/01/linux-realplayer-choppy-video-fix-how-to/](http://blogorrhoea.wordpress.com/2006/03/01/linux-realplayer-choppy-video-fix-how-to/)

I got mine fixed this way.

Cheers

---

### Post by kline on 2006-09-23
> **turbojugend_gr said:**
> are you sure you did what I suggested in my past posts???

If not follow the last post of mine (from now on, second last). It works fine for me. Note that there should be a newer package so make your checks for it (an ftp browse to the last catalogue should clear things out for you).

I'm not sure if this applies to this thread, but in recent days, my realplay apps takes several seconds to recover when unovered by  a termnal (or other GUI app); also the time counter updates only sever 8 to 11 seconds.  

I do have many other workspaces loaded, but (1) my Ubuntu servr is fast and has 1G of memory...

Suggestion on how to reseolve this s-l-o-w-n-e-s-s issue will be much appreciated!   FWIW, I have realplay running on other, much slower,servers:: no problem.

---

### Post by kelbizzle on 2006-12-30
I noticed a few of you are using Beryl. I am also. Realplayer plays slow for me. Although, When I select metacity instead of beryl the video plays ok. This could be due to my older hardware. But I doubt it. I'm gonna test when I get my new card. Right now I have a Nvidia Ti 4200

---

### Post by raghuramos1987 on 2007-09-10
k...same prob here...

realplayer 10 lags and xfmedia doesn wrk(audio and video) and tried the codecs of mplayer...the prob with this is that the clip stops before it actually ends...(like if its 20 mins long it stops abruptly at the 15th min or somethin)

any help please

---

