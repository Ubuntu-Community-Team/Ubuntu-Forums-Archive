---
title: "How to get rid of Edubuntu stuff"
date: 2006-03-28
forum: General Help
---

### Post by omeg on 2006-03-28
Hi all. I've got a default 5.10 installation on my laptop, and decided that it might be fun to install the Edubuntu package (the one that depends on all other packages). I took a quick peek at it and decided that I wasn't really going to use the tools, so I wanted to get rid of them.

Apparently, it's not really possible to remove all of the packages it installed in one turn, so I went ahead and removed all of the applications that showed up in the "Education" folder in the "Applications" menu. However, this didn't really remove everything. There's still a lot of disk space being used by Edubuntu, and I don't know how to reclaim it because I don't know what's really taking up my space. Also, it seems that the startup screen and logo have also been "taken over" by Edubuntu (as well as my wallpaper, which I reset to its original).

Is there any way to completely remove these things? I've installed a good 290 MB of space with Edubuntu, and removing the applications that I found in the "Applications" menu freed up about 50, but I'd still like to get the rest of my space back since the laptop it's on is pretty old and needs all the space it can get.

Thanks!

---

### Post by ajgreeny on 2006-03-28
I'm not sure about this but I wonder if the history in synaptic will tell you what packages were installed when you got the edubuntu package.

If you want to look, open synaptic and click on File-History and find the date you installed edubuntu.  If that doesn't work then I'm afraid I can't help, but I bet someone else can.  Best of luck.

---

### Post by engla on 2006-03-28
Synaptic and apt-get are sadly not the coolest package managers, only very useful tools for removing things.

There is aptitude on the system, but it only has a terminal interface (similar to Synaptic, but in ASCII! ). It works like so that if you install edubuntu-desktop, it marks the additional packages so that they are removed together with edubuntu-desktop too. Sadly there is no way for you to use that now, since you didn't install these packages with aptitude. Yes, it's silly that synaptic doesn't have this feature.

I myself use **debfoster** to remove packages, you can install it from the repositories. It will ask you things like this:
ubuntu-desktop depends on the following packages:
  [list of maybe 200 packages]
Keep ubuntu-desktop? [Yes/No/Purge etc]

First time you run it you have to answer a lot of questions, but using that program you should be able to
1. Install edubuntu-desktop with synaptic again (since it's the *master* package)
2. Use debfoster. Answer to **Keep** (y) everything packages except edubuntu-desktop where you go **Purge** (p) [This will remove all packages that edubuntu-desktop depends on but no other packages (i.e ubuntu-desktop depends on)]

This should work, but I don't know because I never installed edubuntu-desktop. **Don't do the above if you don't really know what it is about or don't trust yourself to judge if you're going to screw up your system or not..** if you mandate to purge the wrong things, you remove all too much, of course.

---

### Post by omeg on 2006-03-28
Hmm. It's even changed my ubuntu-artwork/home/index.html. I really suggest that from now on, the dummy packages such as Edubuntu should carry warnings to prevent people from getting into something they don't know about.

If there's no safe way to remove it, I guess that I just am not going to do it, period...

---

### Post by AndrewCaul on 2006-03-28
[QUOTE=omeg]Hmm. It's even changed my ubuntu-artwork/home/index.html. I really suggest that from now on, the dummy packages such as Edubuntu should carry warnings to prevent people from getting into something they don't know about.

If there's no safe way to remove it, I guess that I just am not going to do it, period...[/QUOTE]
Its dependencies are the warning. Maybe you should have checked the descriptions on those packages before installing. :???: 

Try installing/reinstalling ubuntu-artwork. that might get your artwork back.

---

### Post by omeg on 2006-03-28
Well, it's true that that's the "warning", but it isn't very obvious to most people. I'm tech-savvy, so I should have known better, but I still didn't expect it to be so difficult to remove.

Also, uninstalling edubuntu-artwork has at least made my computer revert to the normal artwork.

---

### Post by AndrewCaul on 2006-03-28
Oh, heh. I had assumed you already tried that. Is everything back to normal now?

---

