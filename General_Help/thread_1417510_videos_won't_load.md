---
title: "videos won't load"
date: 2010-02-27
forum: General Help
---

### Post by mitch534 on 2010-02-27
well i'm using (Ubuntu 8.04 _Hardy Heron) and every time i try to watch a video all i see is black, i installed vlc, and mplayer, and i still just get black every time i go on youtube

---

### Post by mitch534 on 2010-02-27
all of the plugins i have are listed here

**Shockwave Flash**

libibflashplayer.so**Default Plugin**

  libnullplugin.solibnullplugin.s**Demo Print Plugin for unix/linux**

 libunixprintplugin.so**Java(TM) Plug-in 1.6.0_17-b04**

libjavaplugin_oji.so**VLC Multimedia Plugin**

**Totem Web Browser Plugin 2.22.1**

**Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)**

**VLC Multimedia Plugin (compatible Totem 2.22.1)**

**Windows Media Player Plug-in 10 (compatible; Totem)**

**DivX® Web Player**

**QuickTime Plug-in 7.2.0**

**iTunes Application Detector**

**Silverlight Plug-In**

---

### Post by mitch534 on 2010-02-27
Bump

---

### Post by mitch534 on 2010-02-27
Bump

---

### Post by synapsys on 2010-02-27
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by mitch534 on 2010-02-27
i already have it, i can't find out whats wrong i hate ubuntu it sucks  :( and no one can help me i've been tring for almost a month to fix this but nothing

---

### Post by davec64 on 2010-02-27
```
sudo apt-get install ubuntu_restricted_extras
```

You'll need the multiverse reposuitory selected. That should install all the required DVD bits and bobs.

Also you could try turning off desktop affects as that may be causing problems.

---

### Post by mitch534 on 2010-02-27
i have all the restricted extra's also, i've honestly tried everything i don't know mabey some of my plugins are conflicting but i don't know, i'm not all that experinced with ubuntu

---

### Post by mitch534 on 2010-02-27
**Shockwave Flash**

 File name:  libflashplayer.so Shockwave Flash 9.0 r262this plugin lets my youtube videos load to black none of the other plugins do anything for youtube or any other video

---

### Post by mitch534 on 2010-02-27
bump

---

### Post by indiana_crook on 2010-02-27
> **mitch534 said:**
> i have all the restricted extra's also, i've honestly tried everything i don't know mabey some of my plugins are conflicting but i don't know, i'm not all that experinced with ubuntu

Post your system specs...

---

### Post by mitch534 on 2010-02-27
well, i can't honestly find them out because my brother rebuilt my computer from a bunch of different ones, but ubuntu used to work perfectly fine on it, just this time it won't run videos

---

### Post by indiana_crook on 2010-02-27
> **mitch534 said:**
> well, i can't honestly find them out because my brother rebuilt my computer from a bunch of different ones, but ubuntu used to work perfectly fine on it, just this time it won't run videos

Post the results of:

```
sudo lshw -C Video
```

---

### Post by mitch534 on 2010-02-27
*-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/i1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 6a
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=32

---

### Post by mitch534 on 2010-02-27
bump

---

### Post by indiana_crook on 2010-02-27
> **mitch534 said:**
> *-display UNCLAIMED     
       description: VGA compatible controller
       product: CyberBlade/i1
       vendor: Trident Microsystems
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 6a
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-2.0 pm vga_controller bus_master cap_list
       configuration: latency=32

K... what kind of computer, desktop, laptop, netbook? How long have you been using Ubuntu?  Is it a fresh install? It looks like the kernel does not recognize it.

---

### Post by mitch534 on 2010-02-27
i can't remember the computers name, theres nothing on it that i can find it's name, it is a desktop and it's had Ubuntu for 1-2 years

---

### Post by mitch534 on 2010-02-27
bump

---

### Post by indiana_crook on 2010-02-27
> **mitch534 said:**
> i can't remember the computers name, theres nothing on it that i can find it's name, it is a desktop and it's had Ubuntu for 1-2 years

thats strange that it just up and stopped working... if you have any desktop effects enabled try turning them off. (Use Metacity instead of Compiz) I would also recommend an NVIDIA graphics card.

---

### Post by mitch534 on 2010-02-27
i don't think i even have a working graphic's card in it

---

### Post by davec64 on 2010-02-27
Going back a few posts you said you had shockwave flash 9..... . The latest is 10.0 r45. 
What about installing and trying the newsest version from the adobe site?

---

