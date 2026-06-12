---
title: "TouchPad Left Click is stuck. Requires replacement. Instead, I want to disable it."
date: 2010-03-23
forum: General Help
---

### Post by Bare Grizzly on 2010-03-23
What can I do to disable ONLY the LEFT touchpad button on my laptop?
 
Issues: Left Click sticks by itself randomly, this causes problems when using my USB mouse (such as permanent dragging, permanent highlighting, permanent inability to left click anything, the computer is pretty much dead to me unless I try to tab around), it also causes issues with the Tap to Click, and it also causes Ubuntu to not recognize my "Left Handed" mouse button set up after boot for ONLY the touchpad. On the USB mouse, buttons work swapped.
 
 Current solution: Left Handed Button Swap. Touch pad to click. Right touchpad button to right click. Sometimes I use my USB (which does recognize the swap). 
 
 This is the 3rd install of vanilla Ubuntu (tried it just in case). That's not the issue. 

This is a Dell Inspiron 6000. 

Ideally I want to just disable the left button on ONLY the touchpad, I don't want this to affect my USB mouse. I want to keep the right button touch pad working. And of course I want my mouse to work. But, actually, my ideal is to sacrifice the left button, use Tap to Click, and use the right mouse button for right clicking.

If I can't save the right click, can I disable both buttons? I'd rather not do that and get a more surgical solution.

---

### Post by Bare Grizzly on 2010-03-24
I didn't expect this to be a stumper of a question. :)

---

### Post by bobcollard on 2010-03-24
> **Bare Grizzly said:**
> I didn't expect this to be a stumper of a question. :)
Open Synaptic Package Manager and type in "gpointing" (without quotes)  You  are looking for an applet called gpointing-device-settings.  You can install it with Terminal if l you like. ```
sudo apt-get install gpointing-device-settings
```
Start it with Terminal ```
sudo gpointing-device-settings
```  or put it in your startup appllications.  You can disable touchpad with that.

---

### Post by 2hot6ft2 on 2010-03-24
I'm sure there's a config file somewhere you could edit to disable it but I don't know where it is. My solution would mean opening it up and either fixing it, disabling the contact for it (a piece of tape over the contact) or cutting the wire to it.

---

### Post by 2hot6ft2 on 2010-03-24
> **bobcollard said:**
> You can disable touchpad with that.
System > Preferences > Mouse > Touchpad tab you can disable the touchpad but the OP just wants to disable the left click button, not the whole touchpad.

---

### Post by bobcollard on 2010-03-24
> **2hot6ft2 said:**
> System > Preferences > Mouse > Touchpad tab you can disable the touchpad but the OP just wants to disable the left click button, not the whole touchpad.
I offered the only **solution** I know of. I make no apology for that.

---

### Post by James.Lazo on 2010-06-06
> **bobcollard said:**
> I offered the only **solution** I know of. I make no apology for that.

I think a caveat explaining this isn't the solution being **sought** is in order.

I'm also looking for a solution to disable the only left touchpad button for Kubuntu 10.04.

---

### Post by varunksl@gmail.com on 2012-03-21
> **Bare Grizzly said:**
> What can I do to disable ONLY the LEFT touchpad button on my laptop?
 
Issues: Left Click sticks by itself randomly, this causes problems when using my USB mouse (such as permanent dragging, permanent highlighting, permanent inability to left click anything, the computer is pretty much dead to me unless I try to tab around), it also causes issues with the Tap to Click, and it also causes Ubuntu to not recognize my &quot;Left Handed&quot; mouse button set up after boot for ONLY the touchpad. On the USB mouse, buttons work swapped.
 
 Current solution: Left Handed Button Swap. Touch pad to click. Right touchpad button to right click. Sometimes I use my USB (which does recognize the swap). 
 
 This is the 3rd install of vanilla Ubuntu (tried it just in case). That's not the issue. 

This is a Dell Inspiron 6000. 

Ideally I want to just disable the left button on ONLY the touchpad, I don't want this to affect my USB mouse. I want to keep the right button touch pad working. And of course I want my mouse to work. But, actually, my ideal is to sacrifice the left button, use Tap to Click, and use the right mouse button for right clicking.

If I can't save the right click, can I disable both buttons? I'd rather not do that and get a more surgical solution.

I have exact same problem. I used xinput with options list and set-button-map. However, trying to disable the left mouse button disables the touchpad tap-to-click too. any solutions?

---

### Post by overdrank on 2012-03-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

