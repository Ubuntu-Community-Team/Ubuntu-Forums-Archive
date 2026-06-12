---
title: "Low resolution display in Xubuntu"
date: 2011-11-19
forum: General Help
---

### Post by rem on 2011-11-19
Hello,

I've installed Xubuntu Oneiric on my friend's old computer. While testing it with the live CD, the resolution was 1024 x 768 but after installation it went even lower to 600 and something. The Nvidia card was recognised and the proprietary driver is installed but still cannot select a higher resolution from the "Display" settings. I've tried to reconfigure xorg with dpkg-reconfigure xserver-xorg but it just doesn't do anything, the assistant which used to allow me to select higher resolutions doesn't work anymore.

Can you pretty please help? I am trying to help a guy move from Windows to Linux but all I got now is an useless computer due to the very low resolution.

Thank you, appreciate it.

---

### Post by bryncoles on 2011-11-19
According to [this thread](http://ubuntuforums.org/showthread.php?t=1838455), you might need to configure with some special nvidia settings thing.  

Try the following in a terminal:

```
gksudo nvidia-settings
```and 
[quote=hhh]The settings are under "X Server Display Configuration". Change them, clcik the "Apply" button, then "Save to X configuration file", don't merge with the old file.

If you don't have nvidia-settings, install it via Synaptic.[/quote]

Does that help?

---

### Post by rem on 2011-11-20
Thank you for your answer. It all makes sense but once I installed nvidia-settings and went to the X Server Display Configuration tab, I got only this:

```
Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.
```

Have any ideas?

---

### Post by bryncoles on 2011-11-20
Erk!  I didn't expect that outcome.  

Erm, no I'm not sure what to make of it.  Do you have any propitiatory drivers which need enabling (menu -> settings -> additional drivers)?

Also, could you post the output of ```
apt-cache policy nvidia-settings
``` (cut-and-paste into a terminal), as the bug report [here](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings-updates/+bug/539196) implies there is a fix for some versions.  

Don't know if it'll help or not, but worth a try...

---

### Post by rem on 2011-11-20
Ok, will have to try that and get back here asap. The proprietary driver is already installed.

Thank you bryncoles.

---

### Post by bryncoles on 2011-11-20
Hopefully someone more competent will join in soon to help us out further, but let's see how far we can get!

---

### Post by rem on 2011-11-20
> **bryncoles said:**
> Hopefully someone more competent will join in soon to help us out further, but let's see how far we can get!

that would be really great, thank you. it might take a little while until i'll have the output since the computer is not near me. i will have to go visit my friend that i'm trying to help.

---

### Post by rem on 2011-11-20
This is what I got after running apt-cache policy nvidia-settings

```
installed: 280.13-Oubuntu2
candidate: 280.13-Oubuntu2
version table: 
*** 280.13-Oubuntu2 0
500 http://ro.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages
100 /var/lib/dpkg/status
```

Thanks!

---

### Post by bryncoles on 2011-11-20
Bum.  All that output told me is that there shouldn't be a problem, as you're using a nice, up-to-date version of the driver.  

Have you seen [this](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) how to?  Particularly the bit that says to type 

```
sudo nvidia-xconfig
``` into a terminal (it'll ask for the password, but won't display anything as you type.  This is normal, just input the password and press return) and then reboot?

Also, the bit that says to add ```
xrandr --addmode S-video ...
``` into the terminal, replacing the '...' with the resolution you want (so '1280x800' or something like that I guess)

Let's see what happens when you do that?

---

### Post by larrypg on 2011-11-20
Hello,

Since you mentioned your friends old computer.....might want to find out what the video card is and see if it is still supported and what driver it needs.  An older card might not be able to use the propriatary drivers and just use the kernel driver.  Sorry if I overlooked which card it is.

---

### Post by rem on 2011-11-21
Thank you guys for your advices. I will look into that and get back here with the results.

Cheers!

---

### Post by rem on 2011-11-21
i had my friend remove the proprietary driver which turned the resolution to 1024 x 768 which is a huge improvement. thanks larrypg.

one of the next days, since i'm a bit more familiarised with the command line, will go to his place and try the nvidia driver how-to bryncoles recommended, thanks.

will keep you posted.

---

### Post by bryncoles on 2011-11-21
It's good to see progress being made, and good to see you're not command-line phobic!

I hope you and your friend enjoy Xubuntu!

---

### Post by rem on 2011-11-27
Hello guys, back to you again. I run the two commands from the [HOW-TO]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") as such:

first one
```
sudo nvidia-xconfig
```

broke the display and had to go and recover the previously backed-up xorg.conf file

second one
```
xrandr --addmode S-video 1280x768
```

returned this output:

```
xrandr --addmode S-video 1280x768
xrandr: Failed to get size of gamma for output default
xrandr: cannot find output "S-video"
```

I am completely and definitively lost. I don't even know what that means. Have any other advices for me?

Thank you.

---

