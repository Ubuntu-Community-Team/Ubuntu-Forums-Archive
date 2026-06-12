---
title: "Screen resolution woes making me angry.... raaaaaggghhh"
date: 2010-04-12
forum: General Help
---

### Post by rflook on 2010-04-12
Hi there,

I have been battling with my mythbuntu box now for bloody ages and am wishing to throw it out a window at the moment. In a nutshell there is something fudging annoying with my screen resolution which i cant for the life of me figure out.

Here goes

1) When it logs in intially the log in screen is completely out of proportion, its massive, you can probably see the top left quarter of it and that it. This is annoying but not the worlds biggest problem as 
2) My machine logs straight in to mythtv where the resolution is (almost normal). 1380 x 768 i believe. Unfortunately the resolution does not fill the entire screen, there is an area down the right hand side of my samsung tv which is black (evidently the resolution is not filling the screen fully). If I drop out of mythtv into the xfce desktop and change my resolution to 1024x768 it fills the entire screen, but everything has become stretched, bah.

What should I do as its driving me up the wall :-(

---

### Post by rflook on 2010-04-12
OK so brief update, I backed up my old xorg.conf file and recreated using xserver-xorg. It all started a bit wrong with crappy resolutions on display, but after selecting what I believe to be the right nvidia driver and having a fiddle with the Display Settings and Screens and Graphics options I have xfce running in 1024x768 @ 53, it fills the screen nicely and even more of a bonus the log in screen seems to be happily sitting in full view with all options available to me - happy days - sort of.

Now all i need to do is to somehow get my desktop resolution sorted. It would seem that fiddling about with the screen settings in Screens and Graphics can cause the log in window to resize, i say this because changing the resolution size in the Display Settings seems to make no difference to the log in window, only to the main xfce desktop. 

So I guess my problem is to do with getting the right settings in the Display settings, but I cant get over 1024x768 without seemingly screwing up my log in screen.

Its doing my head in trying to figure this out

---

### Post by WinterRain on 2010-04-12
Did you change your settings by:
```
gksudo nvidia-settings
```
?

---

