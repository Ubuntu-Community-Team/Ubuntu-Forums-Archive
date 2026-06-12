---
title: "mouse too fast"
date: 2010-04-18
forum: General Help
---

### Post by BackwardsDown on 2010-04-18
I've got a logitech (I think the MX1000) mouse but after sliding the acceleration sliders all the way to the left I think it's still too fast. I've tried to use the logitech-applet package but it does not seem to help.

Does anyone know another solution?

---

### Post by bobcollard on 2010-04-18
> **BackwardsDown said:**
> I've got a logitech (I think the MX1000) mouse but after sliding the acceleration sliders all the way to the left I think it's still too fast. I've tried to use the logitech-applet package but it does not seem to help.

Does anyone know another solution?
Try gpointing-device-settings you will find it in Synaptic Package Manager or you can install it from Terminal.  It seems to be more accurate to me.  You can open it with "Run Program" (Alt F2) or put it in your startup applications or run it in Terminal with
```
sudo gpointing-device-settings
```

---

### Post by Revolutionary101 on 2010-04-18
Go to System>Preferences>Mouse.

When the window opens up you will be able to control the pointer speed and acceleration.

I hope this helps.

---

### Post by Pyrosopher on 2012-03-04
I've just had this problem and it was a real struggle to solve. Got there in the end with this:

[https://wiki.archlinux.org/index.php/Mouse_acceleration](https://wiki.archlinux.org/index.php/Mouse_acceleration)

and the good folks at the xorg IRC channel.

The solution has two main parts. 

1) Find the amount the amount by which the mouse needs to be slowed.

2) Make the change persistent.

**Task 1: Putting the brakes on**

Plug in your over-zealous mouse, fire up a terminal and give it:

```
xinput -list
```You should be able to spot your mouse in this list. Copy the text description. 

Now  we know what it's called we can tell it to slow down. I was using a  Genius wireless mouse, so this is the command I used (where the contents  of the first set of inverted commas is what I copied at the previous  step):

```
xinput set-prop "Genius 2.4G Wireless Mouse" "Device Accel Constant Deceleration" 7
```The  7 is the factor the mouse is slowed by. The effect is immediate, so  have a play with the mouse. If it is still too fast or you have  over-shot, simply press the up-arrow in the terminal to bring up the  previous command to save typing and change the number at the end. You  might put a double-figure value in it first which will have a large  effect on the speed to check that you've got the command in correctly.

After some trial and error you should have your lucky number.

This  change is only good for your current session, if you're happy with that  or you are ok with entering the command every time you use the mouse,  stop here.
[B]
Task 2: Locking down the brakes[/B]

I won't do this  all in the terminal to make it easier to cut and paste. First off, open  a new text file and drop in the device description we copied in Task 1,  we'll be needing it and you may use your clipboard for other things in  the meantime.

Open a file manager with root privileges

```
sudo nautilus
```Navigate to /etc/X11/

Create folder called: 
```
xorg.conf.d
```Open the folder and create a file called:
```
50-mouse-deceleration.conf
```Paste in the following:
```
Section "InputClass"
     Identifier   "geniusmouse"
     MatchProduct "Genius 2.4G Wireless Mouse"
     Option       "ConstantDeceleration" "7"
EndSection
```The identifier should be something you would recognise as your mouse.

For  MatchProduct, paste in the line you safely stored in a text window  earlier, don't forget the inverted commas. This line makes it so the  deceleration is only applied to your problem mouse. In Task 1 we could  have used the ID instead of this text description, however the ID is  assigned in each session and can change. Therefore we have to use the  text description which isn't going to change.

In the Option  line,"7" was the magic number that got the mouse to the right speed in  Task 1. Again make sure you have all your inverted commas in the right  place. First time around I didn't have inverted commas around the 7 and  Ubuntu wouldn't boot. So, make sure that you've got everything right.

Save and close all the open windows. That should be that. Whenever you plug in your mouse it should be at the right speed.

If this has been helpful, please say!

---

### Post by gladgrind on 2012-08-03
Thank you. That did the trick. I was beginning to think that I would never be able to use a wireless mouse in Ubuntu.

---

### Post by BurningPants on 2012-11-23
Worked a treat for my Logitech M510 mouse, cheers dude:)

---

