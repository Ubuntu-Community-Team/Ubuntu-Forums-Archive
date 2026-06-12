---
title: "Flash not working on Ubuntu 11.04"
date: 2011-05-02
forum: General Help
---

### Post by berserkpi on 2011-05-02
I just installed Ubuntu 11.04 64 bits.

I Installed the restricted packages but the browsers chrome/ff4 can not detect flash :S

Instead of showing the flash content It says I must install flash firstly....  :X

Thanks.

---

### Post by dino99 on 2011-05-02
from synaptic remove/purge it then install flashplugin-installer

---

### Post by 5149.5 on 2011-05-02
Try the Flashaid plugin.

---

### Post by b1tchacked on 2011-08-14
I tired the flash aid plugin , even then it prompts that there is an update for adobe flash player.........

---

### Post by garvinrick4 on 2011-08-14
Flash aid fetches the last known flashplayer version give it a go again.
You have made a mistake somewhere along the line. If you have tried to install
it multiple times there might be remnants of flash everywhere. flash aid will
remove them all and install again for you.
Or if you choose remove all flash and install from Ubuntu software center or Synaptic.
Stop all firefox running and copy and paste these one at a time. 

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
``````
sudo rm -f /usr/lib/mozilla/plugins/*flash*
``````
sudo rm -f ~/.mozilla/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
``````
sudo rm -rfd /usr/lib/nspluginwrapper
```#Now reinstall through Ubuntu software center or synaptics. Or even as most do to get most all restricted packages in one swoop.
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by uRock on 2011-08-14
> **b1tchacked said:**
> I tired the flash aid plugin , even then it prompts that there is an update for adobe flash player.........

Click the FlashAid button on the in the browser and follow the prompts.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200003&stc=1&d=1313302414[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=200004&stc=1&d=1313302414[/IMG]

---

### Post by mathman316 on 2011-09-24
I was having the "flash not working at all" problem (on 32-bit), and the flash aid plugin resolved it.  Thanks!

---

