---
title: "Weird Graphics/Flash Glitch?"
date: 2011-02-15
forum: General Help
---

### Post by WannabeFantasma on 2011-02-15
Hey all

I installed the latest Nvidia drivers yesterday, and I got some weird glitch.. When I'm watching a youtube video on another tab and when there's black on the tab I'm looking on it's like a see trough...
I can see the video through any black (even these letters as I type)
Even happens when I'm in XBMC.

Was going to include screenshots but on screenshots black is black...

Someone knows what the problem is?

Video Link [http://www.youtube.com/watch?v=DBYcMN1uTDg](http://www.youtube.com/watch?v=DBYcMN1uTDg)

---

### Post by Magick93 on 2011-02-15
Yes I have the same thing. 

I think there was an update to the Flash player and its causing it.

Not sure yet how to fix it.

---

### Post by WannabeFantasma on 2011-02-15
Oh could be, I Uninstalled the old flash and installed the new one...

Hopefully someone knows a solution soon :D because it's kind of annoying... :D

---

### Post by Magick93 on 2011-02-15
Ok found a fix!

When flash is playing, right mouse click, select settings. Then disable hardware acceleration. 

Atleast that helped for me.

---

### Post by WannabeFantasma on 2011-02-15
> **Magick93 said:**
> Ok found a fix!

When flash is playing, right mouse click, select settings. Then disable hardware acceleration. 

Atleast that helped for me.

But I want hardware acceleration?

---

### Post by WannabeFantasma on 2011-02-16
Can someone please help me?
PS: I want to keep my Graphics acceleration.

---

### Post by The Stinger on 2011-02-16
I had the same problem for the passed few days, but after reading your post I thought "Why not revert back to the older Nvidia driver." and that seemed to work for me.

Just got to System > Administration > Extra Drivers > And select the older verion(173) and it should work.

Edit: The above names might be a bit different, I'm running Ubuntu in Dutch and just  translated it to what I thought it was in English.
Edit2: A you live in Belgium, if you run the Dutch version just go to Systeem > Beheer > Extra Stuurprogramma's > And select the older verion(173) or anything except "aanbevolen".

---

### Post by WannabeFantasma on 2011-02-17
> **The Stinger said:**
> I had the same problem for the passed few days, but after reading your post I thought "Why not revert back to the older Nvidia driver." and that seemed to work for me.

Just got to System > Administration > Extra Drivers > And select the older verion(173) and it should work.

Edit: The above names might be a bit different, I'm running Ubuntu in Dutch and just  translated it to what I thought it was in English.
Edit2: A you live in Belgium, if you run the Dutch version just go to Systeem > Beheer > Extra Stuurprogramma's > And select the older verion(173) or anything except "aanbevolen".

Ah bummer, after all the hassle of updating to newer version.(I ran the ".run" file wich gave me some errors of drivers already installed etc... after 3 times it finally got it to work) 
Now I got to switch back?!? 

Any other solutions?

Yes I'm from Belgium, but I love the English language so I mostly pick English when I install Ubuntu :D

---

### Post by hvbakel on 2011-02-17
See here [http://http://www.nvnews.net/vbulletin/showthread.php?t=159619]("http://http://www.nvnews.net/vbulletin/showthread.php?t=159619"); apparently disabling hardware accelleration does not disable vdpau rendering of video.

---

### Post by WannabeFantasma on 2011-02-18
> **hvbakel said:**
> See here [http://http://www.nvnews.net/vbulletin/showthread.php?t=159619]("http://http://www.nvnews.net/vbulletin/showthread.php?t=159619"); apparently disabling hardware accelleration does not disable vdpau rendering of video.

Is youtube VDPAU? since I disabled hardware accelleration and 1080p is laggy again....

+ Think I'm going to re-install older flash version... 1080P was more laggy, but didn't show this weird stuff + new one crashes alot on me....

Anyone knows where to download the older flash?

---

### Post by WannabeFantasma on 2011-04-14
Just quick update: Just bought a 1080P screen and can't even watch 360P youtube videos on full screen because I had to disabled hardware acceleration...(i think)

= Super sad :(

---

### Post by WannabeFantasma on 2011-04-18
Update on status at this moment
Updated Firefox to 4 + Flash to 10.2.159.1


And it's still happening :(

NEW Video Link: [http://www.youtube.com/watch?v=OqufCyU4AEU](http://www.youtube.com/watch?v=OqufCyU4AEU)

Can someone please help me? I really need hardware acceleration because even 360P will stutter on my Atom330/ION on a full HD screen :( so I don't want to turn it off (wich fixes the bug)

Maybe this belongs in the Multimedia & Video section?

---

### Post by WannabeFantasma on 2011-04-18
Someone? please?

---

### Post by gesti on 2011-04-20
Hello,

I have struggled with this one for the past week or so. (next to other stuff)
So my system is: **ATI HD4850 on an ASUS P5Q3**
os: **Ubuntu 10.10 The Maverick Meerkat 64-bit** release.
The "glitch" was that I had running **black stripes** in the flash.  (a good example for me was in Mafia Wars on facebook). Also sometimes  the videos went kinda blank, if I switched to another tab in** Mozilla - Firefox**.

I have tried to disable some tool tips like others advised and also  tried to switch hardware acceleration off, but had no such option.

So here comes my **solution**:

[LIST=1]
[*]Remove all the previous flash-players you have (make sure there is  no libflashplayer.so in your Firefox plugins folder -  /usr/lib/firefox-4.0/plugins/ )
[*]Download the [Adobe Flash Player "Square" Preview]("http://labs.adobe.com/technologies/flashplayer10/square/"). This is the flash player from adobe for 64-bit system users.
[*]After unpacking the tar, there is a **libflashplayer.so** file in it. You will need to **copy** this **in to /usr/lib/firefox-4.0/plugins**.
[*]Now just restart Firefox and then test it!
[/LIST]
 I wrote firefox-4.0 as by now i assume that's what most of us are using.  If not then of course you will need to go into the folder with the  right version number.

Good luck and a happy tux to you all,
s

---

### Post by gradinaruvasile on 2011-04-20
Flash 10.3/10.3 (version 10.2.159.1 or  from Adobe is plain buggy on newer nvidia cards (seems ati too).
This is because the 10.2 series introduced hardware decoding for cards that support it (nvidia 8xxx and newer, ati 4xxx and newer).

But this hardware decoding implementation is done wrong (there is a theory in th link) and leads to glitches on the said hardware.

BTW the hardware decoding IS NOT ENABLED BY DEFAULT - you have to create a

/etc/adobe/mms.cfg

file and put this in it:

EnableLinuxHWVideoDecode=1

and restart the browser in order to use it. But the player is buggy with or without this file.

Here is a thread about the issue:

[http://www.nvnews.net/vbulletin/showthread.php?t=161664](http://www.nvnews.net/vbulletin/showthread.php?t=161664)

Workarounds:

I use the flash player (version 10.3 d180) that comes bundled with Chrome (libgcflashplayer.so) in all my browsers. This Flash version has the problematic HW decoding effectively disabled, it is not the same as the Adobe-released version.
There is a flash player 11 preview version, named "incubator" that is more stable than the 10.2/3:

[http://labs.adobe.com/downloads/flashplatformruntimes_incubator.html](http://labs.adobe.com/downloads/flashplatformruntimes_incubator.html)

---

### Post by WannabeFantasma on 2011-04-21
> **gesti said:**
> Hello,

I have struggled with this one for the past week or so. (next to other stuff)
So my system is: **ATI HD4850 on an ASUS P5Q3**
os: **Ubuntu 10.10 The Maverick Meerkat 64-bit** release.
The "glitch" was that I had running **black stripes** in the flash.  (a good example for me was in Mafia Wars on facebook). Also sometimes  the videos went kinda blank, if I switched to another tab in** Mozilla - Firefox**.

I have tried to disable some tool tips like others advised and also  tried to switch hardware acceleration off, but had no such option.

So here comes my **solution**:

[LIST=1]
[*]Remove all the previous flash-players you have (make sure there is  no libflashplayer.so in your Firefox plugins folder -  /usr/lib/firefox-4.0/plugins/ )
[*]Download the [Adobe Flash Player "Square" Preview]("http://labs.adobe.com/technologies/flashplayer10/square/"). This is the flash player from adobe for 64-bit system users.
[*]After unpacking the tar, there is a **libflashplayer.so** file in it. You will need to **copy** this **in to /usr/lib/firefox-4.0/plugins**.
[*]Now just restart Firefox and then test it!
[/LIST]
 I wrote firefox-4.0 as by now i assume that's what most of us are using.  If not then of course you will need to go into the folder with the  right version number.

Good luck and a happy tux to you all,
s

I don't have a 64 bit os so :(

---

### Post by WannabeFantasma on 2011-05-03
Ubuntu 11.04 with flash(hardware acceleration) doesn't have this bug? :/ don't wanna switch on my HTPC! :(

(same flash version/same firefox version.... )

---

