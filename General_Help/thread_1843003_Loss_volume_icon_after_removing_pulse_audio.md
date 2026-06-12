---
title: "Loss volume icon after removing pulse audio"
date: 2011-09-12
forum: General Help
---

### Post by magicland on 2011-09-12
Greetings folks,

i am running ubuntu 11.04 64bits and i've removed the pulseaudio to make skype work correctly. However, i've lost the volume icon on the taskbar and i cannot right click the task bar (is that normal....).

This is the guide i followed to uninstall pulseaudio and installing alsa instead:

[COLOR=#000000][FONT=Segoe UI][SIZE=3][http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/)[/SIZE][/FONT][/COLOR]

Does anyone know how to fix it?


Thanks

---

### Post by Frogs Hair on 2011-09-12
Hi and Welcome

Step 2 in the tutorial explains that purging Pulse Audio removes the volume applet. Entering the commands in step two is supposed to install the Alsa volume applet . 

Did you fully complete the tutorial and restart ? Are you using Unity? It is not clear in the tutorial if it applies to the Gnome Panel , Unity Panel , or both .

---

### Post by magicland on 2011-09-13
Hi,

Yes i entirely followed the guide and restarted but the volume icon is still mixing somehow... And i am not quite sure if it's used for unity or gnome or both, but one of the comment seems to say that he got it to work under 11.04 without any trouble (except for the icon's background color).

Oh and one more thing, i tried to execute the volbar.py and alsavol.py and they aren't doing anything at all.

---

### Post by fdrake on 2011-09-13
can you please run this commands,thanks:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms linux-headers linux-image
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install python python-notify python-gtk2 python-alsaaudio python-eggtrayicon xfce4-mixer

```

after you have done this follow the rest of step 2;
wget [http://howto.blbosti.com/files/alsa/alsa_mixer_applet_1.1.tar.gz](http://howto.blbosti.com/files/alsa/alsa_mixer_applet_1.1.tar.gz) 
etc .... 
and test if they work now. of you still have nothing please post here all the results for each command starting with "sudo apt-get install --reinstall linux-headers- ......."

---

### Post by magicland on 2011-09-13
Hi there,

this is the results after i run the first command:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.38-11-virtual 2.6.38-11.48
  linux-headers-2.6.38-11-server 2.6.38-11.48
  linux-headers-2.6.38-11-generic 2.6.38-11.48
  linux-headers-2.6.38-11 2.6.38-11.48
  linux-headers-2.6.38-10-virtual 2.6.38-10.46
  linux-headers-2.6.38-10-server 2.6.38-10.46
  linux-headers-2.6.38-10-generic 2.6.38-10.46
  linux-headers-2.6.38-10 2.6.38-10.46
  linux-headers-2.6.38-8-virtual 2.6.38-8.42
  linux-headers-2.6.38-8-server 2.6.38-8.42
  linux-headers-2.6.38-8-generic 2.6.38-8.42
  linux-headers-2.6.38-8 2.6.38-8.42
You should explicitly select one to install.

E: Package 'linux-headers' has no installation candidate


Thanks

---

### Post by fdrake on 2011-09-13
can you post the results for ```
uname -r
```

---

### Post by magicland on 2011-09-13
2.6.38-8-generic

this is it

---

### Post by fdrake on 2011-09-13
replace in my first command "linux-headers" with "linux-headers-2.6.38-8-generic"

---

### Post by Pariah819 on 2011-09-13
Can you verify that the "indicator-sound" package is installed in the synaptic package manager.  It might have inadvertently been removed during the procedure you followed.

---

### Post by magicland on 2011-09-13
> **Pariah819 said:**
> Can you verify that the "indicator-sound" package is installed in the synaptic package manager.  It might have inadvertently been removed during the procedure you followed.

Hello,

i just checked in the synaptic package manager and the indicator-sound is still installed.

Oh and a little update, i just noticed that i have no more sound at all, even though i can access xfce4-mixer or the alsamixer and play around with the settings.

---

### Post by magicland on 2011-09-13
@fdrake

Thanks, i replaced the linux-headers in the first command and it proceeded to install/reinstall without any problem. I continued with step 2 and 3 and the rest of the guide and there is still nothing.

During step 2 there was alot of lines i am not sure what to post to you since there's so many lines and i am not sure if it'll be pertinent to post them all.

---

### Post by magicland on 2011-09-13
> **magicland said:**
> 
Oh and a little update, i just noticed that i have no more sound at all, even though i can access xfce4-mixer or the alsamixer and play around with the settings.

Just got home, booted up and my sound is working perfectly now...

---

### Post by Pariah819 on 2011-09-13
Are you still missing the panel indicator or is everything fixed?

---

### Post by magicland on 2011-09-13
I am still missing the indicator...

I tried running the volbar.py manually and this is coming up in the terminal:

/usr/local/bin/volbar.py:202: GtkWarning: Invalid icon size 0

  gtk.main()


Wondering if this is the reason why it isn't showing

---

### Post by Pariah819 on 2011-09-13
Did you install the gnome-alsamixer or the xfce4-mixer?  If you installed the gnome-alsamixer then there was a note about editing the volbar.py script before running it... Did you see that?

---

### Post by magicland on 2011-09-13
Yeah i saw it, but i didn't install the gnome-alsamixer, i installed the xfce4-mixer.

---

### Post by Pariah819 on 2011-09-13
Well I'm starting to run out of ideas but here is another thread I found that sounds similar to your situation, they believe the problem lies somewhere in the home directory...

[http://ubuntuforums.org/showthread.php?t=1841277](http://ubuntuforums.org/showthread.php?t=1841277)

---

### Post by magicland on 2011-09-14
Hey guys, found a fix for the volume indicator.

Source: [http://askubuntu.com/questions/30742/how-do-i-access-and-enable-more-icons-to-be-in-the-system-tray](http://askubuntu.com/questions/30742/how-do-i-access-and-enable-more-icons-to-be-in-the-system-tray)

Code to copy/paste in the terminal:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```This will whitelist all programs to use the unity's panel. And then reboot.

Thanks for all the help guys!

---

### Post by Pariah819 on 2011-09-14
Nice work!

---

