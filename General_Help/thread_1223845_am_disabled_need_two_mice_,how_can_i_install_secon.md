---
title: "am disabled need two mice ,how can i install second mouse"
date: 2009-07-26
forum: General Help
---

### Post by workshop1702 on 2009-07-26
hi i am disabled and need to use two mice i can get two working but they are using the same settings which is no good how can i install a second mouse with its own settings for buttons pointer speed etc. i can do this on windows in a few seconds but really dont have a clue how to do it on ubuntu. could some help please.

---

### Post by fragos on 2009-07-26
I use three cursor control mechanisms and all work interchangable. I have a mouse, a USB touchpad and a Wacom tablet. being different devices they each have individual drivers and setup. This may not help you much since you wish to use two mice. It does potentialy give you a backup approach. I select my cursor control based on what works best for each application. I've carpel tunnel and changing around is very helpful for me.

---

### Post by workshop1702 on 2009-07-28
just the same as me i have carpel tunnel and arthritis and i need to keep changing hand , i just cannot work out how to get each mouse settings to be independent of each other .
as i have them at the moment they booth work but are using the same settings ,i need to have them set differently how do i do this please.

---

### Post by earthpigg on 2009-07-28
hi,

google has told me that [it has been done before]("http://wearables.unisa.edu.au/mpx/?q=screenshots"), but i have thus far been unable to either set it up myself or find an easy how-to.... still looking, though.

this thread looks promising: [http://ubuntuforums.org/showthread.php?t=110945](http://ubuntuforums.org/showthread.php?t=110945)

---

### Post by Favux on 2009-07-28
Hi workshop1702 and earthpigg,

MPX is for using multiple input devices at the same time, which I don't think is what workshop1702 is asking for.  And it has yet to be integrated into Xserver.

You can apparently change the pointing device.
> You can check the XInput pointer status by using xsetpointer as below. The man page states that calling xsetpointer with the name of a particular device will set it as the primary pointing device.
So to see the pointing devices:
```
xsetpointer -l
```
And apparently you then use the name(s) to toggle the primary:
```
xsetpointer name
```
I haven't tried it so I'm not sure.

I'm going to guess you are in Jaunty.

But are you wanting the mice to behave differently with different settings?  But they end up with the same?  Maybe they're both using the same .fdi?  In that case you may have to construct a seperate .fdi for each mouse, if it's possible.  The xsetpointer list should give their HAL names.  Then in a terminal you can:
```
lshal>lshal.txt
```
Which will give you a txt file you can load into gedit.  Using find and the names you can find the relevant HAL sections for each mouse.  Then you can probably identify differences that will allow you to construct seperate match lines for the mice so they can be segregated to two seperate .fdi's.  Part of the problem will be identifying which .fdi is currently running the mice.  Because it seems like there are several mice .fdi's in the configuration .fdi's.

---

### Post by workshop1702 on 2009-07-28
yes this last reply looks interesting . i am no expert on linux yet ,i am slowly learning ,would it be possible for someone to give me step by step instructions on how to get the two mice working one is a logitech trachman wheel and the other is a larger trackball i need to set the speed the pointer moves on each diferently , it would also be good to be able to set specific functions on left and wright mouse buttons as required. i really would be most gratefull if somone could talk me through how to do this.

---

### Post by Favux on 2009-07-28
Hi workshop1702,

Hopefully some mouse .fdi guru will help you.

You could comb through your lshal to pull out the mouse sections.  You probably need them anyway.  Daunting because it's a huge output, but I've done for other things so it's possible.

Also some links showing folks making mouse .fdi's.  Where the .fdi's are located and some commands other than lshal to pull info. out:

[http://ubuntuforums.org/archive/index.php/t-1135001.html](http://ubuntuforums.org/archive/index.php/t-1135001.html)

[http://www.chineselinuxuniversity.net/articles/21232.shtml](http://www.chineselinuxuniversity.net/articles/21232.shtml)

[http://www.pubbs.net/samba/200904/59839/](http://www.pubbs.net/samba/200904/59839/)

Another way to go may be to let the .fdi control the trackball (if it works right) and try to configure the logitech through xorg.conf.  That may seperate the two out and let you customize the logitech.  Some older logitech threads:

[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

[http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)

---

### Post by workshop1702 on 2009-08-19
its so frustrating trying to get something like two mice working on linux , 
i could do thid on windows in seconds , maybe you can on linux but i just cannot find out how , i need a simple step by step guide on how to do this,PLEASE CAN SOMEONE HELP

---

### Post by Favux on 2009-08-21
Hi workshop1702,

Have you tried btnx/btnx-config?  It should be in Synaptic.

It can only handle one of your mice currently, but you should be able to configure that one the way you want.

Also see:  [http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/)

---

### Post by workshop1702 on 2010-05-22
have installed btnx-config however when i run it i get an error message 
error no code key file
btnx-config needs the file/etc/btnx/events to run . make sure you have installed btnx first and that the file exists.

has anyone any ideas what i need to do to sort this out

---

