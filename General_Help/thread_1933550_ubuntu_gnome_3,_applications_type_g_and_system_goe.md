---
title: "ubuntu gnome 3, applications type g and system goes crazy"
date: 2012-02-29
forum: General Help
---

### Post by sdowney717 on 2012-02-29
It was working, now it does this.
put mouse to left corner
type a 'g' in the search field

screen moves around and comes back
do this again, type a 'g' in the search field, screen messes around, then on the top left side displays file edit etc... in a row and you cant use the left corner again as in push mouse to left upper corner, nothing happens.
So then I have to do a logout to reset everything. Have to type alt-sysrq-k for that.

here is the normal view

I cant even post a screenshot of the altered view using ubuntu

---

### Post by sdowney717 on 2012-02-29
I took a photo with the phone. As you can see there is this menu bar at the top which you can interact with. It opens the file nautilus screen which is locked to the left top corner and overlays the browser.

---

### Post by sdowney717 on 2012-02-29
Then this nautilus window stays on top and you can interact with it.

So why is it doing this when typing 'g' in the application search field?

---

### Post by sdowney717 on 2012-03-01
I found out it does this with pressing ANY keyboard letter.

I cant use it like that. I suppose I have to make a new user?
Any ideas where the config file is?

---

### Post by sdowney717 on 2012-03-01
It is a bug!
how come I am always affected? Where are all the bugged people getting bugged posting this issue?
Should be many affected.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/936132](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/936132)

upgraded to 12.04 beta and it still happens, just a more graceful report.

---

### Post by sdowney717 on 2012-03-06
[http://ubuntuforums.org/showthread.php?t=1928215&page=2](http://ubuntuforums.org/showthread.php?t=1928215&page=2)

add the gnome3-team/gnome3 ppa

sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update

I just did this restarted and the problem is gone away.
Fixed. Typing in the search box does not crash the system.

---

