---
title: "Ubuntu 12.04 Randomly Freezes - Core i5 Ivy Bridge - On Board Graphics"
date: 2012-06-26
forum: General Help
---

### Post by Crell Vorlem on 2012-06-26
Hello,

I just built a new PC running Ubuntu 12.04 with an Intel Core i5 3450 (Ivy Bridge) CPU which utilizes on board Intel HD 4000 graphics and am having issues with my desktop completely freezing at random times plus a number of other strange errors. Right after the installation, the freezing begun and would happen randomly approximately once every hour. I also got this error message a few times when booting: 

```
 The system is running in low graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

```

I've already gone through a number of troubleshooting steps like checking the RAM and reinstalling Ubuntu from scratch but nothing helped. While doing some research on this issue, I read conflicting opinions on whether the 12.04 kernel works on Ivy Bridge chipsets, so I don't know if that's a problem. One observation I made was some of the drivers didn't install correctly on both Ubuntu install attempts so I downloaded these from the software center manually which had no effect.

As an experiment, I tried installing and running Ubuntu 12.04 with no internet connection at all and haven't seen it freeze once. Right after connecting it via ethernet to the internet, I tried running the update manager and after having it run for a while, I got this error:

[IMG]http://i.imgur.com/XXSpI.png[/IMG]

EDIT: I just tried updating again and got a slightly different error:

[IMG]http://i.imgur.com/XkUdy.png[/IMG]

I don't know if these issues are related, but for being connected to a fast and stable ethernet connection, my internet connection is slow to non-existant on this Ubuntu install. Many times pages will load half way and then just stop.

Any ideas on how to solve this issue? Thanks.

---

### Post by dino99 on 2012-06-26
can you browsing normally with firefox for example, or is it freezing too ?

check the graphic driver activation; into a terminal, run:

sudo jockey-gtk

then make some cleaning:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install  --fix-missing

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

and finally:

sudo rm /etc/X11/xorg.conf
sudo shutdown -R now

---

### Post by Crell Vorlem on 2012-06-26
> **dino99 said:**
> can you browsing normally with firefox for example, or is it freezing too ?

check the graphic driver activation; into a terminal, run:

sudo jockey-gtk

then make some cleaning:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install  --fix-missing

sudo dpkg-reconfigure -phigh -a
(can take a while, be patient)

and finally:

sudo rm /etc/X11/xorg.conf
sudo shutdown -R now

Thanks for the reply. 

I can browse in Firefox normally but more often than not pages won't load at all. Given enough time, the whole desktop will freeze. Since these problems only start happening after I try installing updates, I think the problem is coming from there.

When I ran *sudo jockey-gtk*, Terminal returned the following message two times followed by an empty Additional Drivers window that said "No Proprietary drivers are in use on this system."

```
(jockey-tk: 2242): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion 'icon_set != NULL' failed

```

The cleaning you suggested seemed to run normally.

When running *sudo apt-get update*, it looks like I run into the same errors that appeared in Update Manager. Each time it seems to get stuck on those Release.gpg files.

[IMG]http://i.imgur.com/aKnw4.png[/IMG]

*sudo apt-get install --fix-missing* seems to have run normally and reported back:
*0 updated, 0 newly installed, 0 to remove and 0 not upgraded.*

Running *sudo dpkg-reconfigure -phigh -a* did take a while and I guess it executed normally. It didn't report back any information.

Lastly, *sudo rm /etc/X11/xorg.conf* didn't seem to work. Upon running that command, I get the following error: 
*rm: cannot remove ' etc/X11/xorg.cong': No such file or directory*

---

