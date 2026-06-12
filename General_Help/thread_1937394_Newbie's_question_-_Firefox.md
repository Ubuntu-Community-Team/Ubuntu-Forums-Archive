---
title: "Newbie's question - Firefox"
date: 2012-03-07
forum: General Help
---

### Post by chenxinghao on 2012-03-07
I installed Ubuntu 11.10 in January and liked it very much. I am learning the basics. I made no customization of the desktop. Everything has been set with the defaults in the installation process.  

Until recently, the Firefox window would open within the space limited by the grey bar at the top and the application bar at the left. And I liked the way it was.

Recently there has been several updates to the system (all I did was click the install button). And now whenever I open a Firefox window it would take over the entire display screen and  I have to resize it to bring back the top grey bar and the left application bar.

Is there a way to set the Firefox window to start as it was before? Is so, how?

---

### Post by coffeecat on 2012-03-07
It sounds as though Firefox is now automaximising, but why it didn't before may be due to the size you resize it to when you unmaximise it.

Try this. When you unmaximise it, make the window smaller - less than 75% of the whole screen. If you then close Firefox, it *should* reopen unmaximised. The reason is that there is a default 75% threshold. If an application window is closed when it is 75% or smaller than maximised, then it will re-open unmaximised. If it is closed when larger than 75%, then it will re-open maximised.

Personally, I find 75% to be too small and prefer the threshold to be 80 or 85% depending on my monitor size. If you find the above suggestion works and you want the threshold larger, install the application compizconfig-settings-manager. Be careful with this. There are some settings which can break your Unity desktop, but you will be OK with the following. Open compizconfig-settings-manager, then Desktop -> Ubuntu Unity Plugin -> Experimental tab. Change the automaximise value to 80, 85% or whatever value suits you.

---

### Post by chenxinghao on 2012-03-07
It workes - resize it to smaller than 75%, closed all Firefox windows and then reopen one and it backs to a window within the desktop space.

---

