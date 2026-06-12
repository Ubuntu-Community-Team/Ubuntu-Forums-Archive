---
title: "upgraded Swiftfox, now neither swiftfox or firefox will run"
date: 2010-05-15
forum: General Help
---

### Post by AvixK7 on 2010-05-15
I just upgraded to lucid and everything was working fine. I use swiftfox as my browser and realised I hadn't updated it in a while. 

I upgrade swiftfox using their apt repository. once the upgrade was completed neither firefox nor swiftfox will run. I tried uninstalling swiftfox so see if it was conflicting with firefox but it still won't load. Reinstalling firefox doesn't help either.

Any suggestions?? Thanks

---

### Post by TeoBigusGeekus on 2010-05-15
What error messages do you get when you type swiftfox or firefox in CL?

---

### Post by AvixK7 on 2010-05-15
> **TeoBigusGeekus said:**
> What error messages do you get when you type swiftfox or firefox in CL?



************:~$ firefox
Attempting to load the system libmoon 
Segmentation fault

---

### Post by TeoBigusGeekus on 2010-05-15
A quick googling gave me these:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/563036]("https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/563036")
[http://lists.mandriva.com/bugs/2010-02/msg00567.php]("http://lists.mandriva.com/bugs/2010-02/msg00567.php")
A documented bug as you can see...
Try 
```
sudo apt-get purge libmoon
```
in order to completely remove it. See if firefox or swiftfox opens. Then
```
sudo apt-get install libmoon
``` 
to install it again.

---

### Post by AvixK7 on 2010-05-15
purged libmoon. firefox runs. Thank you :)

---

### Post by TeoBigusGeekus on 2010-05-15
> **AvixK7 said:**
> purged libmoon. firefox runs. Thank you :)

Great! Keep in mind that you won't be able to load moonlight/silverlight web pages (not many of them, as the link in my post says) without libmoon.
Have you tried reinstalling it?
Mark the thread as solved anyway...
Keep Ubunting!

---

### Post by AvixK7 on 2010-05-15
thanks,

how do I mark as solved??

---

### Post by AvixK7 on 2010-05-19
It turns out I was wrong Firefox occasionally loads up, but for some reason it's unbearably slow, while, chromium loads up most pages very quickly (video playback is somewhat laggy tho). 

Swiftfox won't load up at at all unless it's feeling lucky. I removed firefox entirely because I usually just stick to swiftfox, but the latter refuses to run properly. When I run swiftfox with CLI, nothing happens, it just returns to the prompt and won't load.

Any ideas?? Swiftfox was perfect in Karmic, it's a shame I can't seem to get it to run now.

Thanks.

---

### Post by lovinglinux on 2010-05-19
See [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

