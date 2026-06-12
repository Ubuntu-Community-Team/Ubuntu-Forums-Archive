---
title: "Information about Nvidia optimus support"
date: 2012-07-02
forum: General Help
---

### Post by Mahler122 on 2012-07-02
Hello All,

I've been browsing the web for information regarding muxless graphics (aka Optimus) with new NVIDIA discrete graphics chips. The results have been alright, however I feel like there is a lack of aggregation of this information. 

My setup is the following:

MSI GT70 laptop with,
Ivy Bridge i7-3610QM cpu with HD4000 iGPU (integrated GPU), and
nvidia GTX 675m dGPU (discrete GPU)

Currently with the latest [nvidia binary blob and bumblebee]("https://wiki.ubuntu.com/Bumblebee"), I get the following error when I try to use 'optirun'

```

[ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to assign any connected display devices to X screen 0

[ERROR]Aborting because fallback start is disabled.

```

This shows you that the issue is a little more deep than just nvidia not providing support. It seems like some changes are needed to Xorg in order to allow this kind of thing to work.

In fact it seems that the way a lot of laptops like mine with gtx 6xx discrete chips are wired, is for the dgpu to [copy it's rendered image into the memory of the igpu]("http://www.trustedreviews.com/opinions/nvidia-optimus-explained_Page-2") on intel's chip. This is new, and there will need to be some software changes in linux before proper drivers can be written. There is already progress being made though on both fronts it seems!

In the kernel world, there is ['DMA-BUF']("http://www.phoronix.com/scan.php?page=news_item&px=MTA0ODE"), which would be the ideal case. This way NVIDIA could do something much closer to what is [happening on windows]("http://www.trustedreviews.com/opinions/nvidia-optimus-explained_Page-2"). However there are the much heard of conflicts with the [closed-source nature]("https://lkml.org/lkml/2012/1/17/479") of NVIDIA's software.

Another way is being pursued by david airlie in the form of enhancements to the xorg server and freedesktop drivers to allow gpu offloading, which he is calling PRIME. [here]("http://people.freedesktop.org/~airlied/prime-notes.txt"), [here]("http://www.youtube.com/watch?v=XEUKuNTRp78"), and [here]("https://github.com/Bumblebee-Project/Bumblebee/issues/185#issuecomment-6582552").

I'm sitting here eager to test new software to get this stuff working however I'm not sure what is current or if anyone has tried various things before, so I'm creating this thread for this purpose. If anybody has any information about new software please post it here. I should mention that I would like to try the prime notes mentioned [here]("http://people.freedesktop.org/~airlied/prime-notes.txt") like [this]("https://github.com/Bumblebee-Project/Bumblebee/issues/185#issuecomment-6582552") guy, however I get the following error when cloning the mesa git tree he has.

```

matthew@sibelius:~/Sources$ git clone git://people.freedesktop.org/~airlied/mesa mesa_prime
Cloning into 'mesa_prime'...
remote: Counting objects: 496561, done.
remote: error: unable to find 536cb264f64e90e4123ad30b4cf0a155244c0eb0
remote: error: unable to find 77ed5b4ff21d5a99313380db94ff58b6d2a0be6a
remote: error: unable to find a91bdb3499de0eef0197803410a19f53f70cad51
remote: Compressing objects: 100% (91027/91027), done.
remote: fatal: unable to read 536cb264f64e90e4123ad30b4cf0a155244c0eb0
remote: aborting due to possible repository corruption on the remote side.
fatal: early EOF
fatal: index-pack failed

```

So, I'm waiting until something I can test is ready.

I will edit this post to make it more readable and contain more information such as links as they become available. Hopefully soon I will be able to post how to get it working.

---

### Post by Lekensteyn on 2012-07-03
Mesa is just one patch. Clone from git://anongit.freedesktop.org/mesa/mesa and apply [this patch](http://cgit.freedesktop.org/~airlied/mesa/commit/?h=444159aae6a0a9b9cc0514f34ba754469b0d2dc2) on it (I'm using the master branch, but 8.x.x should be fine too).

Something to keep in mind: when building the xf86-video-{intel,nouveau} drivers, you need to install the new X stack first. Otherwise, the compilation will pick up the old headers, causing X to segfault.

---

### Post by Mahler122 on 2012-07-04
Actually, I found out from airlie himself that his mesa git repository is a remote of the real mesa tree so I should first clone the original mesa tree, then attach his repo as a remote, then pull from it. This worked.

However I'm now having typical build problems which result from not knowing exactly what you're doing..

Maybe I'm being a bit too optimistic, but I'm trying to build X alongside the X which ubuntu set up. I figured I could isolate the build environment, build, then setup the correct LD_LIBRARY_PATH and PATH variables so that when I call X, it calls the new version. I could then shut down my current X, change environment and start the new X. Do you think it's possible to actually have this work in the end?

Right now it's crashing and giving an error related to XKB.

---

### Post by idoitprone on 2012-07-04
Two things

first install bbswitch

```
sudo apt-get install bbswitch
```

this allow you to shutoff your nvidia card when it not in use

believe me, it will stop that noisy fan

second

I only got nvidia optimus working on open drivers. Nvidia support just sucks

---

### Post by dino99 on 2012-07-04
Please send your complaint to nvidia for their documentation helping on linux.

[http://www.phoronix.com/scan.php?page=news_item&px=MTEyMTc](http://www.phoronix.com/scan.php?page=news_item&px=MTEyMTc)

---

### Post by Mahler122 on 2012-07-04
> **idoitprone said:**
> Two things

first install bbswitch



I've had that installed for a while, although cooling on this laptop is pretty good so The fan wasn't very much louder before I had bbswitch.

> **idoitprone said:**
> 
I only got nvidia optimus working on open drivers. Nvidia support just sucks

Yeah, at the moment I'm just trying to reproduce the open source work. I want to see that this works in principle on my machine too.

---

### Post by idoitprone on 2012-07-04
```
cat /proc/acpi/bbswitch
```

?


nouveau driver does not support your card yet

---

### Post by Mahler122 on 2012-07-05
```

matthew@sibelius:~$ cat /proc/acpi/bbswitch 
0000:01:00.0 OFF
```

> **idoitprone said:**
> 
nouveau driver does not support your card yet

This is unclear: 
[http://nouveau.freedesktop.org/wiki/CodeNames#NVC0](http://nouveau.freedesktop.org/wiki/CodeNames#NVC0)
Mine is code NVCE

[http://nouveau.freedesktop.org/wiki/InstallDRM#Firmware](http://nouveau.freedesktop.org/wiki/InstallDRM#Firmware)

My card code is not explicitly listed as needing proprietary firmware, but then again it's also not explicitly listed as having free firmware. It's in the NVC0 family though, so the claim is that the free firmware will work.

As far as I can tell there aren't any muxed systems with a gtx 675m with which people can appropriately test nouveau. It seems like everyone has the same problem as me with X. But then again perhaps I haven't searched deep enough.

Thus the first thing to do is see if I can get this xserver working before the release of xorg 1.13 which now looks like it will have the gpu offloading support: [http://www.phoronix.com/scan.php?page=news_item&px=MTEzMzE](http://www.phoronix.com/scan.php?page=news_item&px=MTEzMzE)

---

### Post by Lekensteyn on 2012-07-05
> **Mahler122 said:**
> However I'm now having typical build problems which result from not knowing exactly what you're doing..

Maybe I'm being a bit too optimistic, but I'm trying to build X alongside the X which ubuntu set up. I figured I could isolate the build environment, build, then setup the correct LD_LIBRARY_PATH and PATH variables so that when I call X, it calls the new version. I could then shut down my current X, change environment and start the new X. Do you think it's possible to actually have this work in the end?

Right now it's crashing and giving an error related to XKB.
To fix the xkb issue, install "libxkbfile-dev" (may be necessary before building X).
You also need to rebuild the evdev module (and any other X module you use, e.g. the "xf86-input-wacom" module for Wacom tables) otherwise the devices will be unusuable, unabling you to use X because of the ABI mismatch.
My notes for PRIME are here: [http://lekensteyn.nl/files/prime-instructions.txt](http://lekensteyn.nl/files/prime-instructions.txt)

---

### Post by idoitprone on 2012-07-05
> **Mahler122 said:**
> ```

matthew@sibelius:~$ cat /proc/acpi/bbswitch 
0000:01:00.0 OFF
```

This is unclear: 
[http://nouveau.freedesktop.org/wiki/CodeNames#NVC0](http://nouveau.freedesktop.org/wiki/CodeNames#NVC0)
Mine is code NVCE

[http://nouveau.freedesktop.org/wiki/InstallDRM#Firmware](http://nouveau.freedesktop.org/wiki/InstallDRM#Firmware)

My card code is not explicitly listed as needing proprietary firmware, but then again it's also not explicitly listed as having free firmware. It's in the NVC0 family though, so the claim is that the free firmware will work.

As far as I can tell there aren't any muxed systems with a gtx 675m with which people can appropriately test nouveau. It seems like everyone has the same problem as me with X. But then again perhaps I haven't searched deep enough.

Thus the first thing to do is see if I can get this xserver working before the release of xorg 1.13 which now looks like it will have the gpu offloading support: [http://www.phoronix.com/scan.php?page=news_item&px=MTEzMzE](http://www.phoronix.com/scan.php?page=news_item&px=MTEzMzE)

Nouveau team barely added remedial support of the kepler series. It is not worth the effort to run nouveau drivers. Graphic cards are very complex these days and those gpu clocks are hard to reverse engineer. 
You will not get acceptable performance because the starting clock is too slow.

---

### Post by seenthelite on 2012-07-05
Check to see that the linux-headers are installed to match the kernel you have.

---

### Post by pogopuschel on 2012-08-16
> **Mahler122 said:**
> 

Another way is being pursued by david airlie in the form of enhancements to the xorg server and freedesktop drivers to allow gpu offloading, which he is calling PRIME. [here]("http://people.freedesktop.org/%7Eairlied/prime-notes.txt"), [here]("http://www.youtube.com/watch?v=XEUKuNTRp78"), and [here]("https://github.com/Bumblebee-Project/Bumblebee/issues/185#issuecomment-6582552")....
....Hopefully soon I will be able to post how to get it working.


Well, I have got Dave Airlies Prime stuff running on Ubuntu. Great work. Prime with nouveau outperforms bumblebee with Nvidiablob drastically - no more loss due to the 2nd Xserver/virtualGL. If anybody is interested, mention it, since that stuff is highly experimental, I prefer not posting a HowTo here.

---

### Post by Trevice on 2012-08-20
Hi,

does anyone knows when this packages will be available in Ubuntu? maybe in 12.10 or we'll have to wait until 13.04?

pogopuschel, an Ubuntu's howto would be great ^^

---

### Post by Lekensteyn on 2012-08-21
> **Trevice said:**
> Hi,

does anyone knows when this packages will be available in Ubuntu? maybe in 12.10 or we'll have to wait until 13.04?

pogopuschel, an Ubuntu's howto would be great ^^

Having support from default repositories in 12.10 is too optimistic, maybe 13.04. Maybe a PPA will become available during 12.10. See also [https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-hybrid-graphics](https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-hybrid-graphics)

Xorg 1.13 should become available soon in which PRIME support is merged. [Mesa master](http://cgit.freedesktop.org/mesa/mesa/commit/?id=6a3ac03f2b80c80655d66b31c0218754f70156de) also contains support for PRIME. Now the intel/nouveau drivers need to have PRIME support merged. My outdated notes which I have linked before largely applies, though you need to check if there is a more recent git branch to try and use the xorg git repo instead of the airlied one.

---

### Post by pogopuschel on 2012-08-21
[COLOR="Red"]**The information in this post is out of date, for an updated an shorter howto see post #20**
[/COLOR]
> **Trevice said:**
> Hi,

does anyone knows when this packages will be available in Ubuntu? maybe in 12.10 or we'll have to wait until 13.04?
Should be available in 12.10. If not, there will be a PPA for prime stuff I guess.
> **Trevice said:**
> 
pogopuschel, an Ubuntu's howto would be great ^^

Ok, for those who cannot wait:
May take 2 hours, depending on your internet connection. Ensure your laptop is properly cooled when it comes to compiling the packages.
First you need a 12.10 install, do **not** add "3rd party software" during install, or you will get the nvidia driver which we do not want. Add "Quantal proposed"  and Xorgedgers PPA to your software sources,  update system. Make sure to get  kernel 3.5.0-6-generic or later. reboot of course when necessary.
Then you have to install all packages needed to build the "prime" stuff:
```
sudo apt-get build-dep xserver-xorg-video-intel libdrm xorg xserver-xorg-video-nouveau mesa
sudo apt-get install mesa-utils asciidoc autoconf automake autotools-dev bison docbook-utils doxygen flex fop git-core gperf intltool jadetex libfontconfig1-dev libfreetype6-dev libglib2.0-dev libncurses5-dev libpng12-dev libssl-dev libtool libudev-dev llvm m4 netpbm psutils systemtap-sdt-dev w3m xmlto zlib1g-dev libice-dev libsm-dev libxi-dev libxmu-dev libxmu-headers libxt-dev libxrender-dev mtdev-tools libxfont-dev x11proto-bigreqs-dev x11proto-xcmisc-dev x11proto-record-dev libxcomposite-dev x11proto-composite-dev x11proto-scrnsaver-dev x11proto-resource-dev xdmx xdmx-tools libmtdev-dev xorg-dev xserver-xorg-input-kbd nouveau-firmware
sudo apt-get purge nvidia*
```Get the sources:
```
mkdir prime
cd prime
git clone git://anongit.freedesktop.org/git/xorg/util/macros
git clone git://anongit.freedesktop.org/mesa/drm
git clone git://anongit.freedesktop.org/mesa/mesa
git clone --depth 1 git://people.freedesktop.org/~airlied/xrandr -b prime
git clone git://people.freedesktop.org/~airlied/xf86-video-intel -b prime-proposed
git clone git://people.freedesktop.org/~airlied/xf86-video-nouveau -b prime
wget http://xorg.freedesktop.org/releases/individual/proto/dri2proto-2.8.tar.bz2
wget http://xorg.freedesktop.org/releases/individual/lib/libXrandr-1.4.0.tar.bz2
wget http://xorg.freedesktop.org/releases/individual/proto/randrproto-1.4.0.tar.bz2
wget http://xorg.freedesktop.org/releases/individual/xserver/xorg-server-1.12.99.903.tar.bz2
wget http://xorg.freedesktop.org/releases/individual/driver/xf86-input-synaptics-1.6.2.tar.bz2
wget http://xorg.freedesktop.org/releases/individual/driver/xf86-input-evdev-2.7.1.tar.bz2
```Unpack:
```
tar jxvf xorg-server-1.12.99.903.tar.bz2
tar jxvf libXrandr-1.4.0.tar.bz2
tar jxvf randrproto-1.4.0.tar.bz2
tar jxvf dri2proto-2.8.tar.bz2
tar jxvf xf86-input-synaptics-1.6.2.tar.bz2
tar jxvf xf86-input-evdev-2.7.1.tar.bz2

```Patching mesa:
```
wget -O prime-support-for-mesa.patch http://cgit.freedesktop.org/~airlied/mesa/patch/?id=444159aae6a0a9b9cc0514f34ba754469b0d2dc2
``````
patch -d mesa -p1 < prime-support-for-mesa.patch
```Patching xserver:
```
sed -i 's/AM_CFLAGS = @XORG_CFLAGS@ @DIX_CFLAGS@/AM_CFLAGS = @XORG_CFLAGS@ @DIX_CFLAGS@ @GL_CFLAGS@/' xorg-server-1.12.99.903/hw/xfree86/dixmods/Makefile.am
```Building all:
```
cd macros
./autogen.sh --prefix=/opt/xorg
sudo make install
cd ..
export ACLOCAL="aclocal -I /opt/xorg/share/aclocal"
export PKG_CONFIG_PATH=/opt/xorg/lib/pkgconfig:/opt/xorg/share/pkgconfig:/opt/mesa/lib/pkgconfig:${PKG_CONFIG_PATH}
export LD_LIBRARY_PATH=/opt/xorg/lib:${LD_LIBRARY_PATH}
export LD_RUN_PATH=/opt/xorg/lib:${LD_RUN_PATH}
# do not close/change terminal until everything is built ! (Or repeat  export)                   
cd randrproto-1.4.0
./configure --prefix=/opt/xorg
sudo make install
cd..
cd libXrandr-1.4.0
./configure --prefix=/opt/xorg
make
sudo make install
cd ..
cd xrandr
./autogen.sh --prefix=/opt/xorg
make
sudo make install
cd ..
cd dri2proto-2.8
./configure --prefix=/opt/xorg
sudo make install
cd ..
cd drm
./autogen.sh \
    --prefix=/opt/xorg \
    --enable-udev \
    --enable-intel \
    --disable-radeon \
    --enable-vmwgfx-experimental-api \
    --enable-nouveau
make
sudo make install
cd ..
cd mesa
./autogen.sh \
    --prefix=/opt/mesa \
    --with-gallium-drivers=nouveau,swrast,svga \
    --with-dri-drivers=i915,i965,nouveau,swrast \
    --enable-gallium-llvm \
    --enable-shared-glapi \
    --enable-gallium-egl \
    --enable-egl \
    --enable-dri \
    --enable-glx \
    --enable-xa \
    --enable-shared-dricore
make
sudo make install
cd ..
cd xorg-server-1.12.99.903
autoreconf -fi
  ./configure --prefix=/opt/xorg \
      --enable-ipv6 \
      --enable-dri \
      --enable-dmx \
      --enable-xvfb \
      --enable-xnest \
      --enable-composite \
      --enable-xcsecurity \
      --enable-xorg \
      --enable-glx-tls \
      --enable-kdrive \
      --enable-kdrive-evdev \
      --enable-kdrive-kbd \
      --enable-kdrive-mouse \
      --enable-install-setuid \
      --enable-config-udev \
      --disable-config-dbus \
      --enable-record \
      --disable-xfbdev \
      --disable-xfake \
      --disable-xephyr \
      --disable-static \
      --localstatedir=/var \
      --with-xkb-path=/usr/share/X11/xkb \
      --with-xkb-output=/var/lib/xkb \
      --with-fontrootdir=/usr/share/fonts
make
sudo make install
cd ..
cd xf86-video-intel
./autogen.sh \
    --prefix=/usr \
    --enable-dri
make
sudo make install
cd ..
cd xf86-video-nouveau
./autogen.sh \
    --prefix=/usr 
make
sudo make install
cd ..
cd xf86-input-evdev-2.7.1
./configure --prefix=/opt/xorg 
make
sudo make install
cd ..
cd xf86-input-synaptics-1.6.2
./configure --prefix=/opt/xorg 
make
sudo make install
```Create Symlinks:
```
echo '/opt/xorg/lib' | sudo tee -a /etc/ld.so.conf.d/startprime.conf
echo 'export LD_LIBRARY_PATH=/opt/xorg/lib:$LD_LIBRARY_PATH' | sudo tee -a /etc/profile.d/loadX.sh
echo 'export PATH=/opt/xorg/bin:$PATH' | sudo tee -a /etc/profile.d/loadX.sh
sudo cp /usr/bin/X /usr/bin/X.backup
sudo ln -s /usr/bin/X /opt/xorg/bin/xorg

```Finished. Log out, change session from "Unity" to "Unity2D" (bug in unity3D with new mesa), log in to check if your new Xserver is running:
```
which X   
```.. should show 
/opt/xorg/bin/X  

Finally testing "prime" :

Load new mesa:
```
export LD_LIBRARY_PATH=/opt/mesa/lib
```Get the needed provider id
```
xrandr --listproviders
```if output shows eg:

Provider 0: id: 111 cap: b nc: 2 no: 4 nap 1 name:Intel
Provider 1: id: 68 cap: 5 nc: 2 no: 3 nap 1 name:nouveau

... the needed provider ids are 111 and 68.

Using those provider ids:
```
xrandr --setprovideroffloadsink 68 111

```Now prime is "up".  Start an application on the Nvidia GPU using the nouveau driver by prefixing "DRI_PRIME=1" , eg:
```
DRI_PRIME=1 glxinfo  
```should show something like:
```
OpenGL vendor string: nouveau
OpenGL renderer string: Gallium 0.4 on NVC1
OpenGL version string: 3.0 Mesa 8.1-devel (git-61b62c0)
OpenGL shading language version string: 1.30
```If you get a black or garbaged window when running eg.
```
DRI_PRIME=1 glxgears  
```or
```
DRI_PRIME=1 openarena  
```and your kernellog gets flooded with pgraph errors, grab the window to enlarge it a bit (glxgears). For openarena you have to start it on the Intel GPU first and set it to fullscreen, then you can start openarena on nouveau successfully.
Powermanagement can be done easily with switcheroo.

I have testet Dave Airlies great work on an Optimus machine with a GT 420M, a Fermi GPU. On Kepler GPUs there might be problems running nouveau.

Special credits to Lekensteyn for his "[_prime scratchbook_]("http://lekensteyn.nl/files/prime-instructions.txt")"  (arch linux) and to
Airlied, Samsagax and mlankhorst for support.

---

### Post by rockorequin on 2012-09-04
@pogopuschel: thanks for the guide, I got it working after a couple of hiccups. There was a typo in the build code (cd.. instead cd ..). I used xserver 1.12.99.905 instead of .903 and the latest nouveau/intel code from git, as the patches are now in there for prime. I didn't need to patch mesa - the patch was already in the git code. I also didn't uninstall nvidia or bumblebee (but bumblebee blacklists the nvidia driver so it doesn't conflict with the nouveau driver).

At first xrandr --listproviders only listed the intel card, but after I rebooted, manually forced the nvidia card on and manually modprobed the nvidia driver, xrandr --listproviders... crashed X completely! But when I logged back in and tried again, it worked and found the nvidia card.

Do you know what causes the PGRAPH errors and if there are any other workarounds? Resizing the window worked for glxspheres - the window had to be larger than a certain size to work - but I wanted to try out prime-nouveau with wine, and since I couldn't resize the screen, I didn't get any output.

---

### Post by pogopuschel on 2012-09-04
@rockorequin
Guess there is no need at all to build mesa, since 9.0 is already available in xorgedgers PPA.  No time to test this now ..;)
Thanks for mentioning typo; could you post the links to updated stuff  for others being interested?

No idea about those pgraph errors; I hoped it was fixed  :-(

---

### Post by rockorequin on 2012-09-04
I used the official master git code (I think) for nouveau and intel (ie I didn't need the prime branches):

nouveau:
[LIST]
[*]git://anongit.freedesktop.org/nouveau/xf86-video-nouveau
[*][http://cgit.freedesktop.org/nouveau/xf86-video-nouveau/](http://cgit.freedesktop.org/nouveau/xf86-video-nouveau/)
[/LIST]

intel:
[LIST]
[*]git://anongit.freedesktop.org/xorg/driver/xf86-video-intel
[*][http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/](http://cgit.freedesktop.org/xorg/driver/xf86-video-intel/)
[/LIST]

and there should be similar support for ATI as well:
[LIST]
[*]git://anongit.freedesktop.org/xorg/driver/xf86-video-ati
[*][http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/)
[/LIST]
So I guess these should also appear soon in xorg-edgers.

Since resizing the glxpsheres window fixes the PGRAPH errors (at least it does if you resize it to above a certain size), perhaps prime isn't sending the window's size to the offloaded GPU? It's pretty fundamental so I also hope it gets fixed soon.

---

### Post by rockorequin on 2012-09-04
I just installed xorg-edgers and the latest nouveau/intel from git. The default xrandr command doesn't support --listproviders, but running 

```
/opt/xorg/xrandr --listproviders
```

(ie the one I built from git://people.freedesktop.org/~airlied/xrandr -b prime) after I enable the nvidia card and sudo modprobe nouveau now gives me:

Providers: number : 2
Provider 0: id: 69 cap: b nc: 2 no: 4 nap 0 name:Intel
Provider 1: id: 379 cap: 2 nc: 2 no: 2 nap 0 name:modesetting

which apart from the 'modesetting' name instead of 'nouveau' is a problem because 

```
/opt/xorg/xrandr --setprovideroffloadsink 379 69
```

gives a BadValue error for 379.

---

### Post by pogopuschel on 2012-09-05
@[rockorequin]("http://ubuntuforums.org/member.php?u=310270")
Just testet daily snapshot 12.10. Everything is now in xorgedgers, besides xrandr. Guess your problems with the modesetting driver instead of nouveau is due to the fact you
have not purged nvidia or have installed bumblebee, which blacklists the nouveau driver by creating bumblebee.conf in /etc/modprobe.d with this content:
```
# installed by bumblebee-nvidia

# do not automatically load nouveau as it may prevent nvidia from loading
**blacklist nouveau**
# do not automatically load nvidia as it's unloaded anyway when bumblebeed
# starts and may fail bumblebeed to disable the card in a race condition.
blacklist nvidia
blacklist nvidia-current
blacklist nvidia-current-updates
```;)

[COLOR=Red]Updated [/COLOR]HowTo:
Install daily built of 12.10, activate Quantal proposed, source code and add xorgedgers PPA.

```
sudo apt-get build-dep xserver-xorg-video-intel xserver-xorg-video-nouveau xorg
sudo apt-get install mesa-utils asciidoc autoconf automake autotools-dev bison docbook-utils doxygen flex fop git-core gperf intltool jadetex libfontconfig1-dev libfreetype6-dev libglib2.0-dev libncurses5-dev libpng12-dev libssl-dev libtool libudev-dev llvm m4 netpbm psutils systemtap-sdt-dev w3m xmlto zlib1g-dev libice-dev libsm-dev libxi-dev libxmu-dev libxmu-headers libxt-dev libxrender-dev mtdev-tools libxfont-dev x11proto-bigreqs-dev x11proto-xcmisc-dev x11proto-record-dev libxcomposite-dev x11proto-composite-dev x11proto-scrnsaver-dev x11proto-resource-dev xdmx xdmx-tools libmtdev-dev xorg-dev xserver-xorg-input-kbd nouveau-firmware

```(maybe you not need the whole bunch, since xserver not needs to get built anymore)
Reboot.
After reboot X was broken (guess due to broken Intel driver from Xorgedgers), so had to reboot in recovery mode, resume normal boot, which works using llvmpipe. Then
reinstall/compile Intel/Nouveau drivers:
```
mkdir prime
cd prime
git clone git://anongit.freedesktop.org/xorg/driver/xf86-video-intel
cd xf86-video-intel
./autogen.sh --prefix=/usr  --enable-dri
make
sudo make install
cd ..
wget http://cgit.freedesktop.org/nouveau/xf86-video-nouveau/snapshot/xf86-video-nouveau-master.tar.gz
tar -zxvf xf86-video-nouveau-master.tar.gz
cd xf86-video-nouveau-master
./autogen.sh  --prefix=/usr
make
sudo make install

```Reboot in normal mode.

```
cd prime
git clone git://anongit.freedesktop.org/git/xorg/util/macros
git clone --depth 1 git://people.freedesktop.org/~airlied/xrandr -b prime
wget http://xorg.freedesktop.org/releases/individual/lib/libXrandr-1.4.0.tar.bz2 
wget http://xorg.freedesktop.org/releases/individual/proto/randrproto-1.4.0.tar.bz2
tar jxvf libXrandr-1.4.0.tar.bz2 
tar jxvf randrproto-1.4.0.tar.bz2
cd macros
./autogen.sh --prefix=/opt/xorg 
sudo make install
export ACLOCAL="aclocal -I /opt/xorg/share/aclocal"
export PKG_CONFIG_PATH=/opt/xorg/lib/pkgconfig:/opt/xorg/share/pkgconfig:${PKG_CONFIG_PATH}
export LD_LIBRARY_PATH=/opt/xorg/lib:${LD_LIBRARY_PATH}
export LD_RUN_PATH=/opt/xorg/lib:${LD_RUN_PATH}
cd ..
cd randrproto-1.4.0
./autogen.sh --prefix=/opt/xorg 
sudo make install
cd ..
cd libXrandr-1.4.0
./autogen.sh --prefix=/opt/xorg
make
sudo make install
cd ..
cd xrandr
./autogen.sh --prefix=/opt/xorg
make
sudo make install
```Thats it, no more building drm, mesa, xserver :-) !
Now get the provider ids:
```
/opt/xorg/bin/xrandr --listproviders
```if output shows eg:

Provider 0: id: 111 cap: b nc: 2 no: 4 nap 1 name:Intel
Provider 1: id: 68 cap: 5 nc: 2 no: 3 nap 1 name:nouveau

... the needed provider ids are 111 and 68.

Using those provider ids:
```
/opt/xorg/bin/xrandr --setprovideroffloadsink 68 111
```Now prime is "up".  Start an application on the Nvidia GPU using the nouveau driver by prefixing "DRI_PRIME=1" , eg:
```
DRI_PRIME=1 glxinfo
```

---

### Post by Perfect Storm on 2012-09-05
Previously guide is marked outdated.

---

### Post by pogopuschel on 2012-09-05
Thanks. Btw, both guides are "previous" (relative to your post); the last one (post #20) is actual of course ;) (9.5.)

---

### Post by Perfect Storm on 2012-09-05
Would it be better if we close this one, and you can start a new one? Then we'll avoid confusion among the users (and me :lolflag:) ?

---

### Post by rockorequin on 2012-09-05
Actually, I found that I don't need to remove bumblebee/nvidia: if I restart X after I modprobe nouveau, I get sane values for xrandr --listproviders, and prime works. It only works if I allow nouveau to do a modeset, which unfortunately means I can't unload it (the nouveau wiki says you can unbind it from the framebuffer and then unload it, but unbinding doesn't work - at least while X is running - presumably because the intel is attached as well).

Using the nouveau driver only seems to work for certain window sizes, or you get a black screen and PGRAPH errors. The default size for glxspheres is too small for it to work, and maximized is too big. I have a 1920x1080 monitor with the unity launcher on the side and the top panel, so maximized is approx 1880x1000.

And DRI_PRIME=3 glxspheres crashed X! In the past that ran the intel driver without frame-limiting it to the vblank interval (60 Hz).

PS. For libXrandr and randrproto, you need ./configure instead of ./autogen. But do we even need to build these? libxrandr is already at 1.4.0-1 in ubuntu.

---

### Post by Lekensteyn on 2012-09-06
> **rockorequin said:**
> PS. For libXrandr and randrproto, you need ./configure instead of ./autogen. But do we even need to build these? libxrandr is already at 1.4.0-1 in ubuntu.

You do not need them, PRIME support for libxrandr is already upstreamed in 1.4.

When trying PRIME, you **must** disable bumblebeed since optirun will not cooperate with PRIME:
```
sudo tee /etc/init/bumblebeed.override <<<manual
sudo stop bumblebeed
```

You can use vgaswitcheroo to safe power, but mind that its still broken after suspend/resume: [https://bugzilla.kernel.org/show_bug.cgi?id=44391](https://bugzilla.kernel.org/show_bug.cgi?id=44391)

---

### Post by pogopuschel on 2012-09-06
> **Lekensteyn said:**
> You do not need them, PRIME support for libxrandr is already upstreamed in 1.4.

Well, indeed you do not need to build libXrandr anymore, that is correct, but still xrandr and randrproto, or you won't have any "listprovideroptions" in xrandr. ;)

@ Lekensteyn
Can you drop a few words about amonakov's "primus" ?
Will it be prime with nvidiablob?

---

### Post by rockorequin on 2012-09-06
@Lekensteyn, thanks for the info. But how exactly does bumblebee not cooperate with prime? Doesn't it just wait in the background and wait for optirun to request a server? Or does it stop vga switcheroo from loading? (I don't have a /sys/kernel/debug/vgaswitcheroo folder, but I thought it only worked with laptops that have a hardware MUX for the video cards.)

I would be quite happy just using bumblebee at the moment, but I was keen on trying out prime because the nvidia driver crashes and burns almost immediately for me on the two games I like to use it for, making the nvidia card pretty much useless for me at present.

---

### Post by Lekensteyn on 2012-09-07
> **pogopuschel said:**
> @ Lekensteyn
Can you drop a few words about amonakov's "primus" ?
Will it be prime with nvidiablob?
See [https://github.com/amonakov/primus](https://github.com/amonakov/primus) for a description of primus. It will indeed be usable with the nvidia blob, although it is not exactly PRIME.

> **rockorequin said:**
> @Lekensteyn, thanks for the info. But how exactly does bumblebee not cooperate with prime? Doesn't it just wait in the background and wait for optirun to request a server? Or does it stop vga switcheroo from loading? (I don't have a /sys/kernel/debug/vgaswitcheroo folder, but I thought it only worked with laptops that have a hardware MUX for the video cards.)
Bumblebee starts an X server on its own and disabled the nvidia card when its not in use. The default method, bbswitch, also requires the video driver to be unloaded. PRIME works with a single X server that communicates with both cards. It requires a driver for the nvidia card (currently nouveau). This does not work with bbswitch (but switcheroo works).

> I would be quite happy just using bumblebee at the moment, but I was keen on trying out prime because the nvidia driver crashes and burns almost immediately for me on the two games I like to use it for, making the nvidia card pretty much useless for me at present.
nvidia blob does not work with PRIME atm, so you might want to stick to Bumblebee for the time being (or try PRIME with nouveau, but you'll very likely hit some bugs now)

---

### Post by rockorequin on 2012-09-07
> **Lekensteyn said:**
> PRIME works with a single X server that communicates with both cards. It requires a driver for the nvidia card (currently nouveau). This does not work with bbswitch (but switcheroo works).

Yes, but I have no /sys/kernel/debug/vgaswitcheroo folder, which the internet tells me I need to use vgaswitcheroo. But my kernel (3.6-rc4) is built with CONFIG_VGA_SWITCHEROO=y.

> 
nvidia blob does not work with PRIME atm, so you might want to stick to Bumblebee for the time being (or try PRIME with nouveau, but you'll very likely hit some bugs now)

Sadly, bumblebee is only useful for turning off the nvidia card at the moment for me, because the nvidia-current kernel module crashes so quickly and comprehensively when I run wine apps with it.

And yes, speaking of buggy, nouveau prime doesn't work for wine apps because of the PGRAPH issue. I did at one point get nouveau working with bumblebee but it runs too slowly.

---

### Post by pogopuschel on 2012-09-08
> **rockorequin said:**
> Yes, but I have no /sys/kernel/debug/vgaswitcheroo folder, which the internet tells me I need to use vgaswitcheroo. But my kernel (3.6-rc4) is built with CONFIG_VGA_SWITCHEROO=y.

Because you have the Nvidiablob installed. This Folder only exists when running the free drivers.

---

### Post by Mahler122 on 2012-09-10
Hi All,

Thanks very much to pogopuschel, for the most recent guide on reply 20! This seems to have worked for me! at least the compiling xorg part.

It seems I can now set the provider and use DRI_PRIME to get the appropriate output from glxinfo. here is an excerpt:

```
matthew@sibelius:~/Sources/prime/xprime/bin$ ./xrandr --listproviders
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
LVDS1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
Providers: number : 2 
Provider 0: id: 137 cap: b nc: 3 no: 4 nap 0 name:Intel
Provider 1: id: 98 cap: 5 nc: 2 no: 1 nap 0 name:nouveau
matthew@sibelius:~/Sources/prime/xprime/bin$ ./xrandr --setprovideroffloadsink 98 137 
matthew@sibelius:~/Sources/prime/xprime/bin$ glxinfo | grep render
direct rendering: Yes 
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Mobile 
    GL_NV_conditional_render, GL_AMD_draw_buffers_blend, 
matthew@sibelius:~/Sources/prime/xprime/bin$ DRI_PRIME=1 glxinfo | grep render
direct rendering: Yes 
OpenGL renderer string: Gallium 0.4 on NVCE
    GL_NV_conditional_render, GL_AMD_conservative_depth,
```

Very nice! It should however be noted that it takes a very long time for the nvidia glxinfo command to return.

However I now try to run glxgears for both intel and nouveau.
With intel, it works fine and produces the following output when I kill glxgears:

```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"^M
      after 318 requests (318 known processed) with 0 events remaining.^M
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
```

Now when I try with my nvidia chip, I get a weird garbled glxgears window for a little bit, when then crashes with a segfault. the log output is:

```
nouveau: kernel rejected pushbuf: Invalid argument
nouveau: ch2: krec 0 pushes 1 bufs 0 relocs 0
```

The backtrace which appeared in dmesg is:

```
[  436.024137] [drm] nouveau 0000:01:00.0: PFIFO: unknown status 0x00000100
[  436.024141] [drm] nouveau 0000:01:00.0: PFIFO: unknown status 0x40000000
[  438.023137] [drm] nouveau 0000:01:00.0: PFIFO - playlist update failed
[  499.093183] [drm] nouveau 0000:01:00.0: Failed to idle channel 2.
[  502.091648] [drm] nouveau 0000:01:00.0: Failed to idle channel 2.
[  505.090110] [drm] nouveau 0000:01:00.0: Failed to idle channel 2.
[  508.088574] [drm] nouveau 0000:01:00.0: Failed to idle channel 2.
[  510.087648] [drm] nouveau 0000:01:00.0: 0x2634 != chid: 0x00100002
[  510.087733] [drm] nouveau 0000:01:00.0: PFIFO: unknown status 0x00000100
[  512.086736] [drm] nouveau 0000:01:00.0: PFIFO - playlist update failed
[  560.930086] [drm] nouveau 0000:01:00.0: PFIFO: unknown status 0x00000100
[  562.929059] [drm] nouveau 0000:01:00.0: PFIFO - playlist update failed
[  568.993975] [drm] nouveau 0000:01:00.0: push 0 buffer not in list
[  568.994113] show_signal_msg: 30 callbacks suppressed
[  568.994118] glxgears[2754]: segfault at 1000000000 ip 00007fba34beb460 sp 00007fffe51cf620 error 4 in libdrm_nouveau.so.2.0.0[7fba34be9000+5000]
[  572.811376] [drm] nouveau 0000:01:00.0: Failed to idle channel 2.
[  574.810531] [drm] nouveau 0000:01:00.0: 0x2634 != chid: 0x00100002
[  574.810624] [drm] nouveau 0000:01:00.0: PFIFO: unknown status 0x00000100
[  576.809623] [drm] nouveau 0000:01:00.0: PFIFO - playlist update failed

```

So, Progress! However I'm not sure exactly who is to blame here. my gut tells me it's nouveau and that this is the result of my card not being supported. However I don't know if this kind of error is the result of me doing something slightly wrong.

Please let me know your thoughts!

---

### Post by Mahler122 on 2012-09-10
Strange, I'm getting varied results.

I tried it again a second ago, and no crash, but my computer basically slowed to a crawl while displaying the garbled glxgears screen and ran for a while before I killed it.

Here was the output.

```
matthew@sibelius:~$ DRI_PRIME=1 glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
206 frames in 6.6 seconds = 31.277 FPS
2 frames in 6.0 seconds =  0.333 FPS
2 frames in 6.0 seconds =  0.333 FPS
2 frames in 6.0 seconds =  0.333 FPS
2 frames in 6.0 seconds =  0.333 FPS
^C

```

So.. I guess it doesn't crash all the time? I'll try to get a screenshot of the glxgears screen.

EDIT:

Okay I tried it again, but instead of a garbled glxgears screen, I got a glxgears window with just black inside. I tried to get the screenshot, but the result was simply blackness.

In anycase, it seems to 'work' without crashing, but without actually drawing anything and at an absolutely unworkable framerate just look at the statistics from the glxgears run above.

Also it seems to slow all other graphics production down. I had to switch to a tty terminal to kill the glxgears because xorg wasn't refreshing my cursor once the forwarding began.

---

### Post by rockorequin on 2012-09-10
> **Mahler122 said:**
> 
Okay I tried it again, but instead of a garbled glxgears screen, I got a glxgears window with just black inside. I tried to get the screenshot, but the result was simply blackness.


Does resizing the window help? I always get a black screen when I first run something on the nouveau card (and nouveau floods the syslog with PGRAPH errors), but resizing it smaller or bigger even slightly fixes the problem.

My tests with glxspheres, which comes with virtualgl in the bumblebee package, showed that the nouveau card is a bit faster than the intel card, but not hugely. I get 120-130 fps with intel if I turn off vsync by setting the env var vblank_mode=0 and maybe 150 fps with nouveau.

---

### Post by pogopuschel on 2012-09-11
[@Mahler122]("http://ubuntuforums.org/member.php?u=649404")

If resizing windows does not help...
...maybe your problems are due to you are running a NVCE, a Kepler GPU, which are not pretty good supported by nouveau [atm]("http://www.phoronix.com/scan.php?page=news_item&px=MTE4MTI").
Suggest to jump in irc channel #nouveau and ask the devs directly, showing your kern.log, maybe you can help them fixing the issue.

---

### Post by Mahler122 on 2012-09-11
> **pogopuschel said:**
> If resizing windows does not help...
...maybe your problems are due to you are running a NVCE, a Kepler GPU, which are not pretty good supported by nouveau [atm]("http://www.phoronix.com/scan.php?page=news_item&px=MTE4MTI").
Suggest to jump in irc channel #nouveau and ask the devs directly, showing your kern.log, maybe you can help them fixing the issue.

The resizing did not help. I'm going to try asking the devs.

---

### Post by wegah on 2012-09-13
An stupid question.
How to turn the "DRI_PRIME=1" default in quantal environment?
More specific in unity/compiz?

---

