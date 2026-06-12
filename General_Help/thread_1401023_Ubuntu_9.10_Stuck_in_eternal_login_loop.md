---
title: "Ubuntu 9.10 Stuck in eternal login loop"
date: 2010-02-07
forum: General Help
---

### Post by cgoo on 2010-02-07
I posted this in a thread started by Chimmer but since that thread is marked as solved thought I should start a new thread. Problem is that logging in takes me back to the login screen.

From my post on the other thread:

                                                  I have the same problem. I installed Ubuntu 9.10 and reset my screen resolution on Jan. 8, it all worked fine until I ran updates about 2 weeks later when the login loop started. I had set up a guest account which worked for a few more days then went into the loop. I then did a clean install onto a new hard drive, set my resolution, ran updates and the problem returned. I tried this two more times with the same results. Then I did another clean install, set the resolution, ran only the important security updates and login seemed to work fine. Then four days later (Feb. 2) and maybe 8-9 restarts later the problem has returned. I can still log in to the guest account I created on the last install but I don't know how much longer it will work. I posted the problem on yelp but not one reply in four days. I can currently login on a guest account but I know that won't last.

 I have not encrypted any files and have added only a few apps. I tried Chimmer's fix but there is no file named xorg.conf in the ect/x11/ folder. 

 I really want to make this work but with this recurring problem and no support it might have to be bye bye to Ubuntu.


Since that was posted I have new information. After I give my password I get this error.



[   144.172020]  [drm:i810_wait_ring] *ERROR* space: 65520 wanted 65528
[   144.172101]  [drm:i810_wait_ring] *ERROR*  lockup





After that attempt I logged back in to my guest account to find that the icons on the right side of both the top and bottom panels have been rearranged. From previous experience that tells me that next time I try to login as guest it will go into the loop. Thanks in advance for any help you can give.

---

### Post by cgoo on 2010-02-07
Anybody? I know I am not the only one with this problem. I don't want to go back to Microsoft.

---

### Post by cgoo on 2010-02-07
No help from anyone? Not even a comment?

---

### Post by 23dornot23d on 2010-02-07
Have you tried it removing gdm and using kdm as the Display manager .....

I had it loop ..... but on the login screen ..... but 

ctrl + alt + F7 would get me out of it .........

ctrl + alt + F1 would take me to a terminal .... 

login using your username and password here

(This is where I did the gdm remove ..... there is another link I will post here ..... about gdm as you can run the old version)

[http://ubuntuforums.org/showthread.php?t=1400146](http://ubuntuforums.org/showthread.php?t=1400146)

sudo apt-get remove gdm

sudo apt-get install kdm

then enter sudo reboot

rather than you going back to windows ...... it is not that serious we cannot get you working again ....

---

### Post by cgoo on 2010-02-07
Thanks 23dornot23d, it looks like I have things working again. I tried removing gdm2.2 and installing gdm, problem returned. Removed gdm and installed kdm, problem appears to be solved. I'll give it a few days, if problem does not come back I'll mark this thread as solved.

---

### Post by 23dornot23d on 2010-02-10
Glad to know that your system is working as you want it to now ...... thanks for reply ......

Will be happy to see that its still working ok now and this thread marked as solved ........

Cheers ....;)

---

