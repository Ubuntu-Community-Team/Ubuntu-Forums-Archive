---
title: "New VirtualBox Help"
date: 2011-06-28
forum: General Help
---

### Post by Voldas on 2011-06-28
Hello and id like to thank every one in advanced for helping me. Okay lets get started I am running virtualbox on a mac (osx 10.5.8 ) and I downloaded the new VirtualBox today 4.0.10 and when I had 3d enabled on the screen  would go all weird and it wouldn't let me do any thing. I could log in, but after I did so I could see the background and it would switch from that to a white screen. when I logging in with ubuntu classic mode with 3d enable off it worked fine and I am not sure what to do because I really like the launcher. Thank you again in advance.

---

### Post by e79 on 2011-06-28
To enabled the 3d effect in you Ubuntu 11.04 (I assume this is what you want - to have access to Unity UI), make sure that in your machine settings you allocated 128MB ram to your video memory and you ticked the 'Enable 3D Acceleration'. Once in Ubuntu, make sure to install the 'Virtual Box Guest Additions' from the Extension pack found on their website and then restart your guest machine.

Hope this helps

---

### Post by Voldas on 2011-06-28
Thank you for the help but this didn't work when i added the new additions but they  didn't help it still does weird stuff and wont let me work on anything but classic mode. Not that I don't like classic but i still like the new unity bar better. Here are some photos (Don't know if they posted)

---

### Post by e79 on 2011-06-28
If you are on the latest version of Virtual Box (4.0.10) and the same goes for the Virtualbox Guest additions and still having issues, maybe this link could help you, at the bottom it says :

> 
If the panel and applications appear gray and unthemed, [gnome-settings-daemon is crashing]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/728803"). You can work around this bug by restarting it:
# killall gnome-settings-daemon
# gnome-settings-daemonor you could try to run Unity in 2D and select it upon login :
[http://www.ubuntugeek.com/install-ubuntu-unity-2d-using-ppa-in-ubuntu-11-0410-10.html](http://www.ubuntugeek.com/install-ubuntu-unity-2d-using-ppa-in-ubuntu-11-0410-10.html)

---

### Post by Voldas on 2011-06-28
For the first thing you posted I did have this problem befor and I thought it was something I had to live with so I went on using it could this mean my daemon crashed and is no longer able to use the unity with 3d option?
As for the second thing you had in the post  I tried it and it still didn't work. Thank you though for being the only one who responded to my post.

---

### Post by e79 on 2011-06-28
> **Voldas said:**
> For the first thing you posted I did have this problem befor and I thought it was something I had to live with so I went on using it could this mean my daemon crashed and is no longer able to use the unity with 3d option?
As for the second thing you had in the post  I tried it and it still didn't work. Thank you though for being the only one who responded to my post.

No I don't think your gnome-setting-daemon is no longer usable, probably just need a restart once you are in Unity. Once loggeg in, try :

1. Alt-F2 - to bring up a 'Run Application' menu
2. type the following :  gnome-settings-daemon

and see how it goes

As for the Unity 2D, couldn't you find it in your UI menu at the login prompt ?

---

### Post by Voldas on 2011-06-28
Sorry but no this did not work. would it be better if i just did a brand knew install of ubuntu and deleted this one of virtualbox? Also i could not find the the 2d unity thin of the login menu. Thank you.

---

### Post by e79 on 2011-06-28
You can always try, Ubuntu install takes 20 min or so anyway, so not big of a deal. As for Unity 2D, it might be called 'Unity Qt' as the link from ubuntugeek states. As I don't have a MAC, I'm beginning to wonder if its related to their hardware in some way (or the OS maybe).

---

### Post by Voldas on 2011-06-28
Thank you for all your help and I will try this and I am not sure but I think it might be with the Virtualbox because it just came out today so ill try downgrading it first if I even can. Thank You again.

---

### Post by e79 on 2011-06-28
> **Voldas said:**
> Thank you for all your help and I will try this and I am not sure but I think it might be with the Virtualbox because it just came out today so ill try downgrading it first if I even can. Thank You again.

Good idea, tell us how it goes; must admit I ran out of ideas as Unity works fine for me under virtualbox running over ubuntu or windows

No need to thanks as I am unable to help you as I would like :(

---

### Post by Voldas on 2011-06-29
The downgrade worked i downgraded to Virtualbox 4.0.6 and at first it had a funny screen real glitchy but after awhile it worked fine. :D

---

### Post by e79 on 2011-06-29
Great, we'll know for next time same problem arise !

I'm glad you could fix it

Regards

---

