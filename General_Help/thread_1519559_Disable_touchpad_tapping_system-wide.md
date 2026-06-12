---
title: "Disable touchpad tapping system-wide?"
date: 2010-06-28
forum: General Help
---

### Post by carn1x on 2010-06-28
I would like to disable touch pad tapping system wide, this includes on the login screen, is this possible? 

No matter how many times I try, either my hands are too fat or my touch pad is badly designed (Only an Acer) but almost every time I login the focus switches out of the password textbox!

I have gone the steps to disable it after logging in, described on this page:

[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Thanks in advance :)

---

### Post by Brandon Williams on 2010-06-28
Have you tried the instructions for [UDEV (10.04)](https://wiki.ubuntu.com/X/Config/Input#Input Configuration with udev (Ubuntu 10.04)) and/or [HAL (8.10 to 9.10)](https://wiki.ubuntu.com/X/Config/Input#Input Configuration with HAL (Ubuntu 8.10 to 9.10))? These work for me.

---

### Post by carn1x on 2010-06-30
Hi,

Your links definitely got me started, thanks.

I also used the following 2 links to nail the problem down and solve it:

[http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html]("http://ubuntu-snippets.blogspot.com/2009/03/multi-touch-for-anyall-synaptics.html")

[http://wiki.archlinux.org/index.php/Touchpad_Synaptics]("http://wiki.archlinux.org/index.php/Touchpad_Synaptics")

To anyone else trying this, I found I had to run:

```
sudo /etc/init.d/hal restart
```

to get the changes to apply (didn't want to restart my system, however logging out and back in didn't work as suggested somewhere).

Thanks :D

---

