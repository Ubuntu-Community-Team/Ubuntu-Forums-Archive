---
title: "General Advice for a Charity"
date: 2011-04-15
forum: General Help
---

### Post by LittleMacNoFat on 2011-04-15
Hi - hoping someone can help set us along the right path here. 

We would like to use a server on an internal network to do two key things:

1) play video footage with audio (lots of short clips) in a loop to a plasma screen;

2) continuously display a web page to a second plasma screen.

for (1) we want to be able to create clips at any time and store them on the server where they will be added to the list of available clips to play out. We also want to link to the same clips from a web site that will be running on the server, accessible only internally at this point (i.e. only available to users within the network).

for (2) we need to connect to an external service and use a second monitor to display the web page.

Challenges we see - 
[LIST]
[*]how to create the repository for the video clips and setting up a playback system to a specific monitor;
[*]how to use a second monitor to display different content.
[/LIST]

The server will be a relatively old HP Proliant DL140 which has a single video out... and we believe we can use a device like a Matrox DualHeadToGo to help get on to different screens.But, is there a better way?

As you may guess, we are completely new to this - we are able to do all of this using multiple desktop machines but we are setting up a new visitor centre and want to achieve it with the least amount of hardware possible. We are familiar with Macs, and use Windows a fair amount, but rarely delve into the world of Linux... any help you can give would be gratefully received!

Thanks (and apologies if this should be in a different forum - we're new here too).

---

### Post by d3v1150m471c on 2011-04-15
```

#!/bin/bash
# say the videos will always go to your ~/Video folder
# you could use cvlc in the following.
while true; do
 cvlc -f --play-and-exit ~/Videos/*
done

```as for two monitors and directing one thing to each. that's out of my range of knowhow...

---

### Post by LittleMacNoFat on 2011-04-15
Thanks for that - if I understand you correctly you suggest dropping all video clips into the ~/Video folder and using the script to cycle through them one at a time to play them back. Adding new clips won't be a problem because of the 'while true' loop in the script... all seems good to me.

I note you reference VLC - I am only slightly familiar with it, but will have a look at it in more detail... thanks!

---

### Post by d3v1150m471c on 2011-04-15
correct, or any folder of your choosing. you can modify the script to your needs and cvlc should just keep looping through whatever videos are in the folder. I wish i could help with the monitors but I use a laptop and it's nothing i ever ventured into. btw cvlc is the command line utility to vlc media player, but the -f option will launch fullscreen video.
```

# you can use either of these to gain more info on cvlc
man cvlc
cvlc --help

```

---

### Post by LittleMacNoFat on 2011-04-15
Thank you for the pointer - I've used the desktop version of VLC on a mac, so command line version is a bit new, but not too daunting, I'm pleased to say!

I think the monitor issue will be a bit harder to resolve - the server is more than 10M from the displays, so VGA won't be any use - I'm looking at using VGA/ethernet extenders, but am not sure of they run on Ubuntu. I appreciate your help thus far, hopefully someone else can help with the monitors

---

### Post by d3v1150m471c on 2011-04-15
btw, if you're going to be running the server soley on an LAN, you should consider samba, which will be more user friendly, and you could allow users to push or remove files from the video folder of your choosing. or setting up a secure ssh and/or ftp server to push the files to the folder. of course ftp and ssh aren't restricted to lan but can work just fine. ftp will probably be your best bet, as ssh is geared more toward remote shells. either way read up on the functionality and security for these applications.

---

### Post by sanderd17 on 2011-04-15
For the monitors: it will be better to have a graphical card with two exists instead of using the Matrox.

There are a lot of graphical cards that are cheaper and the support is better: with a graphical card, the OS knows that there are 2 screens. So when you choose "full-screen", the OS will only fill the current screen (I think this will not cause problems and Ubuntu will choose the sceen on which the terminal is). But if you use Matrox, the OS only sees one (big) screen and full-screen will not work.

For the distance, maybe you can try with a VGA cable, I see that vga cables up to 15m are sold. I have never tried it, but if you can return the cable, nothing is lost.

---

### Post by LittleMacNoFat on 2011-04-15
Samba sounds like a good idea - I was simply going to save out from the iMac onto the server hard drive as a network drive would normally work. On a Mac I have used SMB as a file protocol, which I believe is a variation of Samba, so this should seem familiar when I get to use it I hope.

Even at 15M the VGA connection will be an issue - one monitor is probably within that, but the other is nearer 20m away, and signal loss will probably be significant. 

I've not really used a server like this before - normally they are in a data centre off site doing web based stuff. Is it possible to fit a dual headed graphics card inside one? I guess they are actually only computers after all, so as long as they can accept PCI based cards then it should work. I would much prefer to use a graphics card and not the matrox device, but I think we'll still need to run VGA/Ethernet extenders given the distance. Quality loss should be pretty minimal with these.

The server is a rack mount 1U chassis - I'll need to check the spec, but it is a HP Proliant Dl140 from around 2007. It is now not needed as a web server and currently runs Ubuntu, which is why we are hoping to use it as it is - a software update or two and configure it for it's new role.

These are fantastic tips - really useful stuff, thanks!

---

