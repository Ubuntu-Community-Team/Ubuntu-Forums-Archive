---
title: "I bought a new computer &amp; can't install ubuntu?"
date: 2012-04-03
forum: General Help
---

### Post by onlychevys on 2012-04-03
I can't install on this thing for nothing! This is an Hp Pavilion, model#p6-2133w. Everything goes great until it starts installing files & then I loose video. This machine don't have the older type video connection, it is DVI-D. I want & need Ubuntu! Please help!

---

### Post by bfmetcalf on 2012-04-03
Have you tried running the live cd?  If that plays, it may be something as simple as a driver that needs to be installed.

---

### Post by onlychevys on 2012-04-03
> **bfmetcalf said:**
> Have you tried running the live cd?  If that plays, it may be something as simple as a driver that needs to be installed.

I tried wubi, live cd and every version of Ubuntu starting from 10.04. How would you install a driver when on a live cd, there is no option for that?

---

### Post by bfmetcalf on 2012-04-03
And none of them work?

I didn't see anything real out of the ordinary on that computer on the HP website.  What graphics card do you have?

---

### Post by onlychevys on 2012-04-03
If something worked would I be here asking how to fix this? I will figure this out but some help from someone would be great. I get no video at all on any type of install.

---

### Post by Rodney9 on 2012-04-03
To load drivers for the Live CD see this 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

F4. Modes. Use this option when a specific driver must be loaded to allow installation or booting to the LiveCD Desktop. Once Ubuntu is installed or booted, the user can permanently install the required drivers. 



Rodney

---

### Post by onlychevys on 2012-04-03
Not sure what card I have, I got this computer new a few days ago. Funny thing is I can boot to puppy linux with no problem. However puppy loads all in ram mem.

---

### Post by onlychevys on 2012-04-03
> **Rodney9 said:**
> To load drivers for the Live CD see this 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

F4. Modes. Use this option when a specific driver must be loaded to allow installation or booting to the LiveCD Desktop. Once Ubuntu is installed or booted, the user can permanently install the required drivers. 



Rodney
Thank you, I think this might just get me up and running!!

---

### Post by Erik1984 on 2012-04-03
Have you tried the boot option nomodeset? See reply of Rodney9

---

### Post by onlychevys on 2012-04-04
I boot to the black screen that says try without installing, install, etc. It don't matter witch I choose, as soon as it starts loading my monitor says no signal? I waited on try without installing until it fully loaded but still no video. There is no way to get to ant help screens. Linux Mint and Kubuntu does the same thing. Puppy linux boots right up no problem but I need a full install.

---

### Post by Erik1984 on 2012-04-04
So you have tried the boot option called "nomodeset" ?

---

### Post by onlychevys on 2012-04-08
This is a new computer, an HP Pavilion p6 series model# p6-2133w.
Quad core w/8 gig's of ram running Win7. I can install Ubuntu 11.04 
and get everything going until I let it update video driver. Then all I get is a black screen. I can not even get 11.10 to boot. I installed 11.04 and upgraded to 11.10 and rebooted right to the black screen again. Full install not the wubi thing.I've really become attached to Ubuntu and would replace windows all together other than a few programs that wine won't fix. I was even getting used to Unity and starting to like it, but on this new faster computer Ubuntu says I don't have enough hardware to run it LOL.
I tried Kubuntu, Linux Mint,etc. Any help would be great. Oh, and I can not watch any video like youtube  etc.
WTF, I thought Ubuntu had good support? I'll check back tomorrow!

---

### Post by onlychevys on 2012-04-08
I don't know what  "nomodeset" is. I can't do nothing at all!!!!!! All I see is a black screen.

---

### Post by utnubuuser on 2012-04-08
i think Puppy uses the VESA driver, which as far as I know, is as generic as can be.

Isn't there a way to force VESA when loading the live cd? When you get to the screen that says Intall or Try Ubuntu, does pressing F4 or F6, (I think the kernel options can be changed using F6), do anything, or are you already stuck with a black screen at this point?

Normally, when you press F4 or F6, an input window showing the current kernel parameters opens and you can make changes to that line...  at least that's how it used to work. I haven't had to access those options in ages.

Oh, and you might be able to disable any onboard video card through your BIOS...

---

### Post by oldfred on 2012-04-08
Did you follow the instructions in post #4 by Rodney9? But it may be f6 not f4.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Previously posted in post #4 - shows boot screens and f keys to add options like nomodeset from liveCD.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by oldfred on 2012-04-08
Threads merged.

Please do not start another thread on the same topic. We are all volunteers here and need to see others responses.

---

### Post by onlychevys on 2012-04-11
> **oldfred said:**
> Threads merged.

Please do not start another thread on the same topic. We are all volunteers here and need to see others responses.

I managed to get Ubuntu 10.04lts working as long as I don't update anything to do with video.If I do I'm right back to black. I've created another partition to play with until this is figured out because I'm tired of re-installing. 
As for now, no this was not fixed, I'm using Ubuntu on a different machine for the most part and I've had enough messing with it.
Edit: As for trying to install a more up to date Ubuntu version, Boot to bios, start loading cd, BLACK SCREEN.
No option to hit any keys, and it don't matter what key combo you might hit. Nothing but BLACK SCREEN!
I love Ubuntu, I know my way around pretty good and can even write some Android apps. I really need the Android sdk and Java up and going smooth on this machine, which I have now, just on an older version of Ubuntu. 
I'm sorry for starting other thread but sold old machine & just backed up data and kind of panicked. I figured installing on this thing would be a breeze!  LOL

---

### Post by onlychevys on 2012-04-13
How would I go about finding the right driver? It don't matter if I use the system suggested proprietary driver or not. I managed to get Ubuntu 11.04 running but will not run Unity.

---

### Post by RJARRRPCGP on 2012-04-13
> **onlychevys said:**
> I boot to the black screen that says try without installing, install, etc. It don't matter witch I choose, as soon as it starts loading my monitor says no signal? 

Looks like the graphics hardware is too new.(The X.Org of Oneiric Ocelot don't support the graphics) Looks like you must wait for Precise Pangolin. Sorry.

---

### Post by onlychevys on 2012-04-13
OK!!!!! 
I found a working up to date driver. Now I just need to learn how to use this driver on a fresh install or should I upgrade? Or maybe leave things alone lol. I would love to upgrade to the newest 12.whatever because it is an LTS version. I'm on 11.04 now, would I have to upgrade to 11.10 & then again? By the way, this computer is new but I bought it at freakin Walmart on sale & as far as hardware it isn't that new. Only to me not technology.

---

### Post by pqwoerituytrueiwoq on 2012-04-13
you probably need fglrx 8.960
i have a a6-3500 next to me that driver works great in 2d mode (no effects)
if you start running compiz performance takes a huge hit (like from 60fps to 11fps)
i have tried several desktop environments on it cinnamon,mate,unity,unity 2d,gnome, gnome classic, and gnome classic (no effects)
cinnamon gets really low fps regardless of if effects are on or not
unity gets low fps and so does gnome classic
mate (unable to test compiz thus far on this), unity 2d, and gnome classic no effects run very good
when i booted off the 12.04 daily cd the other day and installed it the screen did some flickering but it did not crash
if you get it installed and it does not boot to a GUI press crtl+alt+f1 and login the the tty and run [FONT=Courier New]sudo apt-get install fglrx [/FONT]
if you get a blank screen try using the other monitor cable till you can install fglrx
this is the daily for 12.04 you would want to use [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso)
keep in mind 12.04 is still in testing and will not be final for another 10 days

---

### Post by onlychevys on 2012-04-13
> **pqwoerituytrueiwoq said:**
> you probably need fglrx 8.960
i have a a6-3500 next to me that driver works great in 2d mode (no effects)
if you start running compiz performance takes a huge hit (like from 60fps to 11fps)
i have tried several desktop environments on it cinnamon,mate,unity,unity 2d,gnome, gnome classic, and gnome classic (no effects)
cinnamon gets really low fps regardless of if effects are on or not
unity gets low fps and so does gnome classic
mate (unable to test compiz thus far on this), unity 2d, and gnome classic no effects run very good
when i booted off the 12.04 daily cd the other day and installed it the screen did some flickering but it did not crash
if you get it installed and it does not boot to a GUI press crtl+alt+f1 and login the the tty and run [FONT=Courier New]sudo apt-get install fglrx [/FONT]
if you get a blank screen try using the other monitor cable till you can install fglrx
this is the daily for 12.04 you would want to use [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-amd64.iso)
keep in mind 12.04 is still in testing and will not be final for another 10 days

That is the driver I came up with, and I don't mind waiting a little while for the final of 12.04 to come out. Thank you so much, of all reply's on this post so far yours is the most precise, to the point and helpful. I'm sure I will have more questions soon & I sure hope your around to help. I'm gonna mark this as solved, it sure is nice to have so many people around to help & I hope I can help out in the near future as well.

---

### Post by pqwoerituytrueiwoq on 2012-04-13
> **onlychevys said:**
> That is the driver I came up with, and I don't mind waiting a little while for the final of 12.04 to come out. Thank you so much, of all reply's on this post so far yours is the most precise, to the point and helpful. I'm sure I will have more questions soon & I sure hope your around to help. I'm gonna mark this as solved, it sure is nice to have so many people around to help & I hope I can help out in the near future as well.
i just tried the latest daily the open source driver puts the proprietary one (fglrx) to shame!!!
using the DVI cable this time (last time i was using VGA) there is no flicking at all i can use graphic effects and get 60fps on hedgewars (gnome fallback and unity) i think cinnamon runs a tad slower but you only notice it if you look really hard and since your apu is a little better than the one i am using i doubt you will notice a thing
at this stage everything is just final testing only critical things (show stoppers) are getting done at this point

---

### Post by onlychevys on 2012-04-13
> **pqwoerituytrueiwoq said:**
> i just tried the latest daily the open source driver puts the proprietary one (fglrx) to shame!!!
using the DVI cable this time (last time i was using VGA) there is no flicking at all i can use graphic effects and get 60fps on hedgewars (gnome fallback and unity)
at this stage everything is just final testing only critical things (show stoppers) are getting done at this point

Don't get me wrong but Linux is %$#^!@$#^! hard! That said, I'm not running any proprietary drivers? I thought what I installed was but there are no proprietary drivers on this machine. I did a google search and this driver is working great. I tried to post this driver here and that did not work very well. It is a .run file= amd-driver-installer-12-2-x86.x86_64.run.

---

