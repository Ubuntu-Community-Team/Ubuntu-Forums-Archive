---
title: "Brightness control in Ubuntu 10.04"
date: 2010-06-05
forum: General Help
---

### Post by Lyubo on 2010-06-05
Hey guys,

I am currently using Windows 7 but I would really like to install the new Ubuntu, what bothers me is that I tried using Ubuntu 9.04 few months ago and I had troubles changing the brightness (Toshiba L40). I have searched in the forum and it appears that there are quite some people with the same problems, of course fixes are offered but as at least some basic kernel knowledge is required I am in no position to follows the proposed steps. Since this is one of the determining factors whether to stay with Windows or go to Ubuntu I was wondering whether this problem is fixed in 10.04 or not?

P.S. I haven't tried messing with the kernel because I have only one laptop and I am afraid to lose the information on it.

Thanks in advance!

---

### Post by colorlessprism on 2010-06-05
im not sure what kind of brightness problems you have/had but,

i would download the iso:
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
and make a bootable USB or LiveCD (scroll down some for great instrictions with pictures). now boot your computer from the USB/CD, make sure to select the try without installing method. this will give you an idea on what works and what doesn't.

with my msi wind i had major brightness flickering issues on 9.10 and 10.04a. these issues were fixed with a bios update. search these  forums for great advice on BIOS updating and whether or not that would even fix you problems.

---

### Post by Lyubo on 2010-06-05
Well the problem was that I could not control the screen brightness which it was set to minimum/very low level. This means that during daytime its close to impossible to see anything. And thanks for the idea, I will try doing that and report back.

---

### Post by oleink on 2010-06-05
> **Lyubo said:**
> Well the problem was that I could not control the screen brightness which it was set to minimum/very low level. This means that during daytime its close to impossible to see anything. And thanks for the idea, I will try doing that and report back.

What did u do to try and change it?

---

### Post by Lyubo on 2010-06-05
> **oleink said:**
> What did u do to try and change it?

I tried adjusting the Brightness Level in the Power Management menu.

---

### Post by oleink on 2010-06-05
> **Lyubo said:**
> I tried adjusting the Brightness Level in the Power Management menu.

Did you try Fn+up arrow

---

### Post by Lyubo on 2010-06-06
> **oleink said:**
> Did you try Fn+up arrow

Yes I did try that, the problem is that the indicator/scale looks as if the brightness is set to maximum, but that is not the case. Also it is interesting to note that when I tried lowering the brightness, say 80% or even 40% nothing has changed. So my guess is I have no actual control of the brightness. 

Any suggestions ?

---

### Post by DarkRage4 on 2010-06-06
I did hear brightness problems with Toshiba laptops in general before, not sure if that's the case, since I do not now, nor have I ever had a brightness problem. I can not say if this was fixed in 10.04, all I can do is suggest getting a Live CD and seeing for yourself. If the problem still exists try one of the fixes (since its a Live CD, it should not affect your data at all). Just follow the fix step by step, you can even copy and paste if you need to go into the terminal.

---

### Post by oleink on 2010-06-07
> **Lyubo said:**
> Yes I did try that, the problem is that the indicator/scale looks as if the brightness is set to maximum, but that is not the case. Also it is interesting to note that when I tried lowering the brightness, say 80% or even 40% nothing has changed. So my guess is I have no actual control of the brightness. 

Any suggestions ?

Sorry that I do not have any suggestions but that is rather strange...

[https://bugs.launchpad.net/ubuntu/+bug/159255]("https://bugs.launchpad.net/ubuntu/+bug/159255")

Take a look at some of the responses to this bug report that may be somewhat helpful.

Hope that can help.  There are a lot of responses there

---

### Post by germanix on 2010-06-07
The following was true for Ubuntu 8.04, should still be valid and may help in your case if the problem still exist for you in 10.04:

Changing screen backlighting
If you’re using Ubuntu on a notebook computer, you should be able to alter the screen backlighting brightness using the notebook’s standard keyboard combination, as with Windows. If this doesn’t work, right- click a blank spot on the bar running across the top of the screen and select Add to Panel from the menu that appears. In the list that appears, select Brightness Applet and click the ADD button. This will add a new icon that, when clicked, presents a slider that will let you alter the degree of backlighting.

---

### Post by wilmor24 on 2010-06-07
> **Lyubo said:**
> Hey guys,

I am currently using Windows 7 but I would really like to install the new Ubuntu, what bothers me is that I tried using Ubuntu 9.04 few months ago and I had troubles changing the brightness (Toshiba L40). I have searched in the forum and it appears that there are quite some people with the same problems, of course fixes are offered but as at least some basic kernel knowledge is required I am in no position to follows the proposed steps. Since this is one of the determining factors whether to stay with Windows or go to Ubuntu I was wondering whether this problem is fixed in 10.04 or not?

P.S. I haven't tried messing with the kernel because I have only one laptop and I am afraid to lose the information on it.

Thanks in advance!

Have you tried setpci? (I use sudo setpci -s 00:02.00 F4.B=xx) xx refers to a hexadecimal value from 0 (brightest) to FF (no brightness at all)

---

### Post by wilmor24 on 2010-06-07
Also, 00:02.0 is specific to my VGA controller, use lspci to see what is the value for yours in case is not the same.

---

### Post by Lyubo on 2010-06-11
Guys, thanks for the responses I am going to try everything and report back.

---

### Post by oleink on 2010-06-11
> **Lyubo said:**
> Guys, thanks for the responses I am going to try everything and report back.

Any good news?

---

### Post by iaminlove on 2010-06-11
Pavilion dv6 2180

Ubuntu 10.04

something definitely wrong with brightness control

1. Fn + UP/DOWN   don't do anything (remains brighter than the sun)
2. Brightness applet

    This is weird. Took me many times to "get hold" of the scroll bar
    first it moved to the very left. Eventually it settled where the icon
    is.

    initial state as indicated by the scrollbar is "complete darkness"
    even though the screen is at its brightest.

    Drag the bar to the desired position (assuming you can) the brightness
    changes suddenly from   brightest to darkest than gradually the the level
    corresponding to the position of the scrollbar.


 It'd be nice to fix this. I don't know how.

 My eyes kind of hurts.

regards,

---

### Post by iaminlove on 2010-06-11
PS Avoid pressing the Fn + UP/DOWN after you have adjusted the brightness

     It resets to brightest level.



Your laptop might work differently.

---

### Post by iaminlove on 2010-06-12
In case, you have dv6, just set the default brightness level in power management to
a suitable value and then you don't have to adjust it.

---

### Post by VCoolio on 2010-06-12
Try [this](https://launchpad.net/redshift)

---

### Post by Lyubo on 2010-06-15
Hey guys,

Thanks for all the help but nothing seems to be working. As an answer to previous questions I am using laptop Toshiba L40 170, not a notebook, I do not use dv6 and when I tried the "sudo setpci -s 00:02.00 F4.B=xx" command I received a message saying that there is no such command. I googled it up and I found the same thing but without the "-s" component, tried that, didn't work. As for the last comment about expanding the maximum of the available brightness scale, that might not work because whatever I set as brightness percentage there is no actual change to the brightness itself. Im guessing the brightness is ok due to the fact that while I am on windows its fine, but its just that I cannot change it on ubuntu or ubuntu cant find my video driver or something. Someone suggested that I try "plsc" command or something like that for diagnostic purposes so I ended up doing a performace test and it appears that I do not have a vga1 ermm something ? :D Could this be the problem?

Again thanks for all the help and sorry for being such a noob :D

---

### Post by chudder on 2010-06-16
Yeah, I've used that fix with the slider, it's interesting I never had the problem until Karmic and now Lucid.  Is there anyway to get the Fn keys to work, I've downloaded toshutils and the like.  Still nothing.

---

