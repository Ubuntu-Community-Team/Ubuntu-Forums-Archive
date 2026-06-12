---
title: "Setting Powermizer to Prefer Maximum Performance"
date: 2010-07-11
forum: General Help
---

### Post by Adam24367 on 2010-07-11
Hello all. I'm pretty new at Linux, the only other experience with it was when I had Debian and Fedora installed on my PS3 

My problem is with powermizer. My graphics card is an Nvidia 8700M GT. The current drivers for have a feature called powermizer, for those who dont know what powermizer is, powermizer steps down the speed of your graphics card when it is not being used. The problem with this is that whenever it steps up or down, it causes a flicker on my screen. This can happen several times a minute. The only way to fix this is by disabling Powermizer (Which I have heard to be quite difficult on linux systems) or setting the Preferred Mode in NVIDIA X Server Settings to "Prefer Maximum Performance". I Chose the latter to fix my problems and so far I have had no screen flickers. It is annoying and tedious to go to System>Admin>NVIDIA X Server Settings>etc to fix the problem every time I restart the computer. I was wondering if there is any way to get it to set Prefer maximum performance every time the computer starts up.

EDIT: I forgot to tell you Im using 10.04 LTS

Thanks
:)

---

### Post by ov3rcl0ck on 2010-07-11
I think you have to set it as root, open it as root with this command:
```

sudo nvidia-settings

```

If that doesn't work to to the bottom that says "nvidia-settings configuration" or something of the sort, and turn off the interval for powermizer, then save the current configuration.

---

### Post by Monkeystador on 2010-07-30
Try here: [http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html)

---

