---
title: "install multiple debs without breaking the system"
date: 2010-11-15
forum: General Help
---

### Post by elliotn on 2010-11-15
I have a folder that contain about 2,5gb of debs ranging from vlc, gstreamer, jokosher and audacity etc 

those programs I backed up with dpkg repack, now I want to restore them but sudo -i .deb breaks my system 

I wonder if there is a to install them and skipping those which dependenciws are not met

---

### Post by elliotn on 2010-11-16
any ideas peeps

---

### Post by yuki-nagato on 2010-11-16
what do you mean when you say that installing these debs "breaks your system?"

[FONT=monospace]"dpkg -L packagename" lists the dependencies

normally if apt-get isn't out of commission, you could do
"apt-get -f install" to fix any broken dependencies but since you're using dpkg, I assume that that also means apt-get is screwed,

dpkg is one of the most basic programs in Debian based OSes like Ubuntu, but that also means that it is designed to do different things than apt-get and aptitude.  dpkg doesn't automatically download missing dependencies like apt-get and aptitude will but it does tell you which ones you'll need.

I would run dpkg -L and find out which ones the packages need to install properly and either use apt-get -f to fix it or find and install the relevant debs manually using dpkg.
[/FONT]

---

### Post by elliotn on 2010-11-16
> **yuki-nagato said:**
> what do you mean when you say that installing these debs "breaks your system?"

[FONT=monospace]"dpkg -L packagename" lists the dependencies
[/FONT]
k that sounds good I will use that command to list all needed files then move them in one folder then do a dpkg -i .deb in that way it won't break my system as all dependencies will be met 
off to try it

---

