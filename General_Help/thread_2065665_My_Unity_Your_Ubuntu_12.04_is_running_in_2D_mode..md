---
title: "My Unity: Your Ubuntu 12.04 is running in 2D mode."
date: 2012-10-02
forum: General Help
---

### Post by AndyOpie150 on 2012-10-02
I have an old 2003 SONY VAIO desktop.

When I open up MY Unity I get the following popup message:
 
Your Ubuntu 12.04 is running in 2D mode.
Many features will not be available.

Taken from this thread: [http://ubuntuforums.org/showthread.php?t=2065360](http://ubuntuforums.org/showthread.php?t=2065360)
here is the output of /usr/lib/nux/unity_support_test -p:

```
andrew@Sony-VAIO-PCV-V200G:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x300)
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no
andrew@Sony-VAIO-PCV-V200G:~$ 



```

And lspci -nnk | grep -iA2 vga:

```
andrew@Sony-VAIO-PCV-V200G:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter [1039:6325]
	Subsystem: Sony Corporation Device [104d:811c]
	Kernel modules: sisfb
andrew@Sony-VAIO-PCV-V200G:~$ 

```

Is it possible to install a driver or package that will allow my old computer to have the 3D capability, or is it beyond the ability of the hardware?

---

### Post by Frogs Hair on 2012-10-02
I don't if there is much you can do if no proprietary drivers are available in additional drivers. If there is a Linux 3D driver available from the internet it would have to be installed manually.

There were/are _some_ Windows driver wrappers available for Linux, but I think they are for WIFI only.

---

### Post by AndyOpie150 on 2012-10-02
I had to install ndiswrapper to get my old wireless card to work.

Well............maybe someone will post here with more info as to weather or not it's possible.

---

### Post by vasa1 on 2012-10-02
Isn't there a sort of "minimum CPU" requirement as well? Or it just a matter of drivers?

---

### Post by AndyOpie150 on 2012-10-02
Your probably right. But haven't seen a definitive answer as to the minimum requirements.

Edit: I have an Intel Pentium 4 at 2.80GHz
1GB of RAM (after adding 500MB's).

---

### Post by AndyOpie150 on 2012-10-02
WOW! I jumped into a big quagmire full of mines. I thought I would see if updating the graphics driver might help. Even went to the manufacturers site (SIS). Left me so confused as to what driver I should install with Ubuntu 12.04 and the 3.2.0-31-generic-pae kernel.

---

### Post by ezsit on 2012-10-02
With those specs I would not even try to run in 3D.

---

### Post by vasa1 on 2012-10-02
> **AndyOpie150 said:**
> WOW! I jumped into a big quagmire full of mines ...

What are your future plans for this machine? Do you intend to stay on 12.04 LTS or will you move to 12.10? In 12.10, Unity 2D has been "killed off". It's just going to be Unity.

My suggestion is not to do anything for a couple of months but keep up with the feedback on how Unity in 12.10 plays on older boxes.

---

### Post by AndyOpie150 on 2012-10-02
Great, no 2D in 12.10! 
Jobless right now. Looks like it will be a while (construction laborer with no other marketable skills). This old box is all I got. Beats using the phone though (3.2 inch screen and virtual keyboard).
 
Thanks for the info.
 
Can't mark this thread as solved, but it has run it's course. EDIT: Actually I can mark it as solved as my Question was answered.

---

### Post by vasa1 on 2012-10-02
Andy, you should consider installing a lighter version of Ubuntu when 12.10 comes around in less than a month.

While Lubuntu appears the lightest, IMO, support is a bit thin. Xubuntu is marginally "heavier" but support in this forum and by way of documentation is not in short supply.

---

### Post by AndyOpie150 on 2012-10-03
I've tried all four of the Ubuntu distro's. They all work just fine on my machine. I like Lubuntu, but I like Kubuntu even more, I like my EYE CANDY. I have Conky lua and Slidewall. I like the 3D cube and wobbly windows, but their not going to work on my machine. I like to really make my machine my own through customization programs. 

I'm using Ubuntu right now because I liked the look of Unity, just didn't realize it made all the other web sites pages to large to see fully, causing me to scroll left and right constantly or resize (but that makes them hard to read). After install I ended up within a couple of days dropping back to Gnome classic so the pages would look normal again. 

I figure I'll stick with Ubuntu until I'm a little more Linux proficient, then switch to Kubuntu (it seems a little harder to navigate and accomplish tasks, but it does have all the bells and whistle's already installed).

---

### Post by haresear on 2012-10-03
I have old hardware and even Unity 2D feels sluggish. Gnome classic runs okay, but the future of that option seems questionable. I've found that Mint 13 with Mate runs nicely and is very familiar if comming from Gnome classic. I actually like it better than Gnome classic. Kubuntu also runs fine if I turn off all effects, and yet is full-featured. Just not quite as familar as Mint. I think I will be following Mint and Kubuntu in the future.

---

### Post by thebunn81 on 2013-09-17
MyUnity thinks that it's in 2D mode if there are any users running in 2D mode. I'm in Unity (running with OpenGL in 3D) but since I have xrdp sessions running too, it thinks that it's in 2D.

[https://bugs.launchpad.net/myunity/+bug/959825](https://bugs.launchpad.net/myunity/+bug/959825)

---

