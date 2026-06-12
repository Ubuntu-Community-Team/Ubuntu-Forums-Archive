---
title: "Frozen Touchpad/Mouse control...Help!"
date: 2012-02-14
forum: General Help
---

### Post by oxf on 2012-02-14
Up until now I have had a flawlessly working installation of Maverick on my Acer Aspire One. Until last night that was...!

The screen greyed out and everything froze up. I managed to get to a terminal and shut down. Upon rebooting everything apears normal Except the touchpad mouse in non functional and the arrow is stuck in the centre of the screen. This happens every time I reboot it.

What also concerns me is this. I dont have the Live USB with me as I'm away from home but I do have a Live USB with Lubuntu on it. I tried booting from that and the same problem exists, i.e non functioninf touchpad.

I can move around the desk top with the up/down/left/right arrow keys. Can anyone tell me how to get into the upper panel with the arrow keys??

One other thing that may be related? when I drop to terminal I get a message something like "CPU encountered lack of security it was expecting.. check bios for further info"

Anyone have any ideas how to proceed/diagnose this issue as I'm dead in the water until I fix this? As I said abouve I have some limited fuctionality with arrow keys.

Thanks..
Katya

---

### Post by josephmills on 2012-02-14
> **oxf said:**
> Up until now I have had a flawlessly working installation of Maverick on my Acer Aspire One. Until last night that was...!

The screen greyed out and everything froze up. I managed to get to a terminal and shut down. Upon rebooting everything apears normal Except the touchpad mouse in non functional and the arrow is stuck in the centre of the screen. This happens every time I reboot it.

What also concerns me is this. I dont have the Live USB with me as I'm away from home but I do have a Live USB with Lubuntu on it. I tried booting from that and the same problem exists, i.e non functioninf touchpad.

I can move around the desk top with the up/down/left/right arrow keys. Can anyone tell me how to get into the upper panel with the arrow keys??

One other thing that may be related? when I drop to terminal I get a message something like "CPU encountered lack of security it was expecting.. check bios for further info"

Anyone have any ideas how to proceed/diagnose this issue as I'm dead in the water until I fix this? As I said abouve I have some limited fuctionality with arrow keys.

Thanks..
Katya


Hi there have you had a look at 
[http://blip.tv/ubuntu-switcher/lubuntu-screencast-touchpad-configuration-4897390](http://blip.tv/ubuntu-switcher/lubuntu-screencast-touchpad-configuration-4897390)

the thing when you start up seems to be in the bios its-self but I could be wrong I would look in the bios under security or something to that nature 
hope this helps

---

### Post by oxf on 2012-02-14
Thanks! Thats useful, I ddin't know that existed.
When I enter "synclient -l" it says "unable to connect to xserver" 

But yes I suspect this might be something to do with the Bios. When I drop to terminal I get two messages:

1: "Your CPU appears to be lacking expected security protections..please check BIOS sttings or run   " /usr/bin/check-bios-nx"

2: when I run that I get this msg:
"CPU sas NX capabilities but is unable to use these features because BIOS is configured to disable the capability"

I went into bios and I see no reference to "NX" or anything like that?

This may/may not be connected to my original touchpad pointer issue since evrything was fine and perfect until it suddently froze last night
:confused:

Katya

---

### Post by josephmills on 2012-02-14
ummm. that is kinda crazy did you watch the video all the way ? there is a gui front end for the touchpad  at the end of the video. 

could you open your terminal and type in 

```
dmesg
``` and paste here PLEASE GO TROUGH AND TAKE OUT IPADDRESS AND MAC ADDRESS thanks

---

### Post by oxf on 2012-02-14
> **josephmills said:**
> ummm. that is kinda crazy did you watch the video all the way ? there is a gui front end for the touchpad  at the end of the video. 

could you open your terminal and type in 

```
dmesg
``` and paste here PLEASE GO TROUGH AND TAKE OUT IPADDRESS AND MAC ADDRESS thanks

Yes I did and yes it is crazy! I havent installed the GUI yet because I can get the arrow keys to let me into the upper/lower panels yet (maybe theres a trick to that?) I can only move around the desk top. I don't get the bios error since I can't see NX listed in the security etc.

anyways..
"dmesg" gives a very long output as you know. I'm trying to think if theres a way of transfering it to this other PC I'm using.

---

### Post by Bromden on 2012-02-14
Try this script to unlock the TouchPad:

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

Just copy and paste into the terminal.

---

### Post by oxf on 2012-02-14
@JosephMills
@Bromden

Thank you both for your help! I have now resolved it I think!

I was unable to list dmesg because the problem laptop was not the one I was using to post to this forum (maybe there's a way of outputting from the shell on to a flash drive, I don't know?)

Anyway Bromden I tried your sugestion but can't say if that was successful because once had gone into the shell I did not know how to return to the desktop snd see if the touchpad was freed or not. So had to "sudo halt" and then reboot. Then it was still locked up.

I'm not quite sure what/why resolved this. I was trying to get access to the upper panel menus via the arrow keys which at that point I couldn't. I think I hit either ctrl or Fn + F10 (or maybe F11) at which point a empty dialog opened and I noticed the cursor/arrow was now functional.

I rebooted several times and all was fine. I did manage to lock the touchpad again somewhere around the F10/F11 keys but it seems that Alt+F7 imediately unlocks it!

Why tis all happened I don't know but now all is working and I am posting from the said laptop so I am very very happy :D

Thanks both for trying to help!

Katya

---

