---
title: "Display going to sleep"
date: 2010-05-14
forum: General Help
---

### Post by Man_Beach on 2010-05-14
How can I stop my display going to sleep?

I've got the Power Management settings for mains power as:

Actions - put computer to sleep when inactive - never

Display - put display to sleep when inactive - never

Screensaver settings are:

Regard computer as idle set to 2 hours

Unticked Activate screensaver when computer is idle

Yet the screen still goes blank after a few minutes when I'm not using it.

I dual boot and it doesn't do it in Windows. It didn't do it in 8.10 or 7.10 either.

---

### Post by eltonw on 2010-05-14
> **Man_Beach said:**
> How can I stop my display going to sleep?

I've got the Power Management settings for mains power as:

Actions - put computer to sleep when inactive - never

Display - put display to sleep when inactive - never

Screensaver settings are:

Regard computer as idle set to 2 hours

Unticked Activate screensaver when computer is idle

Yet the screen still goes blank after a few minutes when I'm not using it.

I dual boot and it doesn't do it in Windows. It didn't do it in 8.10 or 7.10 either.
Since you mention "mains" in your post, does this mean you are using a laptop?

**You gave no information on your hardware.** 

Is the machine ON mains, or running off the battery? If on battery, what are your power savings for battery usage?:confused:
Even if plugged in, could it be on a power-bar which might have been (accidetally) turned off, so you are (in reality) running off battery power?:confused:

... just some things to consider....

HTH.

---

### Post by burton247 on 2010-05-14
Change your screen saver settings. Your display will still be on but the screen saver will cut in, likely to be just a blank screen. Defualt it comes on after 5 mins

---

### Post by Man_Beach on 2010-05-14
It's on mains power (it's not a laptop) and I have no need for power management. As for screensaver, I've tried changing it from the default blank screen setting to see what happens. If that works, I'll mark it as solved.

---

### Post by burton247 on 2010-05-14
Sorry I didn't read that you unchecked activate screen saver when idle. Do you know if it is the screen saver cutting in or the display turning off?

---

### Post by Man_Beach on 2010-05-14
It's the display turning off - but it hasn't done it for the past few hours so maybe it's cured itself. We'll see. It is, after all, just 2 weeks into 10.04 so there're lots of oddities to sort themselves out yet. I seem to be downloading updates daily.

---

### Post by Man_Beach on 2010-05-15
No, it's still happening. Turn the computer on, go away and leave it for 10 minutes and when you come back the display has gone into power saving mode.

It's a fairly normal generic LCD monitor connected to the VGA port and as I said earlier, it doesn't do it with Windows XP and it never used to with 7.10 and 8.10.

As far as I can tell, I've turned off every sort of power saving and screen saver option available.

---

### Post by Man_Beach on 2010-05-16
I've found that it always does it when I turn on the computer, and stops if I click on the Power Management in System > Preferences. It's not necessary to do anything. Just close the Power Management applet and it's OK for the rest of the session.

I'll treat it as yet another quirk of Ubuntu.

---

### Post by scouser73 on 2010-05-16
Try Caffeine to keep your monitor on, use these command in Terminal.

> **sudo add-apt-repository ppa:caffeine-developers/ppa**

> **sudo apt-get update**

> **sudo apt-get install caffeine**

Caffeine can be used upto 168 hours & 59 minutes before the screen turns to power saving mode.

I use it on my pc as I was fed up of the screen going black when I was watching a film.

---

### Post by yoshimitsuspeed on 2010-05-17
> **scouser73 said:**
> Try Caffeine to keep your monitor on, use these command in Terminal.







Caffeine can be used upto 168 hours & 59 minutes before the screen turns to power saving mode.

I use it on my pc as I was fed up of the screen going black when I was watching a film.


Why should you need another application to stop the screen from shutting off though?
I have the same problem. Seems like I had it in kubuntu 9 but I think it was more like 20-30 min. Now it's 10.
Same as the OP I have turned off all power saving options I can find as well as the screen saver. there is no reason this should be happening. 
I just downloaded caffeine. I'll give it a shot but it's annoying to think I'd even have to.

---

### Post by suomaf on 2010-05-18
I know what you are talking about.. there is a command line setting either to the power management or the screen saver.. I just forgot what it is.. I know that it is on this forum that I found it though.. If I remember I will repost here

---

### Post by suomaf on 2010-05-18
Ok got it.. what you have to do is type gconf-editor in a terminal and then navigate to apps, screensaver.. there are options in there that you can adjust. This stops the screen from blanking out every few minutes.. Hope this is what you are looking for.

---

### Post by yoshimitsuspeed on 2010-05-19
Should have added I'm in Kubuntu. 

I installed gconf-editor to check it out but it doesn't list screen saver under apps for me.

I did install caffeine and it did the trick but I'm still annoyed I even need it. WTF?

---

### Post by abumaia on 2010-05-19
I'm having this same issue.
Suomaf, what options were you referring to, to adjust?  Everything under apps> gnome-power-manager and gnome-screensaver reflects the same settings I have in the Power manager and Screensaver windows.

---

### Post by Man_Beach on 2010-05-26
I have found that the solution is to make sure that the 'Power Manager' option is turned _ON_ in System > Preferences > Startup Applications. If I disable it, the screen goes into power saving mode after about 10 minutes.

So, you need power manager to run in the background in order to make sure that power saving doesn't work. I think.

---

### Post by cblanquer on 2011-01-02
I am just getting the same akward behaviour on my main PC (an Intel core2duo desktop with an ATI card running on Kubuntu 10.10) for the last couple of weeks. If I do not interact with the PC, for instance, listeningt o music on Amarok, watching a film on VLC or on a webbrowser, the screen gets dark after some minutes.
This seems indenpendent from the powersavings settings.

Could it be related to the default "drivers" for the ATI videocard, as 10.10 does not install the propietary software for the card ?

---

### Post by radar2020 on 2011-01-02
> I am just getting the same akward behaviour on my main PC (an Intel core2duo desktop with an ATI card running on Kubuntu 10.10) for the last couple of weeks. If I do not interact with the PC, for instance, listeningt o music on Amarok, watching a film on VLC or on a webbrowser, the screen gets dark after some minutes.
This seems indenpendent from the powersavings settings.

Could it be related to the default "drivers" for the ATI videocard, as 10.10 does not install the propietary software for the card ? 
I had this problem with kubuntu 10.4 also.  In my case it was an Energy Star (dpms) issue.

To find out if Energy Star is on/off, type in the terminal:
```
xset -q
```

Look at the bottom lines concerning DPMS Energy Star.
Is DPMS enabled?
What are the Standby, Suspend, Off settings? (Times are in seconds, )

To understand more about this & to change settings:
```
man xset
```

---

### Post by stinkeye on 2011-01-02
To add to radar2020 post, if xset -q shows DPMS is Enabled
add this to startup applications.
```
xset -dpms
```

---

### Post by mc4man on 2011-09-25
> **stinkeye said:**
> To add to radar2020 post, if xset -q shows DPMS is Enabled
add this to startup applications.
```
xset -dpms
```
didn't know about xset - so use a section to xorg.conf to prevent the DPMS blanking 
Actually like this better, can do per session (or add a startup to default to off, then enable as desired (xset dpms

---

