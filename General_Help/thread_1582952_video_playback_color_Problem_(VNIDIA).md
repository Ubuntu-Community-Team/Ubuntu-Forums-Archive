---
title: "video playback color Problem (VNIDIA)"
date: 2010-09-27
forum: General Help
---

### Post by alz3abi on 2010-09-27
Hello every body.

i have installed Ubuntu 10.4 in my PC , my PC comes with NVIDIA, GeForce 9400 GT.

now every thing is okay except my video, colors come wrong, SMplayer, VLC, ... etc.


please how can i fix it, with best regards

---

### Post by alz3abi on 2010-09-27
Open gstreamer-properties from within a terminal.
 ```
gstreamer-properties
```  Now click on the **Video** tab. From the **Plugin** dropdown box select **Custom**. Finally add the following line to the **Pipeline** box.
 ```
videobalance hue=-1 ! autovideosink
```


restart player and every thing comes ok

---

### Post by 3rdalbum on 2010-09-27
This occasionally happens with Nvidia's drivers.

Your video players are probably set to XVideo's output module, which sometimes doesn't work properly with Nvidia's drivers. This is entirely dependent on your Nvidia card and driver version, and seemingly on the current location of the moon.

Basically, your solution is to change the video output module to something else, for instance X11. In VLC, it's Tools > Preferences then click on Video and change the Output from Default to X11. Restart VLC and your videos should be okay.

Use a similar procedure to change SMplayer's output module. You can also change the Gstreamer output module in gconf-editor, if you use Totem or Pitivi or any other Gstreamer-based programs.

---

### Post by jruden on 2011-09-27
> **alz3abi said:**
> 
<.. CUT ..>
restart player and every thing comes ok
Thanks, this works great and restores balance to the err colors! :)

---

