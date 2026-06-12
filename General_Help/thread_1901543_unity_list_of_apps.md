---
title: "unity list of apps"
date: 2011-12-28
forum: General Help
---

### Post by Janeleaper on 2011-12-28
How do I get a list of installed apps in Unity?  I've been watching Jorge's tutorial, and he seems to have one in the side bar, but I don't have one.

---

### Post by arpanaut on 2011-12-28
Hit the Super (windows) key + a will give you the apps lens. They took it out of the launcher in 11.10
or hit the top ubuntu icon then across the bottom of the dash next to the home icon hit the apps icon for the list.

---

### Post by Janeleaper on 2011-12-28
Horrible.  Unity is a step backwards.  You have to use two keys/two hands, to do almost everything you could previously do with one.  A lot of people seem to be switching to Debian.  I've got Lubuntu 11.10 set up on my netbook, and I may switch to that.

---

### Post by grahammechanical on 2011-12-28
You may be right but I am not sure that I agree with the two hands comment. I bet you will not see Lubuntu on many touch-screen devices but Unity will be there.

This is a beginning

[http://www.canonical.com/content/vodafone-webbook-ubuntu-software-launched-south-africa]("http://www.canonical.com/content/vodafone-webbook-ubuntu-software-launched-south-africa")

Regards.

---

### Post by Janeleaper on 2011-12-29
Frankly, I'm torn between brand loyalty (I've been using Ubuntu for several years) and my productivity needs.  I multitask on my desktop, and although it is not impossible on Oneiric, having several applications open at once involves more keystrokes/mouse actions.

It is particularly irritating that there is no installed applications list.  I dislike the dashboard, and using it to open applications is tedious and time-wasting. 

Actually, I hate the dashboard. The fact that it cannot be customized, means that that it gives me shortcuts to three apps I never use (Shotwell, Thunderbird and Banshee), and everything I do use has to be found by a timewasting search.

My screen is only 10" tall.  It is on my work-desk, and since I'm not a gamer, and don't use my desktop for media, other than radio, I don't want a larger screen. The big icons for apps means there is not enough space on for all the apps I do use.  

Sorry, I'm just sounding off.  I know that all these criticisms have been made elsewhere on the forum.  I started this thread in the genuine hope that I could restore the apps list.

---

### Post by JRV on 2011-12-29
You can install an indicator that will give you the gnome classic menus, like this:

```

sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator

```

---

### Post by cortman on 2011-12-29
> **Janeleaper said:**
> Frankly, I'm torn between brand loyalty (I've been using Ubuntu for several years) and my productivity needs.  I multitask on my desktop, and although it is not impossible on Oneiric, having several applications open at once involves more keystrokes/mouse actions.

It is particularly irritating that there is no installed applications list.  I dislike the dashboard, and using it to open applications is tedious and time-wasting. 

Actually, I hate the dashboard. The fact that it cannot be customized, means that that it gives me shortcuts to three apps I never use (Shotwell, Thunderbird and Banshee), and everything I do use has to be found by a timewasting search.

My screen is only 10" tall.  It is on my work-desk, and since I'm not a gamer, and don't use my desktop for media, other than radio, I don't want a larger screen. The big icons for apps means there is not enough space on for all the apps I do use.  

Sorry, I'm just sounding off.  I know that all these criticisms have been made elsewhere on the forum.  I started this thread in the genuine hope that I could restore the apps list.

Just don't use Unity. I have gotten used to my gnome shell and docky arrangement. If you prefer a classic menu style and a lot of customizability on that, go XFCE.

```
sudo apt-get xfce4
```

or if you want the whole app bundle too

```
sudo apt-get install xubuntu-desktop
```

Unity != Ubuntu. You can use just about any DE with Ubuntu.

---

### Post by Janeleaper on 2011-12-30
Thanks for the tips.

I installed the classic menu indicator.  

The Xubuntu work-top wouldn't install.

However, the classic menu indicator is what I was looking for.  It makes Unity usable for me, so I'll stick with it for a while.

---

### Post by Paqman on 2011-12-30
> **Janeleaper said:**
> 
Actually, I hate the dashboard. The fact that it cannot be customized, means that that it gives me shortcuts to three apps I never use (Shotwell, Thunderbird and Banshee), and everything I do use has to be found by a timewasting search.


They've listened to the feedback on the pointless stuff in the dash, and it'll be changed for the next version. It will basically just be the search box IIRC. Hopefully that'l make it a bit snappier and more pleasant to use.

I'm still undecided about the usability of search as the ONLY way to launch apps, but it really comes into its own when you realise that with zeitgeist beavering away behind the scenes it can launch anything, not just apps. I use Synapse, a zeitgeist-powered launcher to launch just about everything these days. Having the same interface for launching apps and commonly used files is nice.

---

### Post by JRV on 2011-12-30
> **Janeleaper said:**
> The big icons for apps means there is not enough space on for all the apps I do use.  


To shrink the icons in the launcher bar install compizconfig-settings-manager with the command:
```

sudo apt-get install compizconfig-settings-manager
```

And run it with the command:```
ccsm
```

Be careful with this. Lots of the features it has don't work well with Unity.
(I Don't use anything but the Ubuntu Unity Plugin.)  

Open the Ubuntu Unity Plugin and click the Experimental tab.

There you will find the slider to control the icon size.

---

### Post by cortman on 2011-12-30
> **Janeleaper said:**
> Thanks for the tips.

I installed the classic menu indicator.  

The Xubuntu work-top wouldn't install.

However, the classic menu indicator is what I was looking for.  It makes Unity usable for me, so I'll stick with it for a while.

Glad to hear Unity's working for you!
BUT...

Xubuntu probably would have installed fine had you tried

```
xubuntu-_desk_top
```

---

### Post by Janeleaper on 2011-12-30
Thanks for the tip about reducing the size of the icons JRV.  However, now that you've helped me install the Classic Menu Indicator, I can live with the icons as they are, so I think I'll stop tweaking at this point.

---

### Post by corncob on 2011-12-30
> **JRV said:**
> You can install an indicator that will give you the gnome classic menus, like this:

```

sudo add-apt-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator

```

Thank you.  That will make Unity more useful.  It does come as an application on cairo dock incidentally.

---

