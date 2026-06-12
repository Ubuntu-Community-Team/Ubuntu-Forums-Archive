---
title: "Reinstalling sound card driver"
date: 2006-02-21
forum: General Help
---

### Post by Mishal on 2006-02-21
Everything with ubuntu has been great EXCEPT my sound card. I have posted two separate topic begging for help regarding my non-working rear speakers and noone could help:cry: 

So I got desperate and tried to install OSS driver rather than use ALSA. When I tried to compile from source, not only did it get stuck due to dependency hell, it also broke my ALSA driver. Now I have no sound at all and all software that uses audio is telling me that sound card is not configured or installed.

WILL SOMEBODY PLEASE PLEASE PLEASE HELP ME OUT?!!?:cry: :cry: :cry: 

I am getting seriously desperate now. Surely I won't have to switch back to Windows because of such a petty problem? Surely SOMEONE knows a way out?

I have tried going to device manager but it won't allow me to do anything. HELP!!:cry:

---

### Post by akiro.yamamoto on 2006-02-21
What is is sound card?
Did you try using Synaptic to re-install the ALSA drivers?
Re-install alsa-base, alsa-utils, libasound2, libesd and linux-sound-base. 
I think those are all the drivers installed during system set-up.
You can also install alsa mixer GUI and try using that to get the rear speakers working.
Hope this helps you get your sound drivers back online.

---

### Post by Mishal on 2006-02-21
It's a AC97 VIA 8235.

I have tried reinstalling alsa and it didn't work but I will try again. I have no other choice, do I?:(

---

### Post by akiro.yamamoto on 2006-02-21
My card is a AC97 VIA 8237, I get some strange settings as well, The Volume for me is controlled by the PCM the Master slid control has no effect. ;)

---

### Post by Mishal on 2006-02-21
I tried to remove alsa-utils, libasound2, libesd and linux-sound-base and Synaptic tells me that ubuntu-desktop and gdm will be uninstalled too in the process. I can't do that, can I?:(

You can remove alsa-base without affectingother packages and as I said, I have already done that once without any benefit.

So, any other solution? :(:(

---

### Post by akiro.yamamoto on 2006-02-21
No don't un-install. Right click each package and choose Mark For Re-installation.
This way GDM etc should not be disturbed.

---

### Post by Mishal on 2006-02-21
Done. And it doesn't change the situation. I even rebooted just to be sure.

Thank you for having the patience anyway :)

Now can you suggest anything else? Like where to change .conf file or something? Or where to recompile the driver through the terminal or something like that? Surely SOMETHING can be done?

Hasn't ANYBODY faced this situation before? Am I the first one EVER in the history of Linux to have messed up his sound card driver? Am I the first one EVER to have ANY problems related to sound card drivers?

I have just committed the ultimate sin of booting to Windows. I am posting this message using Windows...and I am not liking it. I wanna go back to Linux BUT WITH SOUND of course.:(

---

### Post by il nonno on 2006-08-14
[COLOR="DarkSlateGray"]damn, you sound so desperate. I can only sympathise though[/COLOR]

---

### Post by ashmew2 on 2006-12-27
HI , im having a similar problem , i am using a CMI8738 sound card and it was working fine , but the sound was seeming quite low as compared to windows on Linux , so i went to [www.alsa-project.com](www.alsa-project.com) and tried to install the latest stable driver which ended up giving some errors on compiling and stuff and ultimately the sound got damaged. Now I have tried removing those packages which are mentioned in your previous posts and it uninstalled nautilius and gdm and what not..now what can i do ?!?!?! PLease help

---

### Post by kah00na on 2008-02-23
My sound has cut out and I can't get it back either.  I have reinstalled the suggested packages with Synaptic Package Manager but that didn't help.  I still have no sound.  Is there anyway to remove the sound card and then run something else to "re-find" it?

---

