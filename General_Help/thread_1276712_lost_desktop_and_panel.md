---
title: "lost desktop and panel"
date: 2009-09-27
forum: General Help
---

### Post by popppppz on 2009-09-27
:confused: **I updated from KDE 4.2 to KDE 4.3 but some packages were missing it said. After I rebooted, my desktop, panel, internet, and ability to right click on the desktop were all missing. My Avant Windows Dock is still there, and so are my Screenlets, so I do have a terminal to work with. I still have access to the Gnome desktop where I see all my stuff is still there including KDE 4.2 and KDE 4.3 folders however I still do not have internet access, even with the Gnome desktop. I tried removing KDE 4.3, terminal says its removed but it's not. My linux version is Ubuntu updated to Kubuntu 9.04. Please help, thank you.**

---

### Post by Catarina on 2009-09-27
Do you keep a backup of your data somewhere? Or maybe have /home on another partition? That would help ;)

I once updated from Ubuntu to Xubuntu, and when I tried to go back, the packages just got all messed up, so I think the best you can do is a clean install of the system. Sorry, that's the only solution I can give you atm, but if you have important data you can't afford to loose, there might be someone that might be able to help you more than me. :(

---

### Post by popppppz on 2009-09-27
I still have all my folders inside the gnome desktop. Is there any other way to fix the desktop or panel other than reformatting linux? I'm new to linux and have worked very hard the past few weeks to learn the system, finally I had everything setup perfectly, it was a lot of work. I have everything fine tuned and skins on every program that would let me. :(

---

### Post by MelDJ on 2009-09-28
> **popppppz said:**
> :confused: **I updated from KDE 4.2 to KDE 4.3 but some packages were missing it said. After I rebooted, my desktop, panel, internet, and ability to right click on the desktop were all missing. My Avant Windows Dock is still there, and so are my Screenlets, so I do have a terminal to work with. I still have access to the Gnome desktop where I see all my stuff is still there including KDE 4.2 and KDE 4.3 folders however I still do not have internet access, even with the Gnome desktop. I tried removing KDE 4.3, terminal says its removed but it's not. My linux version is Ubuntu updated to Kubuntu 9.04. Please help, thank you.**

did you go to synaptic to uninstall KDE? if not, find for kde-desktop or Kde 4.3 and mark it for complete removal. after that go to terminal and do  sudo apt-get autoremove. this should remove kde from your ubuntu

---

### Post by popppppz on 2009-09-28
Yes I tried that, I was able to find and remove KDE 4, however, I still get the same error. I am unable to install KDE 4.2 again because it deleted network manager and now I can't get a connection. I also can't get network manager reinstalled because I have no internet. I feel like if I could get my internet working again I could possibly reinstall KDE 4.2 and be okay. Is it possible to get my internet working again with out having the internet to download the package?

---

### Post by MelDJ on 2009-09-28
gnome' network manager should still be available. do you mean the it doesn't come in the panel. just try right clicking your panel and the press add to panel and then add notification area

---

### Post by popppppz on 2009-09-28
I have network widget avaliable but it has now ay of editing the numbers and all the numbers are wrong,.......i saw the terminal delete network manager and when i look in synapatic manager both kde network manager and gnome network manager are unchecked when i try to reinstall one or the other it says cannont find packages i think its because i have no internet because i have my sources right

---

### Post by MelDJ on 2009-09-28
maybe you could use your ubuntu cd as a software source. then install network manager from there

---

### Post by popppppz on 2009-09-28
i just finished trying that but it didnt work either at first thought it was going to because it found new software from it but it wouldnt install

---

### Post by MelDJ on 2009-09-28
was there an error message? if there was, please post it

---

### Post by popppppz on 2009-09-28
It was the same as before that it couldnt find packages ,...i think it was trying to connect to the internet and not the cd but it didnt pop up untill i put in the cd

---

### Post by MelDJ on 2009-09-28
did you go to software sources- third party software and check the cdrom?

---

### Post by popppppz on 2009-09-28
no it popped up when i put in the disk but thats a great idea ill try that,..ill have to try it later its 5 am here so bed time first lol but thanks ill def try it that way

---

### Post by MelDJ on 2009-09-28
come back here and post the result of it though:KS

---

