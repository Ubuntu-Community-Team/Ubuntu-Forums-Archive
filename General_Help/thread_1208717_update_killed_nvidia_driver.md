---
title: "update killed nvidia driver?"
date: 2009-07-09
forum: General Help
---

### Post by lapishc on 2009-07-09
I am runnning a Dell Precision workstation with a nvidia quadro fx 3700 graphics card.  Upon a recent batch of updates and restart somehow my video card drivers have been compromised, I believe. When I boot in I am sent to a prompt asking me to reconfigure my video card.  I am not sure how to do this as I do not see my specific make/model listed.  

Can anyone point me to the correct model to enter or how to patch the nvidia drivers?    

Thanks!

---

### Post by nacho32 on 2009-07-09
could you post a screen shot?

---

### Post by ajgreeny on 2009-07-09
There was a recent kernel update so you may just need to reinstall the nvidia driver for that.

---

### Post by lapishc on 2009-07-09
I have been working on how to install that driver all day!!

From what I can tell, I need the nvidia-glx-180 driver but I can't seem to get that to come up in synaptic or by installing Tweak and then having ubuntu-x grab it.  

I also tried the following...
sudo apt-get -d install nvidia-glx-180
sudo apt-get --fix-broken nvidia-glx-180
sudo apt-get --reinstall nvidia-glx-180

but got the following error...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-180

Any helpyou can lend getting this reloaded will be greatly appreicated!

Thanks

---

