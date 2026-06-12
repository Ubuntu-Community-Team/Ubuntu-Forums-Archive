---
title: "Updating packages broke Gnome 3?"
date: 2011-05-07
forum: General Help
---

### Post by smarmytime on 2011-05-07
I've been running Gnome 3 for the past few days, and enjoying it - I like it a lot better than Unity, and would like to keep using it. But I guess it doesn't automatically let you know when packages need to be updated, so earlier today, I logged into a virtual terminal (I believe that's the right expression, but please correct me if I'm wrong - it was a full screen terminal, and I got there by pressing Cntl-Alt-F1), and it said 48 packages needed to be upgraded. So I ran sudo apt-get update, then sudo apt-get upgrade. The system did the package upgrades, then told me I needed to reboot to finish the upgrades, which I did...but then when I tried to log into Gnome, it said "Failed to load session "Gnome"". 

Distressing. 

So, I guess I must have broken a Gnome dependency...how do I start troubleshooting this? And how do I make sure it doesn't happen again?

---

### Post by pritam_par on 2011-08-06
I too have faced the same problem. If you are using Ubuntu 11.04, then at the login screen change the Desktop environment to Ubuntu classic to Ubuntu. You will be able to login to the Gnome with Unity.

___________________________________________________________________________
[My blog on Opensource]("http://http://opensource-sidh.blogspot.com/")

---

