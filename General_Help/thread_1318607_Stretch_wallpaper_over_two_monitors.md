---
title: "Stretch wallpaper over two monitors"
date: 2009-11-07
forum: General Help
---

### Post by raafe on 2009-11-07
Hi all, as the title suggests I have a dual monitor wallpaper but when when I change it in kubuntu 9.10 it just changes the wallpaper for the i am using, how do i get it to stretch one image over both monitors like it always used too?

Thanks folks, sorry for the noobish questions!

Guy

---

### Post by raafe on 2009-11-10
Bump

---

### Post by gradinaruvasile on 2009-11-10
Ummm.. do u have some options on how the wallpaper is presented? You should use something like centered/scaled. At least Gnome has them named like this.

---

### Post by raafe on 2009-11-10
Hey, cheers for the reply!

Yes i have all the usual options , centered, scaled, cropped and so on but all they do is change the wallpaper on the monitor i have the settings open in. I just want one wallpaper to scale across both monitors like they normally do!

Guy

---

### Post by raafe on 2009-11-13
Bump..

---

### Post by kubug on 2009-11-13
What video card do you have? I have an nvidia card and it does it for me without me setting anything. Also, I have "Twinview" setup and not "Separate X Screen" in my Nvidia settings.

My wallpaper setting is on "Zoom".

---

### Post by raafe on 2009-11-13
Thanks for the reply, I have a Nvidia gpu too, I have the latest drivers and I have my monitors configured to "Twinview" too.

It's really annoying because everything else works perfectly except for this. I have two of the plasma icons in the top right, 1 on each monitor - maybe that is related?

And i do not have a "zoom" option in my desktop settings :cry:

Thanks

Guy

---

### Post by kubug on 2009-11-13
I took a screenshot of my nvidia-settings. Can you check to see if there are some differences (other than gpu model and monitors)?

---

### Post by raafe on 2009-11-13
H again kubug, thanks for your help with this it's really appreciated.

I have everything the same as you except for my "make this the primary display for the X screen" is checked.

I opened my nvidia settings as sudo and checked the box then clicked apply and save to x configuration file and then did a restart to see if that was causing it, however when i logged back in the box was still checked.

Any Ideas? Or is your other monitor the primary display?

Thanks

Guy

---

### Post by kubug on 2009-11-13
I just checked. Neither is set as primary. 

How about resetting your xorg.conf? 

```
sudo dpkg-reconfigure xserver-xorg
```

This will create a xorg.conf file is none existed (Karmic doesn't make on by default). 

Then run 

```
sudo nvidia-xconfig
```

which will set the default nvidia settings. That's all I did and I had everything the way I wanted.

---

### Post by raafe on 2009-11-13
I cannot seem to reset my xorg.conf, after following both your commands the settings had not changed at all, so i then deleted the xorg.conf which i thought would cause it to make a new one on boot. However all my settings are the same still and i still cannot uncheck that damned box! Does karmic still use the xorg.conf or am i just going crazy?!

Thanks

Guy

---

### Post by kubug on 2009-11-13
Oh Dang... I just realised that you are on Kubuntu. I am on ubuntu. I really should take the time to read the information more careful. Sorry.

I apologise for sending you on a wild goose chase that wasn't going anywhere. 

Here is a link that discusses what you were asking for: [http://www.tuxmachines.org/node/40388]("http://www.tuxmachines.org/node/40388")

Not that I agree with all the sentiments in the article. I guess the only way for you to get a wallpaper that "stretches" across is to take a dual monitor wallpaper, cut it in half, and use each half on each monitor.

---

### Post by raafe on 2009-11-13
Ahhh dang

Cheers for the help anyway, will just have to GIMP it i guess

Thanks

Guy

---

### Post by cosimo on 2010-11-05
Hey guy,
 As far as I am aware,  KDE took out the option for stretching a wallpaper across both monitors or even having the same wallpaper on both monitors.
Unfortunately  gnome/ubuntu  has done something similar,, With ubuntu you cannot stretch any image across both monitors because some idiot changed the parameters for wallpaper rendering, probably because they only have a laptop :)
  This is a regression on both DE's, and needs to be complained about constantly until the change is reverted.
  Bug reports have been many over and again about this with no change in sight!

coz

---

### Post by Cope57 on 2010-11-05
I know this post does not help the issue, but when you do figure it out, you can check out these wallpapers.

[[SIZE="6"]dmb[/SIZE]]("http://www.dualmonitorbackgrounds.com")

---

### Post by ingramproductions on 2012-01-02
I get my background across both monitors by setting the wallpaper style to span, but I'm on Ubuntu 10.10. I don't know if it's the same for Kubuntu.
Here is a tutorial on how to span the background across 2 monitors:
[http://itswapshop.com/tutorial/how-span-background-image-across-multiple-monitors-ubuntu-1010]("http://itswapshop.com/tutorial/how-span-background-image-across-multiple-monitors-ubuntu-1010")

---

### Post by overdrank on 2012-01-02
Back to sleep thread. Thread closed.

---

