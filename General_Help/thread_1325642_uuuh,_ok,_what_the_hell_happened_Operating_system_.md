---
title: "uuuh, ok, what the hell happened? Operating system damaged."
date: 2009-11-13
forum: General Help
---

### Post by Dead Die Jazz on 2009-11-13
About a thousand reboots ago, I shutdown a virtual image of winxp sp3 in VMware workstation 7. However, it got to a blue screen...

Then my entire operating system starting going screwy. My music starting sounding somewhere between a broken record, a damaged tape and a scratched disk. The actual audio, as far as I could determine, was fine, but 9.10 was struggling with gettting it to the audio.

Then all my programs started fading in and out of gray, and so I decided that it was time for a reboot. So eventually I managed to tell linux to reboot, and it started to do so. Only all that seemed to do was get rid of the GUI and throw me into the command line. so I typed reboot, and then it did something, I forget what, and just stayed there. Not sure if it hung or not, I forgot to see if numlock or capslock worked, but after 5-10 minutes, I gave up and manually forced a shutodown with the power button.

I'm not sure what happened, but when I restarted I soon discovered that my BIOS had reverted to an earlier image, so I fixed that, then I discovered that for some reason it was skipping the first two options in my boot order, and going straght to my USB-HDD, as it was now booting my old (broken) 9.04 install. So I shutdown the system, unplugged that, restarted, and got into grub2, and selected the 9.10 install, which upon booting I discovered that it was actually an old forsaken install that I was no longer using. So I shutdown and unplugged all my sata drives except for the harddrive that has my current 9.10 install. Upon restarting, I discovered that the reason I couldn't find my lastest install was that it had been idenfied by grub as generic linux. So I booted into that, and discovered that there was something seriously wrong with my audio, as it worked, but sounded absolutely awful, so after much playing around with them, I reinstalled them, and that seems to have fixed that. However, now one of my 2 autoloading NTFS drives wasn't working (ironically, the one which has my music), and since I haven't figured out how to make it so I don't have to type my password every time I mount an internal drive, this is kinda a big thing. So after much more playing around, I removed the automount entries in f-whatever it is, and reinstalled my NTFS programs a couple of times. That seems to have been a brilliant move, as now gnome can't load my desktop (or something called ICE.authority or something. Within Temptation fans will be amused to know that my login is queen :P), unless I use the recovery options (which is why I can type this). I would normally troubleshoot this the google way, but the minute I finish typing this I'm off to an exam, and then I've got another exam the day after next, so I really need this fixed yesterday. I've run all the recovery options, even make space, and it hasn't seem to have fixed it. If it helps, I also thought I'd try telling ubuntu to send me straight to the desktop without asking for a login, in the last time I access my OS without using recovery options.

As a bonus question, what the heck do I do when I get thrown into 'choose an application'. Because as awesome as thunderbird 3 is, the fact that it can't find firefox, and I don't know how to tell it, is really annoying.

---

