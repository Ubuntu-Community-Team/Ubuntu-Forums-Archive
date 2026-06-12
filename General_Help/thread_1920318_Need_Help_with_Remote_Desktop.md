---
title: "Need Help with Remote Desktop"
date: 2012-02-04
forum: General Help
---

### Post by Iggy64 on 2012-02-04
I am new to Linux (2 weeks).  I have installed Ubuntu 11.10 on a laptop.  I have the Unity, GNOME, and Xubuntu environments all available.  

I used to run Win XP on my laptop, and regularly connected it wirelessly to my Win XP desktop, to run its apps and to share files.  Now that I have switched the laptop to Ubuntu, I have not found a complete solution for remote desktop to the desktop PC.

First I tried the built-in Remote Desktop, from the GUI, as well as from the Terminal.  I could not find a suitable combination of preferences/commands to make everything work.  I could easily connect to the desktop XP machine, but:
a) I could not see the entire screen of the XP machine; the bottom taskbar was always cut off (offscreen), no matter what resolution I chose.
b) I could not find any way to transfer files from one machine to the other.  I could not share a local drive, not could I get the clipboards to synch.

Next I tried Remmina.  With this, I was able to share local (laptop) drives with the desktop machine.  And I was able to get a full-screen view of the desktop's video (including the Windows bottom taskbar).  However, the image on my laptop was extremely grainy, and the colors were a bit distorted.  I tried various resolution and quality settings, with no effect on the poor image quality.

In short, I want to be able to:
- Control my desktop XP machine from my Ubuntu laptop
- Transfer files between the two
- Have a decent image to look at.

As a complete noob, I will likely find the answer eventually by hacking around on my own.  But I have gotten pretty frustrated, and thought I'd see if someone could kindly lend a hand.  If this has already been asked and answered in this forum, please forgive me; I tried my best in searching.  Please point me to the answer.

---

### Post by Iggy64 on 2012-02-04
I guess a more-streamlined question would be:

Can anyone help me get a better screen image in Remmina?

Remmina does everything I need, but the display is so grainy and color-distorted, it is somewhat difficult to read in some places.  I have it set at a normal 1024x768 resolution and have the Quality set to "Good" (although changing this setting seems to have no effect whatsoever).

Any suggestions would be very welcomed.  I am limping along with rdesktop, which provides a much nicer display.  But it doesn't allow file transfers (as far as I can tell), and it sounds like it's going to be dropped in favor of Remmina in upcoming Ubuntu releases.

Thanks!

---

### Post by ibod on 2012-02-06
> **Iggy64 said:**
> I guess a more-streamlined question would be:

Can anyone help me get a better screen image in Remmina?

Remmina does everything I need, but the display is so grainy and color-distorted, it is somewhat difficult to read in some places.  I have it set at a normal 1024x768 resolution and have the Quality set to "Good" (although changing this setting seems to have no effect whatsoever).

Any suggestions would be very welcomed.  I am limping along with rdesktop, which provides a much nicer display.  But it doesn't allow file transfers (as far as I can tell), and it sounds like it's going to be dropped in favor of Remmina in upcoming Ubuntu releases.

Thanks!

Hi Iggy64,

When you clicked on the "Create a new remote desktop file" icon (the page with the green +, at the top of the "Remmina Remote Desktop Client" window 
did you select the Basic Tab and set the "Colour Depth" there os a pop down allowing 256 colours (default) or 15, 16, or 24 bit colour. The more colour the slower the link so try them out starting with 15bit and work up.

Also there is a Quality pop down, where you can select Poor, Medium, Good or Best, again the better quality the slower the connection

Also look in the Advanced Tab. I have both horizontal and vertical scale sliders set all the way to the left.

When connected there are also some buttons at the top of the connected screen you could try them out. I have it set to scale the remote screen to fit in my window so there is no messing around scrolling all the time 

Hope this helps 

Ibod

P.S. One other thing i have noticed is that Remmina's process does not stop when the remmina window is closed.

I have to stop it manually 

If anyone has any comments on this I would be interested

---

### Post by Iggy64 on 2012-02-10
Thanks, ibod!

I needed help, and I got it from you.  I had been messing with the Resolution setting and the Quality setting, without much success.  I didn't even suspect that the color depth would make so much difference in the sharpness and clarity of the image.  Boy, it sure does.  Now I have a really good looking image, without even having to max out the settings.

And fussing with the toolbar buttons on top of the Reminna window was very useful, too.  I learned how to display only the part of the remote desktop I wanted -- including full remote screen view, which I sometimes need.

I very much appreciate your help on this.  I might have given up on Reminna and wasted a bunch of time looking for some other solution.

I'm going to check out your observation of the need to manually close Reminna, and I'll let you know whether I do, and if I learn any workaround for that.

Again, thanks!

---

