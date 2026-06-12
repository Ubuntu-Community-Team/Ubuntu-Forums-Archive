---
title: "Unity 3D on D620"
date: 2012-04-11
forum: General Help
---

### Post by Cpierce on 2012-04-11
I have a Dell D620 with the nVidia M110 graphics card. I have been able to run compiz and 3D graphics in the past with no issues. I installed 12.04 beta 2, and found that I have Unity 2D. I found this command and ran it. 


chuck@chuck-Latitude-D620:~$ /usr/lib/nux/unity_support_test -pOpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7300/PCIe/SSE2
OpenGL version string:  2.1.2 NVIDIA 295.33

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
chuck@chuck-Latitude-D620:~$ 


It basically says that Unity 3D is not supported. Is there a setting that needs to be changed, or a file that needs to be installed ? I would be disappointed if Unity would have to use that much resources.

Can anyone help ?

---

### Post by idoitprone on 2012-04-11
the nvidia driver has been blacklisted, use nvidia 173 or nouveau

see this bug report
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745)

and this thread

[http://ubuntuforums.org/showthread.php?t=1863880](http://ubuntuforums.org/showthread.php?t=1863880)

---

### Post by jadtech on 2012-04-11
well I don't quite have the same card how ever  I found after I loaded and installed the vender driver recommended even though I still find I need to boot in unbuntu 2d , 3d is working well what is not working is acceleration though I am only running 11.10 .

---

### Post by idoitprone on 2012-04-11
> **jadtech said:**
> well I don't quite have the same card how ever  I found after I loaded and installed the vender driver recommended even though I still find I need to boot in unbuntu 2d , 3d is working well what is not working is acceleration though I am only running 11.10 .

ur card nvidia m110 is probably a rebranded card

use 

```
lspci 
```

to check

but
> chuck@chuck-Latitude-D620:~$ /usr/lib/nux/unity_support_test -pOpenGL vendor string:   NVIDIA Corporation
** OpenGL renderer string: GeForce Go 7300/PCIe/SSE2**
OpenGL version string:  2.1.2 NVIDIA 295.33the command showed the name of your card

---

### Post by jadtech on 2012-04-11
naa my dell has the amd ati

---

### Post by idoitprone on 2012-04-11
> **jadtech said:**
> naa my dell has the amd ati

crp it one of those strange moments when i thought i replied to the op but its to another person lol:lolflag:

---

### Post by Cpierce on 2012-04-11
idoitprone

I went to additional drivers and uninstalled nvidia-current. Then I went back to additional drivers and nvidia 173 nor nouveau are listed as an option. So I went to synaptic and saw nvidia 173, but it comes up as a broken package as soon as I check it. 

How do I get one of these installed ?

---

### Post by Cpierce on 2012-04-11
I think I got it fixed. When I uninstalled nvidia-current, it looks like it installed nouveau by default. I went into synaptic and installed the nouveau nvidia firmware. I then modified the /etc/environment file with "sudo gedit /etc/environment" and added
"UNITY_FORCE_START=1" to the file and saved it.

It appears to be working and I can make adjustments with "myUnity"

Thanks everyone.

---

