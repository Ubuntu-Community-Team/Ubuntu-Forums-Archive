---
title: "Can't play games...???"
date: 2011-03-21
forum: General Help
---

### Post by robertcoulson on 2011-03-21
Since installing the last update for Ubuntu 10.10, I can not play SuperTuxKart, SuperTux, Secret Maryo Chronicles, etc.etc....Has anyone else had the same problem...???
Robert

---

### Post by Rhubarb on 2011-03-21
I take it the last update you had contained a Linux kernel update.
I had a similar problem too.
It's easily enough to fix up.

If you've got an nvidia card (or maybe you are using the proprietary ati video drivers), then you'll need to re-install the proprietary video drivers so you can play games again.

Easiest way would be to run the "Additional Drivers" application in System --> Administration
Then select the video driver you want to install.

You'll probably need to reboot for the change to be made.
Then you should be able to start playing games again :D

---

### Post by robertcoulson on 2011-03-21
Wish it were that easy...see attachment
Robert

---

### Post by Rhubarb on 2011-03-21
Tell us what video card / integrated video you have, and we may be able to help you out.

If you have nVidia graphics, you may need to manually install the proprietary video drivers (which is what I currently do, and like you, nothing appears in the "Additional Drivers" application.

I have little experience with amd/ati video.

---

### Post by mastablasta on 2011-03-22
that't the good thing about stable systems like Ubuntu at one point they work nicely and then they don't anymore after security updates...
 
Note in this case they did some "fixes" on opensource radeon drivers and as a result plenty users reported flash not working propperly (inlcuding me) eventhough it worked nicelly before. so maybe this coul dbe the face. i haven't tried playing any games yet...

---

### Post by robertcoulson on 2011-03-22
Well rhubarb.....My Acer Aspire has a "Intel HD Graphics" card....Also can not use "normal" or "extra" visual effect, I get a answer that you can see in the attachment.
Robert

---

### Post by Rhubarb on 2011-03-22
Ok, this means that it's unable to render any 3D stuff or video acceleration.
And hence can't play most games (Secret Maryo Chronicles uses video acceleration).

I don't have much familiarity with intel video.
You could try a few things which may help:
[LIST]
[*]See if there's any updates to install
[*]Load up a previous kernel and see if that lets you play your games again
[*]Try an internet search to see if this has happened to anyone else
[/LIST]

To load up a previous Linux kernel, you'll need to reboot your machine. Press and hold the shift key during boot and you'll be presented with the grub boot menu.
Use the cursor keys and go down to select the 3rd item from the top (it should be your previous linux kernel that you were using before the update, don't select the recovery ones).
Then you'll be back into ubuntu, if it works it's possible to delete the most-recent Linux kernel so you'll always boot into the older working kernel that's good for games.

---

