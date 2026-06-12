---
title: "Dual monitors won't work"
date: 2012-01-16
forum: General Help
---

### Post by SynthErik on 2012-01-16
Hello everyone!

I've got this problem. I have two screens connected to my computer, and in Windows it all works fine, but in Ubuntu it doesn't work at all.

At first I tried to change the xorg config-file myself, but of course that lead to the x-server crashing. I then tried doing it with nVidia's tool, but that failed to, but at least my second screen then got signals, only that I got mirrored screens instead of extended screens. This was 11.04. I then changed to 10.04.

Now, Ubuntu's monitor configuration program (System->Preferences->Monitor) doesn't find the second monitor at all and nVidia's tool won't let me configure anything at all. It complains about not finding the configuration file, even though I've created one with nvidia-xconfig. The xorg.conf file created also crashed the x-server.

Also, here's my xrandr-print:
```

Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

```

So, my question is if anyone can help me with this?

Thanks in advance!

---

### Post by dino99 on 2012-01-16
well you dont talk about which model of monitors you are using; are they both LCD ?

As the kernel deals directly with X, custom xorg.conf can kill the server as it conflict. So as a rule, ONLY use archive driver and tools provided by ubuntu.

sudo synaptic:
- purge ALL the nvidia installed packages
- purge jockey-gtk
- reinstall nvidia-current & nvidia-settings & jockey-gtk

reboot
sudo jockey-gtk (to check driver activation)
sudo nvidia-settings ( to set your dual monitors settings)

reboot

---

### Post by SynthErik on 2012-01-16
Yes, they are both LCD, they're not the same brand though, but that shouldn't affect, right?

Anyways, so I did what you said and the results are this:
jockey-gtk says that the driver nvidia_current is "active but not currently in use".
nvidia-settings still complains about the missing xorg.conf file, and wants me to create one with nvidia-xconfig. So I do that, I restart the x-server and it crashes again.

---

### Post by SynthErik on 2012-01-17
Come on, someone ought to be able to help me with this?

---

### Post by Neill_R on 2012-01-17
I had the devil of problems trying to get an old VGA card to work. Did not get much help I am affraid to say gave up and got a different graphics card.

tell people what your setup is that way they might be able to help what does the Xorg.0.log file say?

---

### Post by Grenage on 2012-01-17
> **SynthErik said:**
> Come on, someone ought to be able to help me with this?

Greetings; it's been a while but I'll throw in what I can.  Firstly, if you're running nvidia-settings as root (gksu nvidia-settings) and you're using the recommended Nvidia driver (installed via the additional drivers menu), I would expect it to work.  It looks like you've probably exhausted that avenue, so if so, we'll try a different angle.

Please post the output of these commands:

```
xrandr -q
```
```
lspci | grep VGA
```

Please also post the monitor brands and models, and the connection types you are using; this should give us plenty of information.

---

### Post by SynthErik on 2012-01-17
> **Neill_R said:**
> I had the devil of problems trying to get an old VGA card to work. Did not get much help I am affraid to say gave up and got a different graphics card.

tell people what your setup is that way they might be able to help what does the Xorg.0.log file say?

Well, I'm not giving up and getting another graphics card, I wasn't even going to buy this one... (integrated HD graphics in my CPU, forgot to check motherboard for video ports..)

Anyways, what setup do you mean? I've posted the outcome from xrandr in my first post.

My log file says a lot of things, I don't really know how to sort things out of it.. But it doesn't say anything about a second monitor, that's for sure. Last entry is "Fatal server error: no screens found"


> **Grenage said:**
> Greetings; it's been a while but I'll throw in what I can.  Firstly, if you're running nvidia-settings as root (gksu nvidia-settings) and you're using the recommended Nvidia driver (installed via the additional drivers menu), I would expect it to work.  It looks like you've probably exhausted that avenue, so if so, we'll try a different angle.

Please post the output of these commands:

```
xrandr -q
```
```
lspci | grep VGA
```

Please also post the monitor brands and models, and the connection types you are using; this should give us plenty of information.

Right. Output from xrandr -q:

```

Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  

```

lspci | grep VGA:
```

01:00.0 VGA compatible controller: nVidia Corporation Device 1245 (rev a1)

```

My brands and models are Samsung, Syncmaster E1920NR and Fujitsu Siemens, unknown model (I didn't buy iy myself. It's a bit older than the Samsung though.)

---

