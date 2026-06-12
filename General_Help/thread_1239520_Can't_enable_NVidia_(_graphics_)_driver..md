---
title: "Can't enable NVidia ( graphics ) driver."
date: 2009-08-13
forum: General Help
---

### Post by credobyte on 2009-08-13
Video card:
```
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
```Installed:
```
nvidia-glx-173

```After rebooting my PC, NVidia drivers are still not enabled and I can't enable them via Hardware drivers window - nothing happens when I click Activate.
What I need to do to enable them ? 8-[

---

### Post by SPr on 2009-08-13
Have you installed the nVidia kernel? It should be in the repos.
```

aptitude install nvidia-kernel-$(uname -r)

```
or
```

apt-get install nvidia-kernel-$(uname -r)

```
depending on your preferences.

Edit:
> 
Your system has achieved a perfect TruStealth rating. Your system ignored and refused to reply to repeated Pings (ICMP Echo Requests).

My cat knows more about PC security than Gibbo.

---

### Post by credobyte on 2009-08-13
I can't seem to find anything similar to what you said .. 
```
E: Couldn't find package nvidia-kernel-2.6.28-14-generic

```

```
dainis@credobyte:~$ sudo aptitude search nvidia | grep kernel
i A nvidia-173-kernel-source        - NVIDIA binary kernel module source
p   nvidia-180-kernel-source        - NVIDIA binary kernel module source
p   nvidia-71-kernel-source         - NVIDIA binary kernel module source
p   nvidia-96-kernel-source         - NVIDIA binary kernel module source
i   nvidia-kernel-common            - NVIDIA binary kernel module common files
v   nvidia-kernel-source            -

```

All I can find is nvidia-kernel-common, which resulted in ( no changes ):

[IMG]http://i29.tinypic.com/qn5xsk.png[/IMG]

P.S. - cats don't talk :p

---

### Post by sblunix on 2009-08-13
> **credobyte said:**
> I can't seem to find anything similar to what you said .. 
```
E: Couldn't find package nvidia-kernel-2.6.28-14-generic

```

```
dainis@credobyte:~$ sudo aptitude search nvidia | grep kernel
i A nvidia-173-kernel-source        - NVIDIA binary kernel module source
p   nvidia-180-kernel-source        - NVIDIA binary kernel module source
p   nvidia-71-kernel-source         - NVIDIA binary kernel module source
p   nvidia-96-kernel-source         - NVIDIA binary kernel module source
i   nvidia-kernel-common            - NVIDIA binary kernel module common files
v   nvidia-kernel-source            -

```

All I can find is nvidia-kernel-common, which resulted in ( no changes ):

[IMG]http://i29.tinypic.com/qn5xsk.png[/IMG]

P.S. - cats don't talk :p
```
sudo nvidia-xconfig
```???

---

