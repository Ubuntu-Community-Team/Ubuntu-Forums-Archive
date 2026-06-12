---
title: "Widescreen monitor appearing as 4:3 ?"
date: 2010-03-11
forum: General Help
---

### Post by GreenDance on 2010-03-11
Hi, I have a widescreen monitor, but it's looking as if the settings are appearing as 4:3, the screen is stretched, my display settings are 1024*768.

please can anyone help, thanks,

---

### Post by swoll1980 on 2010-03-11
> **GreenDance said:**
> Hi, I have a widescreen monitor, but it's looking as if the settings are appearing as 4:3, the screen is stretched, my display settings are 1024*768.

please can anyone help, thanks,

1024x768 is a 4:3 screen size. This is why it looks stretched, because it is. Find out what the native resolution of your display is, and use that.

---

### Post by GreenDance on 2010-03-11
> **swoll1980 said:**
> 1024x768 is a 4:3 screen size. This is why it looks stretched, because it is. Find out what the native resolution of your display is, and use that.

it's an acer monitor model: al1603w

---

### Post by swoll1980 on 2010-03-11
> **GreenDance said:**
> it's an acer monitor model: al1603w

Google the model, and find out what it's native resolution is.

---

### Post by GreenDance on 2010-03-11
> **swoll1980 said:**
> Google the model, and find out what it's native resolution is.

this doesn't seem right, my display looked better on windows vista (before i made the change to linux/ubuntu)

---

### Post by Post Monkeh on 2010-03-11
> **GreenDance said:**
> this doesn't seem right, my display looked better on windows vista (before i made the change to linux/ubuntu)

probably because you had it set to a widescreen resolution (like the 1400 * 900 i have mine set to)

also, if you have a wall[paper that isn't widescreen, and try to stretch it to fit a widescreen, it'll look awful no matter what program is stretching it.

---

### Post by swoll1980 on 2010-03-11
> **GreenDance said:**
> this doesn't seem right, my display looked better on windows vista (before i made the change to linux/ubuntu)

If your using a 1024x768 resolution on a widescreen display, it's going to look like crap. The only way to fix this, is to find the native resolution, and use that. I'm trying to help you, but you have to help yourself too. I'm not going to do your Google searches for you.

---

### Post by GreenDance on 2010-03-11
> **swoll1980 said:**
> If your using a 1024x768 resolution on a widescreen display, it's going to look like crap. The only way to fix this, is to find the native resolution, and use that. I'm trying to help you, but you have to help yourself too. I'm not going to do your Google searches for you.

Sorry I forgot to say I found the native resolution, it looks crap

---

### Post by Grenage on 2010-03-11
And that resolution was?

---

### Post by GreenDance on 2010-03-11
> **grenage said:**
> and that resolution was?

1360*768

---

### Post by swoll1980 on 2010-03-11
> **GreenDance said:**
> Sorry I forgot to say I found the native resolution, it looks crap

What kind of video card do you have?

---

### Post by GreenDance on 2010-03-11
> **swoll1980 said:**
> What kind of video card do you have?

it;s built on-board

---

### Post by Grenage on 2010-03-11
I would have thought 1366x768 bit I guess it wouldn't make much diff.  How does it look "crap", you're going to need to elaborate if you want help.

You'll also need to tell us which GFX card, not what type.

---

### Post by Post Monkeh on 2010-03-11
> **GreenDance said:**
> Sorry I forgot to say I found the native resolution, it looks crap

what was it?

and make sure your wallpaper is a widescreen wallpaper, otherwise you'll be getting foxy brown and stretching her out to the size of roy chubby brown, and that will never look good

---

### Post by swoll1980 on 2010-03-11
Make sure the refresh rate is right too. It will look blurred, and strain your eyes if it is set to the wrong frequency.

---

### Post by GreenDance on 2010-03-11
Hi, sorry for the delay, when I set the screen size to 1366*768, the desktop goes off the screen, the font looks a bit weird, but a google search said it's the correct resolution, i don't know how to find out what gfx card i have.

---

### Post by Post Monkeh on 2010-03-11
> **GreenDance said:**
> Hi, sorry for the delay, when I set the screen size to 1366*768, the desktop goes off the screen, the font looks a bit weird, but a google search said it's the correct resolution, i don't know how to find out what gfx card i have.

hmm, i don't know if it's your graphics card or your monitor.

try a resolution of 1400 * 900 if it's there. that's the same as my widescreen resolution on both my computers and it works fine.

you should be able to see what kind of graphics card you have by going into the terminal and typing 

lspci | grep Display


there may also be an option in your monitor menu for it to reconfigure itself - you should be able to get  into it by pressing buttons on the monitor itself, this menu has nothing to do with the computer connected to your monitor.

---

### Post by GreenDance on 2010-03-12
> **Post Monkeh said:**
> hmm, i don't know if it's your graphics card or your monitor.

try a resolution of 1400 * 900 if it's there. that's the same as my widescreen resolution on both my computers and it works fine.

you should be able to see what kind of graphics card you have by going into the terminal and typing 

lspci | grep Display


there may also be an option in your monitor menu for it to reconfigure itself - you should be able to get  into it by pressing buttons on the monitor itself, this menu has nothing to do with the computer connected to your monitor.

Hi, 1366*768 is the highest it will let me go, but the desktop goes off the screen about 20%, lspci says nVidia Corporation nForce 630i

---

### Post by Post Monkeh on 2010-03-12
> **GreenDance said:**
> Hi, 1366*768 is the highest it will let me go, but the desktop goes off the screen about 20%, lspci says nVidia Corporation nForce 630i

i have an ati card so don't know too much about the nvidia drivers, but from what i hear they're better than the ati ones.

go to system > administration > hardware drivers and see if you can install the proprietary driver for your video card, that might help.

---

