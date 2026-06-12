---
title: "Flash 10.2 + multiple monitors - not working correctly"
date: 2011-02-12
forum: General Help
---

### Post by azredwing on 2011-02-12
Hi all - 

Running Flash 10.2 on Ubuntu 10.10 x64. I've got a dual screen setup and I was super excited to see that the latest Flash allows multiple monitor use!..

..except mine doesn't. If I full-screen a video on one monitor, clicking away from it still returns back to regular sized. 

This happens both in Chrome and Firefox.

Anyone have any idea what is going on?

---

### Post by Foxcow on 2011-02-12
I'm also curious.  In Win7, that feature works beautifully.


How did you install the latest version of flash?  At first, I tried to get it from Adobe Labs but I could not find a 64-bit version.  I ended up using the flash installer that comes in 'Ubuntu Restricted Extras.'

---

### Post by azredwing on 2011-02-12
> **Foxcow said:**
> I'm also curious.  In Win7, that feature works beautifully.


How did you install the latest version of flash?  At first, I tried to get it from Adobe Labs but I could not find a 64-bit version.  I ended up using the flash installer that comes in 'Ubuntu Restricted Extras.'

The Chrome version came with the latest version of Chrome. (heh). I updated my system and it updated flashplugin-nonfree, so I think I already had that repository allowed.

---

### Post by jwcalla on 2011-02-12
I always had this problem when I had "Undirect Fullscreen Windows" selected in the Compiz Config Settings Manager.

I don't know what that option is used for but I can never play Flash fullscreen when it's checked.

---

### Post by azredwing on 2011-02-13
> **jwcalla said:**
> I always had this problem when I had "Undirect Fullscreen Windows" selected in the Compiz Config Settings Manager.

I don't know what that option is used for but I can never play Flash fullscreen when it's checked.

Thanks for the tip, but it didn't help..

The problem isn't that Flash won't play full screen. It does! It's that under Flash 10.2, I should be able to click away from the video and keep it full screened.

---

### Post by azredwing on 2011-02-21
no other ideas? :( i'm surprised there isn't more on the subject. maybe it's not available for x64..?

---

### Post by oracle2b on 2011-02-24
I too am having difficulty getting full screen flash to work with dual monitors on 10.4. I'm using the 32-bit version.

---

### Post by darthpaul on 2011-02-25
> **azredwing said:**
> Hi all - 

Running Flash 10.2 on Ubuntu 10.10 x64. I've got a dual screen setup and I was super excited to see that the latest Flash allows multiple monitor use!..

..except mine doesn't. If I full-screen a video on one monitor, clicking away from it still returns back to regular sized. 

This happens both in Chrome and Firefox.

Anyone have any idea what is going on?

i'm in the same boat.  any solutions yet?

---

### Post by azredwing on 2011-03-09
> **darthpaul said:**
> i'm in the same boat.  any solutions yet?

doesn't look like it, which is frustrating. :/

---

### Post by jwcalla on 2011-03-09
It seems to happen whenever the window loses focus.

---

### Post by azredwing on 2011-03-09
> **jwcalla said:**
> It seems to happen whenever the window loses focus.

right - which it shouldn't be with flash 10.2 now.

---

### Post by Foxcow on 2011-03-09
It looks like a 10.3 beta is available:


I'm not sure about a link for 64-bit but I'm still searching for it.

[http://labs.adobe.com/downloads/flashplayer10-3.html](http://labs.adobe.com/downloads/flashplayer10-3.html)

---

### Post by azredwing on 2011-03-22
> **Foxcow said:**
> It looks like a 10.3 beta is available:


I'm not sure about a link for 64-bit but I'm still searching for it.

[http://labs.adobe.com/downloads/flashplayer10-3.html](http://labs.adobe.com/downloads/flashplayer10-3.html)

has this helped?

---

### Post by Foxcow on 2011-03-22
> **azredwing said:**
> has this helped?



I haven't tried it because I use 64 bit Ubuntu.  I wish they would release a current 64 bit version.

---

### Post by Dimitree on 2011-04-19
Well it seams that 10.3 is still not working.
As a "workaround"...

In Opera you can 

1.Drag the tab with the flash movie to the task bar which will make it a second Opera instance.
Then drag the window to your second monitor and maximize.

2.Press the "+" key to "zoom-in".
Once you zoom-in you can center on the flash movie window with the scroll bars.

3.Press "*" to restore original settings for the page.

You get almost fullscreen flash playback hehe...

I hope they will fix this soon :/
I like to watch NASA HD on ustream on my second monitor...

---

### Post by SycloneMedia on 2012-01-03
Any updates on this issue...? I guess it's still not fixed out of the box? Having this problem on Kubuntu 11.10 64bit, brand new install.

I was wondering if there is a workaround using the [System Settings>Window Behavior>Window Rules] settings?

:confused:

---

### Post by Jaylor on 2012-12-27
NOTE: Only for the ADOBE Flash plugin

Hah, I'm looking for a solution for a whole other issue and keep on finding questions about this one that I've already found the answer to so I'll post what the solution I found.

And its quite easy, does take some command line and Hex editing but the directions are GREAT!

Heres the issue:  Adobe hasn't decided to take the In Focus tag out of the Linux plugin yet.  (Windows and Mac used to have the same problem years ago but they've changed the plugins for those OS's.. no clue why they haven't for Linux)

So heres what you do:

Goto [http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html](http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html)
and scroll down to:
**Get Flash videos to remain full screen when working (clicking) in the other desktop**

I did the 2nd method of editing the Adobe Plugin using a Hex editor and it worked great!  (I didn't want to deal with another plugin for Firefox).  It takes longer to setup but then you don't have to worry about clicking on the Maxamize Flash icon every time you want to watch a movie.

---

### Post by azredwing on 2013-01-13
> **Jaylor said:**
> NOTE: Only for the ADOBE Flash plugin

Hah, I'm looking for a solution for a whole other issue and keep on finding questions about this one that I've already found the answer to so I'll post what the solution I found.

And its quite easy, does take some command line and Hex editing but the directions are GREAT!

Heres the issue:  Adobe hasn't decided to take the In Focus tag out of the Linux plugin yet.  (Windows and Mac used to have the same problem years ago but they've changed the plugins for those OS's.. no clue why they haven't for Linux)

So heres what you do:

Goto [http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html](http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html)
and scroll down to:
**Get Flash videos to remain full screen when working (clicking) in the other desktop**

I did the 2nd method of editing the Adobe Plugin using a Hex editor and it worked great!  (I didn't want to deal with another plugin for Firefox).  It takes longer to setup but then you don't have to worry about clicking on the Maxamize Flash icon every time you want to watch a movie.

This worked perfectly! Thanks. If you post this solution to the following AskUbuntu question: [http://askubuntu.com/questions/59328/dual-screen-flash-does-it-work](http://askubuntu.com/questions/59328/dual-screen-flash-does-it-work) I will give you credit for the proper solution!

---

