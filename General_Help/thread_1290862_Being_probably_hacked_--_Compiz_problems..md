---
title: "Being probably hacked -- Compiz problems."
date: 2009-10-14
forum: General Help
---

### Post by sopadeajo on 2009-10-14
All works Ok including appliations. I decide to open CompizConfig Settings Manager,uncheck some activated plugins from the menu, and suddenly a black area appears in the CCSM window, small first. It happened to me 2 days ago and i had to reinstall. So this time i try to open quickly a terminal and type compiz --replace in it. But mouse seems to be blocked and Alt+f2 does not obey. Soon half the screen is black and totally irresponsive.I know what will happen: no way to get back to a desktop mode. A total black screen when booting again.     I think i am being hacked maybe by people from this forum who know my IP. Or else there should be a  publicized known bug in Compiz.    Any way if being hacked to get rid of the intruders?    Any way to rescue Ubuntu without a reinstall? (writing this with Vista)

---

### Post by cariboo on 2009-10-14
Normal forum users can't see your ip address. Have you checked [Launchpad]("https://bugs.launchpad.net") to see if anyone else has run into the same bug.

It sounds like you have a graphics driver or compiz problem.

---

### Post by __p1n__ on 2009-10-14
> **sopadeajo said:**
> All works Ok including appliations. I decide to open CompizConfig Settings Manager,uncheck some activated plugins from the menu, and suddenly a black area appears in the CCSM window, small first. ...

It couldn't be related to that could it?  I mean, it *must* be hackers.

---

### Post by Zero++ on 2009-10-14
Have you tried using metacity instead of compiz? do you have any problems then?

---

### Post by sopadeajo on 2009-10-14
Here is a way to know the IP of somebody ina forum.There are more.  [http://themostboringblogintheworld.wordpress.com/2006/10/10/hack-image-shack-find-the-ips-of-the-uploader-for-any-pic/](http://themostboringblogintheworld.wordpress.com/2006/10/10/hack-image-shack-find-the-ips-of-the-uploader-for-any-pic/)  I cannot boot to Ububtu . I just get an unresponsive total black screen.I do not want to reinstall.I tried to boot opening a Terminal and typing compix --replace on it. But it did not work (could not open or find something...(was the answer)).  Any help to boot to desktop Ubuntu without reinstalling?????  Control+alt+F1 opens a kind of whole screen new booting Terminal that asks me for password but compiz--replace does not work in it and i do not know what to write on it to rescue my system if rescue is possible.I´ll try later with metacity --replace

---

### Post by CharlesA on 2009-10-14
> **sopadeajo said:**
> Here is a way to know the IP of somebody ina forum.There are more.  [http://themostboringblogintheworld.wordpress.com/2006/10/10/hack-image-shack-find-the-ips-of-the-uploader-for-any-pic/](http://themostboringblogintheworld.wordpress.com/2006/10/10/hack-image-shack-find-the-ips-of-the-uploader-for-any-pic/)

You do know that that "hack" was only to find the IP of whoever uploaded an image and is now fixed? Do your research first please.

>  I cannot boot to Ububtu . I just get an unresponsive total black screen.I do not want to reinstall.I tried to boot opening a Terminal and typing compix --replace on it. But it did not work (could not open or find something...(was the answer)).  Any help to boot to desktop Ubuntu without reinstalling?????If you are able to get to a terminal screen try running just compiz.

EDIT: Do you mean compix or compiz? compiz --replace is the command.

---

### Post by cariboo on 2009-10-14
I would depend on what version you are running, if you are running Jaunty, start in recovery mode and at the menu choose drop to root prompt. Once at the prompt mv your current /etc/X11/xorg.conf to a backup eg:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

After running the above command type exit at the prompt and select resume from the menu. THis should get you back to your desktop.

> Here is a way to know the IP of somebody ina forum.There are more. [http://themostboringblogintheworld.w...r-for-any-pic/](http://themostboringblogintheworld.w...r-for-any-pic/) 

The above only works if you use Image ack to host your pictures.

I moved this thread to General Help, as it has nothing to do with security.

---

### Post by sopadeajo on 2009-10-14
I have done: mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak  in command line in recovery mode and then resumed and i got the background image to be seen gor a few seconds (that i could not see before) and then again the total irresponsive black screen.  have tried matacity --replace and get: window manager error: Unable to open X display  I must say that my Intel garphic card worked well with all the Compiz effects: rotating cube and sphere and cylinder, fire and water effects, without problems when it worked.

---

### Post by t0p on 2009-10-14
> **sopadeajo said:**
>      I think i am being hacked maybe by people from this forum who know my IP. Or else there should be a  publicized known bug in Compiz.    Any way if being hacked to get rid of the intruders?    Any way to rescue Ubuntu without a reinstall? (writing this with Vista)

I assume this kind of paranoia comes from having a Windows state of mind.  People who have run Linux exclusively for an extended period have shaken this irrational fear.  Thus I find it amusing that the OP is using Vista because of fears that his Ubuntu system is "being hacked".

But why does the OP think it is people from this forum who are "hacking" his machine?  Are Ubuntu users  especially disreputable?  I thought we were kinda cuddly...

Oh, and that Imageshack IP grabbing trick no longer works, according to the link provided by the OP.  So how else can a user of this site (without administrative access) learn a user's IP?

---

### Post by Slim Odds on 2009-10-14
> **__p1n__ said:**
> It couldn't be related to that could it?  I mean, it *must* be hackers.

Yes, and the hackers name is [B]sopadeajo

[/B]

---

### Post by StuartN on 2009-10-14
> **t0p said:**
> I assume this kind of paranoia comes from having a Windows state of mind.

I think Linux is alert to security, and is not full of false alarms as a result. We have a Windows Vista machine on the network occasionally and it is amazing what is open (telnet, remote command, C$ operating system disk share, some kind of remote admin...).

Generally in Linux if there is a black rectangle on your screen (or whatever) then it is a software or a hardware error. If you are still worried, then run Firestarter or some other firewall to see all your open connections and run ClamAV to look for (Windows) viruses on your disks.

---

### Post by Giblet5 on 2009-10-14
> **__p1n__ said:**
> It couldn't be related to that could it?  I mean, it *must* be hackers.

I just spewed coffee on my keyboard. Thanks!

---

### Post by Giblet5 on 2009-10-14
> **t0p said:**
> I thought we were kinda cuddly...

This from the guy with the pit-bull avatar... :)


This is not hackers.

This is a video driver or xorg setting problem.

Can you please bring up a terminal window and post the output of ```
xdpyinfo
```

---

### Post by mechro on 2009-10-14
```
fi@fifofum-desktop:~$ xdpyinfo
name of display:    :0.0
version number:    11.0
vendor string:    The X.Org Foundation
vendor release number:    10600000
X.Org version: 1.6.0
maximum request size:  16777212 bytes
motion buffer size:  256
bitmap unit, bit order, padding:    32, LSBFirst, 32
image byte order:    LSBFirst
number of supported pixmap formats:    7
YOU HAVE BEEN HACKED

```

---

### Post by Slim Odds on 2009-10-14
> **sopadeajo said:**
> The two writers(top and Slim Odds) are simply  2 sons of a bitch.If i find you i ´ll make you pay for your insults...

My comment was intended to be a light hearted joke.

Is there no sense of humor left in the world today?

You need to lighten up a bit.........

I believe that I was not the only one that thought you have overreacted to your perceived problem. You might want to take a deep breath next time and think before you post that you think you've been hacked right after a change that you've made produces strange results for you.

I hope you know that making threats on the Internet are taken very seriously these days. You may be putting yourself into a situation that you don't want to be in.

---

