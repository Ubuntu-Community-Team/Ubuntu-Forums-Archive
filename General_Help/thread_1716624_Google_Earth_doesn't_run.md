---
title: "Google Earth doesn't run"
date: 2011-03-28
forum: General Help
---

### Post by rva1945 on 2011-03-28
Ubuntu 10.10. I downloaded and installed the .deb package. It installed ok (I think so).

Now, Applications/Internet/Google earth does nothing.

If I run the command

google-earth

I get

/usr/bin/google-earth: 43: ./googleearth-bin: not found


?

---

### Post by wilee-nilee on 2011-03-28
Run this in the terminal.
```
sudo apt-get install lsb-core
```

You don't need the command there is a icon in menu-internet if it gets installed correctly.

---

### Post by rva1945 on 2011-03-28
> **wilee-nilee said:**
> Run this in the terminal.
```
sudo apt-get install lsb-core
```You don't need the command there is a icon in menu-internet if it gets installed correctly.

Thanks, it works now.

Now, how do I know when i have to run the pt-get install command? I thought that downloading the .deb package, right-click and opening it with the Ubuntu Software Center was enough.

---

### Post by wilee-nilee on 2011-03-28
> **rva1945 said:**
> Thanks, it works now.

Now, how do I know when i have to run the pt-get install command? I thought that downloading the .deb package, right-click and opening it with the Ubuntu Software Center was enough.

The google earth deb is a hacked version set up for open source in general, so the dependencies flag is not there for specific distro's, kind of unusual to some extent.

The thing is with 100's of versions of open source setups, and a portion of them and the programs and software only attached by installable software and little else, sometimes you have to mess around a bit.

---

### Post by rva1945 on 2011-03-29
> **wilee-nilee said:**
> The google earth deb is a hacked version set up for open source in general, so the dependencies flag is not there for specific distro's, kind of unusual to some extent.

The thing is with 100's of versions of open source setups, and a portion of them and the programs and software only attached by installable software and little else, sometimes you have to mess around a bit.

OK, now I wish to install Fligh Gear. Do you know which are the steps to follow?

Do I have to download a .deb package and then...?

---

### Post by Enigmapond on 2011-03-29
No..that can be installed right from [http://www.playdeb.net/updates/Ubuntu/10.10](http://www.playdeb.net/updates/Ubuntu/10.10)

Just follow the instructions on adding the repo and once done, it will be available in the software centre after you run:
```
sudo apt-get update
```

---

### Post by rva1945 on 2011-03-29
> **Enigmapond said:**
> No..that can be installed right from [http://www.playdeb.net/updates/Ubuntu/10.10](http://www.playdeb.net/updates/Ubuntu/10.10)
 
Just follow the instructions on adding the repo and once done, it will be available in the software centre after you run:
```
sudo apt-get update
```
 
Thanks, I'll try tonight.
 
A year ago I decided to change to Linux (from W) and it was a correct decision: the PC works fast, no problems with viruses, no fees. I use W just in a VM to connect to the office with mstsc because it uses rdp 6.
 
The only problem -closely related to vireses, I'm having since a week is that I can't watch most videos in youtube; some don't play but worse than that, many videos seem to have been replaced by ads or things like that. I can't even watch some videos I uploaded!
 
As far as I know, maybe I updated the plug-in but it was a malaware or something like that. I tried uninstalling the flash plug-in form Synaptic and reinstalling from adobe.com but to no avail.
 
Do you have any hint about this?
 
Thanks

---

