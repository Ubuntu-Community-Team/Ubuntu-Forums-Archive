---
title: "ubuntu 10.04: NVIDIA drivers"
date: 2012-04-29
forum: General Help
---

### Post by yaami on 2012-04-29
Hi all,

I'm trying to install the NVIDIA drivers. I added _*ubuntu-x-swat*_ to apt sources.list and installed _*nvidia-current*_. And ran the _*nvidia-xconfig*_ program. It created the X11 conf file (attached). But every time I power on the system it displays EE no device detected and goes to the low graphics mode. I'm using a _*Lenovo Y470*_.

```
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
** 01:00.0 VGA compatible controller: nVidia Corporation Device 0df6 (rev a1)**

``````

$ nvidia-detector 
none

```

pls let me know how this can be fixed or any pointers where I should start.

Thanks,

---

### Post by dino99 on 2012-04-29
Intel is not Nvidia  :lolflag:

****VGA compatible controller: Intel  *****

xserver-xorg-video-intel is your graphic driver (install it via synaptic)

---

### Post by yaami on 2012-04-29
> **dino99 said:**
> Intel is not Nvidia  <img src="images/smilies/smiley-faces-75.gif" border="0" alt="" title="LOL" smilieid="72" class="inlineimg" /><br />
<br />
****VGA compatible controller: Intel  *****<br />
<br />
xserver-xorg-video-intel is your graphic driver (install it via synaptic)<br />
<br />



I also have a NVIDIA GEFORCE 555m card (hybrid graphics...)
> **yaami said:**
> 
```
$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
** 01:00.0 VGA compatible controller: nVidia Corporation Device 0df6 (rev a1)**

```



 which can be turned on and off (works well in windows)... Any ways Looks like my laptop Y470 and Y570 are different [http://linux-hybrid-graphics.blogspot.com/2012/02/nvidia-optimus-lenovo-ideapad-y570.html](http://linux-hybrid-graphics.blogspot.com/2012/02/nvidia-optimus-lenovo-ideapad-y570.html)....

[http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-Ideapad-Y470-Nvidia-GPU-100-Any-Linux/td-p/507171](http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-Ideapad-Y470-Nvidia-GPU-100-Any-Linux/td-p/507171)

Thanks.

---

### Post by blitzit on 2012-04-29
If you are trying to install proprietary NVIDIA drivers, you will need to disable all ubuntu-drivers and blacklist a few of them.

I have been running a NVIDIA-8400GS successfully with ubuntu 10.04 for the last 2 years with this method, before upgrading to 12.04.

I am presently using NVIDIA-Linux-x86-295 with ubuntu 12.04.

---

### Post by fabio.hipolito on 2012-05-14
Hi,

In my Y470 I run Ubuntu 12.04 and use bumblebee for the nvidia support.

Check the [bumblebee project]("http://www.bumblebee-project.org/install.html#Ubuntu") and install it.

After that I continue to have a problem, but solved it with this work around by [Lekensteyn]("https://github.com/Bumblebee-Project/bbswitch/tree/ec42e5b7ad3643a94fedf325cd7ec21a0ad5e712").

Cheers.

---

