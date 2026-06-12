---
title: "installing cairo dock 2.1.2-4"
date: 2010-01-04
forum: General Help
---

### Post by yxrkt on 2010-01-04
The latest .deb i was able to find was for 2.0.9, but i'd like to install 2.1.2-4. This is the website i found:

[http://developer.berlios.de/project/showfiles.php?group_id=8724](http://developer.berlios.de/project/showfiles.php?group_id=8724)

I'd greatly appreciate it if someone could tell me where to find a deb, or tell me how to make gettext work when I run 

```
autoreconf -isf
```

---

### Post by timgood on 2010-01-04
It is available in launchpad. From terminal do:

sudo -v
echo "deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu)  $(lsb_release -sc) main ## Cairo-Dock-PPA-Stable" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
sudo apt-get update
sudo apt-get install cairo-dock

Hope this helps.

---

### Post by fabounet on 2010-01-04
come on, it's written in capital letters on the page you've quoted !
> WE_ARE_ON_LAUNCHPAD_NOW

the installation method is fully described there, and you can also find a weekly package to get the current beta version.

---

### Post by yxrkt on 2010-01-04
thanks timgood, got the latest version (unfortunately, there's still the wine problem though). I'd still like to be able to build applets for it though

---

### Post by bhj6268 on 2010-01-22
I used this method to install 2.1.2-4 and it worked.  How do I install the 2.1.2-4 plugins?

sudo -v
echo "deb [http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu](http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu)  $(lsb_release -sc) main ## Cairo-Dock-PPA-Stable" | sudo tee -a /etc/apt/sources.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E80D6BF5
sudo apt-get update
sudo apt-get install cairo-dock



I'm new to Linux so don't laugh.

---

### Post by fabounet on 2010-01-22
plug-ins are included in the package (this is a meta-package)

---

### Post by graphius on 2010-01-30
I upgraded my cairo dock as per the instructions above, now I do not have any plug-ins, accessories, controllers....

Not sure if they are just hidden in the configuration panel, or if they were deleted...

---

### Post by fabounet on 2010-01-30
you have to install both **core** _and_ **plug-ins** in the same version.
if their version mismatch, they will not be loaded.

---

### Post by finlost on 2010-01-31
Something is hosed up.  

I initially install via Synaptic.  I think I had v2.0.9xxx.  I couldn't update themes as the OP indicated in this topic.

I then followed the above commands to install via terminal.  I am now running v2.1.2-4.  I still cannot update themes.  Just as graphius indicated, I also appear to be missing a lot of the options/settings.  I have Behavior and Appearance.  Accessories, Desktop, Controllers, and Plug-ins are all blank.

Is it a bad sign if [www.cairo-dock.org](www.cairo-dock.org) cannot be found?

---

### Post by finlost on 2010-01-31
> **fabounet said:**
> you have to install both **core** _and_ **plug-ins** in the same version.
if their version mismatch, they will not be loaded.
This solved the problem of  Accessories, Desktop, Controllers, and Plug-ins previously missing.  It didn't solve the problem of not being able to load themes.

---

### Post by finlost on 2010-01-31
Answer found for a temp fix for themes - [clicky]("http://ubuntuforums.org/showpost.php?p=8681404&postcount=3")

---

### Post by graphius on 2010-01-31
> I also appear to be missing a lot of the options/settings. I have Behavior and Appearance. Accessories, Desktop, Controllers, and Plug-ins are all blank.

I uninstalled the plugins:

```
sudo apt-get purge cairo-dock-plugins
```

then installed them again

```
sudo apt-get install cairo-dock-plugins
```

then, since I had cairo dock set to start up automatically, I logged out and logged back in, all is good now.

---

