---
title: "Running custom commands on startup"
date: 2012-07-14
forum: General Help
---

### Post by BastardNamban on 2012-07-14
I have a simple problem (?) I can't seem to find an answer to.

My laptop's touchpad has shorted out, and in Ubuntu, it does weird click holding things, instead of being ignored as windows does with it on my second partition.

At every boot, I have to immediately launch terminal and type in:

[xinput set-prop 12 "Device Enabled" 0] or
[xinput set-prop 13 "Device Enabled" 0]  

to manually shutoff my touchpad, every time. If I don't do it quick enough, ubuntu freezes my mouse click on everything perpetually it moves over, working becomes impossible. 
The reason for the 12 or 13 is another part of the difficulty: depending on when I turn on my usb mouse, it shifts. I wish I could run both commands automatically upon booting linux, without having to do it myself,
 as it's become a real pain in the ***, but I am still a relative beginner, and cannot find anything understandable to help me assign custom commands on startup. I used to be much more savvy,
but it's been over a year since I really did anything technical with my linux setup, and I've lost my tech knowledge of how to approach anything.

Can anyone help? I'm sorry I'm such a moron. I just can't stand this anymore!

(and yes, I know I could manually disconnect the touchpad by opening the laptop up, but this is my only computer, and I can't afford another for a couple years if I break it! This one's a Dell inspiron 9300 thats already 7 years old)

---

### Post by OM55 on 2012-07-14
Hi,

You can create a text file with those lines in it in your home directory. Then change tye permissions to allow execution as a program. You can do that by right clicking on the file and 'Permissions' tab, or in command line:

chmod 766 <file name>

Just open terminal window and type: 

gnome-session-properties

This will launch the "Startup Applications" program. Just add the file name you created above, and it should run every time you log in.

---

### Post by BastardNamban on 2012-07-14
That was simple- and it worked! Rebooted, and touchpad is off.
Put in both commands and my usb mouse still works, touchpad off.

I've been doing that manually for months until you helped me- 
Thank you so much!

---

### Post by OM55 on 2012-07-14
Glad I was able to help.
But keep in mind that this is just like an Advil for a recurrent headache: You may want to solve the underlying problem...

As for the changing device number of the touchpad, this number is assigned during boot by the x-server, so if you have additional deices that are listed first, the number will change between boots.

Anyway, at least for now you have a bit less hassle every time you boot!

---

### Post by BastardNamban on 2012-07-28
....And we're back to the same old ********.

Laptop started the same tired routine of fritzing the mouse clicking again, DESPITE having an unaltered custom command that did indeed shut it off for a week or so.

I double checked the gnome-sessions-properties list of startup commands- my custom script of 2 lines that initially worked for a week or so is still there, the computer just seems to ignore it now!

I have to enter the same commands, manually, again, and that fixes it.
So the commands work, that's not the problem. What I can't understand is why ubuntu is now choosing to IGNORE the commands on startup. They are the same 2 commands.

I am going nuts and ready to throw this ******* computer out my window! I've had it. Please, any ideas on what is wrong now?

---

