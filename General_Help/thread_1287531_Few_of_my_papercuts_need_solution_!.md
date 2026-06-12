---
title: "Few of my papercuts need solution !"
date: 2009-10-10
forum: General Help
---

### Post by sigurnjak on 2009-10-10
I have few questions regarding  little issues in my jaunty .

1. When i listen my music  ( XMMS , Real player or any other player ) and start anything that uses emulator  (Wine app. or Vbox ) my playing app cuts out . Is there a way to stop this , or keep it playing while other app is working ,such Win Firefox or Vbox .

2. At night i put my pc to sleep . When it wakes up i have to put my password in . My computer is set to auto login at boot  since only me and my wife use is . How do i make it auto  login from sleep ? 

3. When using dark themes  and wish to bookmark page in firefox or shiretoko , that little pop-up has all text black with black background . I thing i should edit chrome file in my browser profile , but i am not sure what to edit . 
Here is a screenshot to .

Any help is appreciated !

---

### Post by mac9416 on 2009-10-10
> 2. At night i put my pc to sleep . When it wakes up i have to put my password in . My computer is set to auto login at boot since only me and my wife use is . How do i make it auto login from sleep ?

Solution found here: [http://ubuntuforums.org/showthread.php?t=620769](http://ubuntuforums.org/showthread.php?t=620769)

[LIST=1]
[*]Start "gconf-editor" from Terminal.
[*]Check "/apps/gnome-power-manager/lock/use_screensaver_settings" option.
[/LIST]

There should really be a better way to change that.

I hope someone else is able to help you with the other two! :)

---

### Post by CatKiller on 2009-10-10
> **sigurnjak said:**
>  1. When i listen my music  ( XMMS , Real player or any other player ) and start anything that uses emulator  (Wine app. or Vbox ) my playing app cuts out . Is there a way to stop this , or keep it playing while other app is working ,such Win Firefox or Vbox .

Use a sound system that doesn't lock the sound device, like ALSA or PulseAudio. Either of these will behave nicely. This can be set in System &#8594; Preferences &#8594; Sound.

For Wine, I've found that the best results are to be had by setting Wine to use the OSS output in *winecfg*, but then running Wine through a wrapper that actually uses ALSA by running ```
aoss wine *programname*
``` Just telling Wine to use ALSA is sufficient, but it doesn't seem to perform quite as well on some applications as using OSS and the wrapper.

There's probably a way to tell VirtualBox to use ALSA or PulseAudio, but I couldn't tell you how because I've never used it. If it insists on using OSS, you can use the *aoss* wrapper again.

PulseAudio would be my preferred choice out of ALSA or PulseAudio, but I lot of people have taken against it because of its shaky first implementation in Ubuntu.

---

### Post by sigurnjak on 2009-10-10
Thanks folks for quick answers ! 
Sleep  issue fixed !
Wine sound seems to be little over my head .I have win Firefox on my desktop . How do i modify it to run with that wrapper ?

---

### Post by CatKiller on 2009-10-10
The easiest way is simply to run *winecfg* in a Terminal and change the sound device to ALSA. Otherwise, we'd need to know what "win Firefox on your desktop" means; is it the executable, or a shortcut, or what?

Any reason why you're running Firefox in Wine rather than using the native version?

---

### Post by sigurnjak on 2009-10-10
Firefox on the desktop is shortcut for windows Firefox installed for my wife to enable her to play Yoville on facebook . It is only way darn game works well.
As for winecfg , it is already set to ALSA . 

If you need more info let me know . Thanks for taking time to help me out .

---

### Post by CatKiller on 2009-10-11
That's good, it means you can modify the existing launcher rather than having to create a new one. Just right-click on the launcher and change the Command section of its properties to add in aoss before the wine part. Then set *winecfg* to use OSS. This is really a performance thing though.

What have you got set as your sound system in System &#8594; Preferences &#8594; Sound now? PulseAudio would be my preferred choice, as I said, since it should transparently handle software mixing of your audio streams.

---

### Post by sigurnjak on 2009-10-11
Excellent instructions ! I have added aoss to Firefox and change sound to Pulse audio . Now when i start Firefox via vine or Vbox  it does not interrupt rhytmbox   radio stream . Now if i could configure XMMS to use pulse that would be awesome . :guitar::)

---

### Post by CatKiller on 2009-10-11
Glad to hear it.

I can't really tell you anything about XMMS, since I don't use it.

ALSA output for XMMS should work in principle, or you could use the aoss wrapper again to change the output from OSS to ALSA, or there's a *padsp* wrapper that turns OSS into PulseAudio, but that doesn't appear to work quite as well as just using ALSA for automatic integration with PulseAudio.

---

