---
title: "Getting ATI Drivers working completely"
date: 2006-06-03
forum: General Help
---

### Post by Patrick-Ruff on 2006-06-03
hey all, I couldn't find the thread for this, and I think it may be different for dapper, what are the steps for getting ATI cards working perfectly on dapper? like, 100% 3d accelleration etc.

heres my card:
Ati's Mobility Radeon X300 PCI-e 64mb dedicated.

---

### Post by shuttleworthwannabe on 2006-06-03
These wiki instructions have always worked for me: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

---

### Post by Patrick-Ruff on 2006-06-04
it really doesn't look like its actually being 'accellerated' how do I test whether or not this is the maxa I can get? its getting horrible FPS in a screensaver for christ sake... and I did the verify thing on that wiki, I don't think thats actual proof of real 'accelleration' what can I do here?

---

### Post by shuttleworthwannabe on 2006-06-04
to get the FPS printout, try

$glxgears -printfps

(I think).

Which one did you install (Binary driver or Prop ATU drivers). If one does not get you the desired FPS try the other. I am no expert, bu there may be other xorg.conf options that I am not familiar with, but someone can advise you better.

---

### Post by Patrick-Ruff on 2006-06-04
I'm pretty sure it was the binary, also, I'm getting 1700 range.

---

### Post by Patrick-Ruff on 2006-06-04
some other screensavers, I get less then 10 FPS tho, and I don't think thats entirely correct at all, I mean, this video card could handle Unreal Tournament 2004. perfectly.

---

### Post by oobe on 2006-06-04
I am using the ATI Mobility 9200 in my Laptop. In windows once the proper ATI drivers have been installed, I can use a keyboard combination to enable S-Video output so I can watch video on my television. How do I achieve this in (K)Ubuntu?

---

### Post by Patrick-Ruff on 2006-06-04
umm, they haven't even answered my issues yet dude. start your own thread.

---

### Post by firetux on 2006-06-04
What is the result of ```
fglrxinfo
```?

---

### Post by pertti on 2006-06-04
[QUOTE=Patrick-Ruff]it really doesn't look like its actually being 'accellerated' how do I test whether or not this is the maxa I can get? its getting horrible FPS in a screensaver for christ sake... and I did the verify thing on that wiki, I don't think thats actual proof of real 'accelleration' what can I do here?[/QUOTE]

Same problem here. I have an ATI 9600 Pro with the driver from the ATI website (8.24.8). glxgears runs fine, over 2600 fps, but GL screen savers run pretty slowly. Here's my flgrxinfo:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5755 (8.24.8)
```

I'm going to try with the driver from the Ubuntu repository, which has the same version as the one I'm using now. If that doesn't work either, I'll try again with the new drivers from ATI (8.25.18).

---

### Post by pertti on 2006-06-04
Ok, now I have everything working, using the drivers from the repository (which are 8.25.18, not 8.24. as I thought).

First I switched to vesa and uninstalled everything related to the fglrx driver: linux-restricted-modules-<kernel>, fglrx-kernel-<kernel> and xorg-driver-fglrx. I had a problem with the later, which I had to solve using some [black magic]("http://www.ubuntuforums.org/showthread.php?t=186389") ;).

The I installed again the restricted modules and xorg-driver-fglrx. Got the infamous "mesa issue", which I solved by removing fglrx from the list in /etc/default/linux-restricted-modules-common (oops, I forgot to do that).

Rebooted, and everything went fine. Hope this helps.

---

### Post by Patrick-Ruff on 2006-06-04
whoa, thats a tad bit confusing, I'm a noob so...can anyone explain those steps to me?

also from fglrx info I get

display:  :0.0 screen: 0
OpenGL Vendor string:  Mesa Project:  [www.mesa3d.org](www.mesa3d.org)
OpenGL Renderer String: Mesa GLX Indirect
OpenGL Version string 1.2 (1.5 Mesa 6.4.1)

---

### Post by Patrick-Ruff on 2006-06-04
this is really weird, it was showing ATI yesterday....

---

### Post by Patrick-Ruff on 2006-06-04
ok I fixed that issue, but I'm still getting horrible FPS in the 'Hyperspace' screensaver and others. that I shouldn't be gettng low FPS in.... this video card should be able to EASEALLY handle that screensaver, especially in a small square...

fglrxinfo prints:
display: :0.0 screen: 0
OpenGL Vendor string: ATI Technologies Inc.
OpenGL Renderer String: Mobility Radeon X300 Generic
OpenGL Version string:  2.0.5814 ( 8.25.18 )

---

### Post by Patrick-Ruff on 2006-06-04
**bump**

---

### Post by Patrick-Ruff on 2006-06-04
ok guys, its been atleast 12 hours since the last responce..... I still lack in 'actual' video accelleration, what other steps can I do to make this possible, I should be able to get equal performance that I did in windows... I don't see why it isant possible.

---

### Post by eqisow on 2006-06-04
Well you may not get equal performance because ATI has horrible Linux drivers. However, your screensavers should certainly run. Run the following command for me:

```
cat /etc/X11/xorg.conf | grep fglrx
```

If it outputs something like, **Driver "fglrx"**, your drivers *should* be working and we'll have to try something else. If it doesn't output anything, your drivers aren't installed correctly, and we can fix that as well.

Edit: Just out of curiousity, do other 3D apps (not screensavers) work fine? Something like Planet Penguin Racer, foobillards, Solar Wolf, or UT 2004 (since you said you had it).

---

### Post by Patrick-Ruff on 2006-06-04
I haven't installed UT2k4  yet, I suppose that'd be a good test. hold on I'll install it now.

---

### Post by eqisow on 2006-06-04
What about the output of the command I asked you to run?

---

### Post by Patrick-Ruff on 2006-06-04
how does one go about installing UT2k4 on Linux? lol

---

### Post by Patrick-Ruff on 2006-06-04
the command said ' Driver "fglrx"

---

### Post by eqisow on 2006-06-04
I may be mistaken, but I believe there is a file called linux-installer.sh on the install CD. Just run this with **sh /media/cdrom/linux-installer.sh** .

Edit: NM, I see now. Thanks. :)

---

### Post by Patrick-Ruff on 2006-06-04
ok so...what do I do about my graphics accelleration?

---

### Post by eqisow on 2006-06-04
Did you restart you computer when you did the driver install? If not, do so and try the screensavers or something again. If you have already rebooted, or if you reboot and 3D still doesn't work, try the following command and copy/paste the output hhere.

```
dmesg | grep fglrx
```

---

### Post by Patrick-Ruff on 2006-06-04
yes I did.

---

### Post by eqisow on 2006-06-04
```
dmesg | grep fglrx
```

Do that and paste the output here.

---

### Post by Patrick-Ruff on 2006-06-04
sorry bout that I had to turn ICS on the laptop.  I'm on the Linux machine right now. 
```

eclypse@Eclypse:~$ dmesg | grep fglrx
[4294698.981000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294698.982000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294698.982000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294700.530000] [fglrx] total      GART = 67108864
[4294700.530000] [fglrx] free       GART = 51118080
[4294700.530000] [fglrx] max single GART = 51118080
[4294700.531000] [fglrx] total      LFB  = 60846080
[4294700.531000] [fglrx] free       LFB  = 52654080
[4294700.531000] [fglrx] max single LFB  = 52654080
[4294700.531000] [fglrx] total      Inv  = 0
[4294700.531000] [fglrx] free       Inv  = 0
[4294700.531000] [fglrx] max single Inv  = 0
[4294700.531000] [fglrx] total      TIM  = 0


```

---

### Post by Patrick-Ruff on 2006-06-04
sorry bout that I had to turn ICS on the laptop.  I'm on the Linux machine right now. 
```

eclypse@Eclypse:~$ dmesg | grep fglrx
[4294698.981000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294698.982000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[4294698.982000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294700.530000] [fglrx] total      GART = 67108864
[4294700.530000] [fglrx] free       GART = 51118080
[4294700.530000] [fglrx] max single GART = 51118080
[4294700.531000] [fglrx] total      LFB  = 60846080
[4294700.531000] [fglrx] free       LFB  = 52654080
[4294700.531000] [fglrx] max single LFB  = 52654080
[4294700.531000] [fglrx] total      Inv  = 0
[4294700.531000] [fglrx] free       Inv  = 0
[4294700.531000] [fglrx] max single Inv  = 0
[4294700.531000] [fglrx] total      TIM  = 0


```

---

### Post by eqisow on 2006-06-04
No problem. It looks like the module is loading normally, so I'm really not sure what the issue is. I can only think of one more thing to check off the top of my head.

Do the following command, and post the output.

```
cat /etc/X11/xorg.conf | grep Load
```

---

### Post by Patrick-Ruff on 2006-06-04
eclypse@Eclypse:~$ cat /etc/X11/xorg.conf | grep Load
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"

---

### Post by eqisow on 2006-06-04
OK, try the following.

```
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
```

If you still have no luck, run the following and then attach the generated text file (it will be in your home directory) to your post.

```
cat /var/log/Xorg.0.log > Xorg.log.txt
```

---

### Post by Patrick-Ruff on 2006-06-04
file:///home/eclypse/Xorg.log.txt

---

### Post by eqisow on 2006-06-04
Err, try again. Click "Manage Attachments" under the "Additional Options" header when making your post. Click browse and select the file from there. :)

---

### Post by Patrick-Ruff on 2006-06-04
sorry bout that, its attatched now.

---

### Post by JGKC9AYC on 2006-06-05
[QUOTE=shuttleworthwannabe]These wiki instructions have always worked for me: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)[/QUOTE]

Here's what I got after typing in "fglrxinfo":

[I]display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
[/I]

I tried typing in "cat /etc/x11/xorg.conf | grep fglrx" & got:
[i]
cat: /etc/x11/xorg.conf: No such file or directory[/i]

Ideas?  Suggestions?

---

### Post by Patrick-Ruff on 2006-06-05
and my problem hasent even been solved yet...

edit: removed personal insult

---

### Post by exclipy on 2006-06-05
You missed a captial X there JGKC9AYC:
"cat /etc/X11/xorg.conf | grep fglrx"

---

### Post by Patrick-Ruff on 2006-06-05
.....

---

### Post by ericesque on 2006-06-05
Patrick,

I would have to ask that you be more polite and respectful of the other forum members.  I am no admin, but I find your conduct and language offensive.  Consider this a kind reminder of community [conduct]("http://www.ubuntu.com/community/conduct") and an opportunity to use the edit button on some of your previous comments.

The ATI driver issue is well known and well documented in wikis and other threads.  Please be patient at other members try to assist you.  I find people more willing to help when I am patient and courteous with them.

---

### Post by Patrick-Ruff on 2006-06-05
been there, tried that 3 days ago. didn't work well for me after waiting for 40 hours...

---

### Post by Patrick-Ruff on 2006-06-05
good night everyone. hopefully there may be some actually useful replys tomorrow.

---

### Post by Stratus on 2006-06-05
[QUOTE=Patrick-Ruff]good night everyone. hopefully there may be some actually useful replys tomorrow.[/QUOTE]

Hi Patrick, from your Xorg.0.log output, acceleration appears to be working!
Can you post the output from the following commands?

```
export LIBGL_DEBUG=verbose
``` then
```
fglrxinfo
```

---

### Post by Patrick-Ruff on 2006-06-05
here it is:
```

eclypse@Eclypse:~$ export LIBGL_DEBUG=verbose
eclypse@Eclypse:~$ fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.25.18 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.25.18 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
Can't open configuration file /etc/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/eclypse/.drirc: No such file or directory.
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

---

### Post by department27 on 2006-06-05
Hi Have a similar problem. Originally got the mesa message in fglrxinfo, but now I get a load of errors.

Here some info:

lsmod |grep fglrx
fglrx                 391756  8
agpgart                36784  2 fglrx,intel_agp


pete@tindrum:~$ dmesg | grep fglrx
[4294702.993000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294702.996000] [fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[4294702.997000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294703.750000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294703.750000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294703.750000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294703.751000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294703.761000] [fglrx] total      GART = 134217728
[4294703.761000] [fglrx] free       GART = 118222848
[4294703.761000] [fglrx] max single GART = 118222848
[4294703.762000] [fglrx] total      LFB  = 26210304
[4294703.762000] [fglrx] free       LFB  = 15724544
[4294703.762000] [fglrx] max single LFB  = 15724544
[4294703.762000] [fglrx] total      Inv  = 0
[4294703.762000] [fglrx] free       Inv  = 0
[4294703.762000] [fglrx] max single Inv  = 0
[4294703.762000] [fglrx] total      TIM  = 0
pete@tindrum:~$

pete@tindrum:~$ fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS.....

Full error attached.

I did follow all the info, i.e. remove driver and restricted, and then reinstalled them.

I assume the wrong driver is being loaded, not sure at what point and where I can force it. Any idea's woould be great.

P.S. Card is an mobility 9000, on a dell d600.

---

### Post by sweeper on 2006-06-05
[QUOTE=Stratus]Hi Patrick, from your Xorg.0.log output, acceleration appears to be working!
Can you post the output from the following commands?

```
export LIBGL_DEBUG=verbose
``` then
```
fglrxinfo
```[/QUOTE]

Can you tell me if my acceleration is working too please?
Sorry to jump in Patrick but it didn't seem worth starting another thread.

edit
I think I found it > fglrx(0): Acceleration enabled

---

### Post by Patrick-Ruff on 2006-06-05
anyone else have any information regarding this problem?

---

### Post by Patrick-Ruff on 2006-06-05
also, if you get nice FPS in games, such as UT2k4, equal to windows anyways, your fine. look at some screensavers and see if you get perfect fps or fps equal to that of what you would get in windows.

---

### Post by Kilz on 2006-06-05
[QUOTE=Patrick-Ruff]also, if you get nice FPS in games, such as UT2k4, equal to windows anyways, your fine. look at some screensavers and see if you get perfect fps or fps equal to that of what you would get in windows.[/QUOTE]

I have a ati x200, the 8.25.18 drivers are awful. Odds are you dont have acceleration for some applications with it. Its also known to cause crashes on shutdown.
I tried everything, uninstalling, overwriting, etc,etc.The only way I was able to get rid of the 8.25.18 drivers was a complete Dapper reinstall then[ use the wiki and reinstall the 8.24.8]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2") drivers. Once I had them Installed I opened synaptic, searched for fglrx, highlighted every installed file,  clicked package , then lock version.

In case you or anyone else is having problems with the 8.25.18 drivers and want to use the 8.24.8 drivers here is an install source. Sadly you may have to go to drastic mesures to get rid of the 8.25.18 ones you have installed.

For x86
        * [RADEON 8500 Series and higher]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run")
        * [Motherboards with ATI Graphics]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run")
      [  * Notebooks with ATI Graphics]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run")

---

### Post by sweeper on 2006-06-05
[QUOTE=Kilz]I have a ati x200, the 8.25.18 drivers are awful. Odds are you dont have acceleration for some applications with it. Its also known to cause crashes on shutdown.
I tried everything, uninstalling, overwriting, etc,etc.The only way I was able to get rid of the 8.25.18 drivers was a complete Dapper reinstall then[ use the wiki and reinstall the 8.24.8]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI#head-26e8b0d4be861a6b7c545dc21c45232f909d8ca2") drivers. Once I had them Installed I opened synaptic, searched for fglrx, highlighted every installed file,  clicked package , then lock version.

In case you or anyone else is having problems with the 8.25.18 drivers and want to use the 8.24.8 drivers here is an install source. Sadly you may have to go to drastic mesures to get rid of the 8.25.18 ones you have installed.

For x86
        * [RADEON 8500 Series and higher]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run")
        * [Motherboards with ATI Graphics]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run")
      [  * Notebooks with ATI Graphics]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.24.8-x86.run")[/QUOTE]

I had no problems with the latest drivers but I installed the 8.24.8 just in case, it was a bit of a hassle. How can I lock it please?

---

### Post by WoodyJI on 2006-06-05
I have a similar situation to yours, I think.  I installed my ati drivers properly, but my screensaver is very choppy...obviously no full graphics acceleration.  Then I ran the program "gfl_glxgears" (located in /usr/bin).  It's a rotating cube w/ gears on it that the ati installer provided to test your graphics card.  Mine ran very smoothly, yet my screensavers are still slow.  I don't think it's an ati problem...it might be a ubuntu problem.  If only we could figure out how to make sure that all programs that need to access graphics acceleration would!

---

### Post by Stratus on 2006-06-05
[QUOTE=Patrick-Ruff]whoa, thats a tad bit confusing, I'm a noob so...can anyone explain those steps to me?

also from fglrx info I get

display:  :0.0 screen: 0
OpenGL Vendor string:  Mesa Project:  [www.mesa3d.org](www.mesa3d.org)
OpenGL Renderer String: Mesa GLX Indirect
OpenGL Version string 1.2 (1.5 Mesa 6.4.1)[/QUOTE]

[QUOTE=Patrick-Ruff]here it is:
```

eclypse@Eclypse:~$ export LIBGL_DEBUG=verbose
eclypse@Eclypse:~$ fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.25.18 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.25.18 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
Can't open configuration file /etc/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/eclypse/.drirc: No such file or directory.
display: :0.0  screen: 0
[COLOR="Red"]OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5814 (8.25.18)[/COLOR]

```[/QUOTE]

Hi Patrick 

The first quote is from you earlier on in this thread, the second from just up the page.
It appears that you now have acceleration, I've highlighted the important part in red for you.

Cheers

---

### Post by Stratus on 2006-06-05
[QUOTE=department27]Hi Have a similar problem. Originally got the mesa message in fglrxinfo, but now I get a load of errors.

Here some info:

lsmod |grep fglrx
fglrx                 391756  8
agpgart                36784  2 fglrx,intel_agp


pete@tindrum:~$ dmesg | grep fglrx
[4294702.993000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[4294702.996000] [fglrx] Maximum main memory to use for locked dma buffers: 430 MBytes.
[4294702.997000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[4294703.750000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294703.750000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294703.750000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[4294703.751000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294703.761000] [fglrx] total      GART = 134217728
[4294703.761000] [fglrx] free       GART = 118222848
[4294703.761000] [fglrx] max single GART = 118222848
[4294703.762000] [fglrx] total      LFB  = 26210304
[4294703.762000] [fglrx] free       LFB  = 15724544
[4294703.762000] [fglrx] max single LFB  = 15724544
[4294703.762000] [fglrx] total      Inv  = 0
[4294703.762000] [fglrx] free       Inv  = 0
[4294703.762000] [fglrx] max single Inv  = 0
[4294703.762000] [fglrx] total      TIM  = 0
pete@tindrum:~$

pete@tindrum:~$ fglrxinfo
libGL: XF86DRIGetClientDriverName: 8.25.18 atiogl_a (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/atiogl_a_dri.so
fglrx: libGL version does not match - OpenGL module is using glapi fallback
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS.....

Full error attached.

I did follow all the info, i.e. remove driver and restricted, and then reinstalled them.

I assume the wrong driver is being loaded, not sure at what point and where I can force it. Any idea's woould be great.

P.S. Card is an mobility 9000, on a dell d600.[/QUOTE]

Please have a look at this thread... [http://www.ubuntuforums.org/showthread.php?t=184111&page=2&highlight=ati+fglrx](http://www.ubuntuforums.org/showthread.php?t=184111&page=2&highlight=ati+fglrx)

---

### Post by RavenOfOdin on 2006-06-05
8.25.18 with the old libGL.so works for me.

No functionality is lost either, since I can operate apps that require 8.20 or above correctly.

---

### Post by Patrick-Ruff on 2006-06-05
of course it 'appears' I have accelleration...but I don't call it accelleration when it can hardly handle a 3d screen saver. seriously....

---

### Post by Kilz on 2006-06-05
[QUOTE=Patrick-Ruff]of course it 'appears' I have accelleration...but I don't call it accelleration when it can hardly handle a 3d screen saver. seriously....[/QUOTE]

What is your screen resolution and color depth? The screen saver is probably relying on hardware acceleration, as is glxgears. Games and bigger programs will use software acceleration.

[QUOTE=Patrick-Ruff] Post #5  I'm pretty sure it was the binary, also, I'm getting 1700 range.[/QUOTE]

From your own file from post 34
(II) fglrx(0): VESA VBE Total Mem: 65536 kB

You have ATI x300 on board graphics, with 64 megs of shared video ram.

1700 fps sounds about right. ATI with x300 and 64 megs of shared video ram is going to give you about 1700 fps with glxgears. This isn't a Ubuntu problem. Its what ATI is capable of with the Linux drivers ATI supplies. If you want to complain about poor performance I suggest an email to ATI.

---

### Post by Patrick-Ruff on 2006-06-05
that memory is not shared. its on the actual video card... dedicated memory... if I get horrible FPS in Unreal Tournament 2004 when I get it installed, your wrong.

---

### Post by Patrick-Ruff on 2006-06-05
ok, well UT2k4 seems to be working just as well.. *yawns* thanks guys, my allergy medicine is making me very drowsy so, thanks for all your help, I still have one more remark tho, it seems like the desktop enviornment isant as 'speedy' as I would hope, how could I make such a thing possible, the icons when I open up a menu, like say administration preferrences, the icons take about a quarter second to load, and generally it should be much faster then that...anyone know?

---

### Post by Patrick-Ruff on 2006-06-06
guys, I still have a question, regarding a performance issue with gnome, it always takes like a quarter second to load the icons on the menu's and all that, now can I fix this? trust me my laptop is NOT slow lol.

---

### Post by Patrick-Ruff on 2006-06-06
also, seeing that UT2k4 uses 'software' accelleration and seems to perform well...is it possible to make the entire GNOME/Linux enviornment use software so perhaps it would perform like windows?

---

### Post by firetux on 2006-06-06
Patrick, instead of writing four posts in a row you can also use the "edit" button, it makes these forums so much easier to read.

---

### Post by elemental666 on 2006-06-06
mkay, so wow, its been 2 hours since you last posted Patrick, please take a few deep breathes I"m about to lay some reading on you:

1st and formost, you need to pay attention to this link and its author.  Respect it!

[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)

For your speed tweaks start here, then ask a specific question.

Gnome performance thread: [http://ubuntuforums.org/showthread.php?t=189309](http://ubuntuforums.org/showthread.php?t=189309)
Ubuntu performance thread: [http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)

---

### Post by department27 on 2006-06-06
Thanks for answering. Actually managed to get it fixed. Looks like the problem is the libGL.so.1.2. Someone had posted a different version on this forum, and I replaced mine and it now works. Have not tested the speed or antyhing yet.

---

### Post by Patrick-Ruff on 2006-06-06
first off, If I don't post like that people just forget about the thread then after a while its like 5 pages back and nobody will ever reply to it.

---

### Post by Patrick-Ruff on 2006-06-06
it definately seems to be a gnome issue, KDE runs very well. but ever since dapper, gnome looks much better then KDE :D

---

### Post by Patrick-Ruff on 2006-06-07
isant it great that GNOME has actually gotten to the point where it looks better then KDE? :)

---

### Post by iMerlin on 2006-06-07
Just a little follow up.

I had the same problem. I only got "mesa" from "fglrxinfo" but it appeared that the "fglrx_dri.so" was causing my problems.

The firegl debug pointed me to this:

```
libGL error: dlopen /usr/X11R6/lib/modules/dri//fglrx_dri.so failed (/usr/X11R6/lib/modules/dri//fglrx_dri.so: cannot open shared object file: No such file or directory)
```

I symlinked the 'dri' directory and now fglrxinfo shows 'ATI' instead of Mesa.

3D acceleration now works perfectly...

---

### Post by Patrick-Ruff on 2006-06-08
I think the main thing I was noticing is that Gnome wasent as speedy as windows was graphically. any way this can be improoved?

---

### Post by Cataphract on 2006-06-12
Hello,

I'm having problems with my ATI Radeon X300SE as well. I just re-installed Ubuntu because of what I suspect are graphics acceleration problems and, after installing the 20 updates waiting for me, decided to install two games off of the Synaptic Package Manager to test: Planet Penguin Racer and Trigger. Planet Penguin Racer seems fine, but Trigger exits out to the desktop after about 8-10 seconds and then the mouse cursor appears to be frozen. The only way to recover I have found is Ctrl + Alt + Backspace. Screensaver Hufo's Tunnel and Hyperspace I have noticed also run extremely slowly.

None of the previous posts on this thead have helped me (though, at the same time, I do not want to go off and do something someone mentioned on a hunch that it would work...I've had bad experiences with such "quick fixes" messing up my installation). But I'm sure it's not going to be hard to figure out. :-o

I have my computer set-up for dual boot, so just before trying this out, I checked the version of my driver in Windows XP: 6.14.10.6444

I went to this link: [https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI") and followed the instructions *exactly* (copying and pasting the commands) for the Ubuntu 6.06 (Dapper Drake) section. Here is the command line output of the first 5 commands under that section:

> 
karl@karlsdell:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Fetched 4B in 0s (6B/s)
Reading package lists... Done
karl@karlsdell:~$ sudo apt-get install linux-restricted-modules-$(uname -r)
Reading package lists... Done
Building dependency tree... Done
linux-restricted-modules-2.6.15-23-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karl@karlsdell:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
karl@karlsdell:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
karl@karlsdell:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1


Updated the xorg.conf file normally enough. Rebooted. Then, when I ran **fglrxinfo**, I got this output:

> karl@karlsdell:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)



Since Patrick-Ruff never explained how he "fixed the issue" with this showing up, I am left in the dark. However, the reply by JGKC9AYC looked promising, so I typed:

> cat /etc/X11/xorg.conf | grep fglrx

...and got output: Driver      "fglrx"

"**dmesg | grep fglrx**" produces NO output.

"**cat /etc/X11/xorg.conf | grep Load**" produces this output:

> 
karl@karlsdell:~$ cat /etc/X11/xorg.conf | grep Load
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"


"**sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri**" produces NO output.

I have attached the file produced by "**cat /var/log/Xorg.0.log > Xorg.log.txt**".

"**export LIBGL_DEBUG=verbose**" produces NO output.

My problem doesn't seem to be exactly like anyone else's problem that I can see. Oh, if you want to know, here is my Synaptic package install history:

> 
Commit Log for Mon Jun 12 18:53:25 2006


Upgraded the following packages:
app-install-data (0.1.32) to 0.1.33
binutils-static (2.16.1cvs20060117-1ubuntu2) to 2.16.1cvs20060117-1ubuntu2.1
deskbar-applet (2.14.1.1-0ubuntu3) to 2.14.2-0ubuntu1
evince (0.5.2-0ubuntu2) to 0.5.2-0ubuntu3
file-roller (2.14.2-0ubuntu2) to 2.14.3-0ubuntu1
firefox (1.5.dfsg+1.5.0.3-0ubuntu3) to 1.5.dfsg+1.5.0.4-0ubuntu6.06
firefox-gnome-support (1.5.dfsg+1.5.0.3-0ubuntu3) to 1.5.dfsg+1.5.0.4-0ubuntu6.06
gdm (2.14.6-0ubuntu2) to 2.14.6-0ubuntu2.1
gedit (2.14.2-0ubuntu3) to 2.14.3-0ubuntu1
gedit-common (2.14.2-0ubuntu3) to 2.14.3-0ubuntu1
gnome-app-install (0.1.32) to 0.1.33
libfreetype6 (2.1.10-1ubuntu2) to 2.1.10-1ubuntu2.1
libglib2.0-0 (2.10.2-1ubuntu3) to 2.10.3-0ubuntu1
libglib2.0-data (2.10.2-1ubuntu3) to 2.10.3-0ubuntu1
libnspr4 (2:1.firefox1.5.dfsg+1.5.0.3-0ubuntu3) to 2:1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06
libnss3 (2:1.firefox1.5.dfsg+1.5.0.3-0ubuntu3) to 2:1.firefox1.5.dfsg+1.5.0.4-0ubuntu6.06
libpq4 (8.1.3-4) to 8.1.4-0ubuntu1
libtiff4 (3.7.4-1ubuntu3) to 3.7.4-1ubuntu3.1
pcmcia-cs (3.2.8-5.2ubuntu5) to 3.2.8-5.2ubuntu6
zenity (2.14.1-0ubuntu2) to 2.14.2-0ubuntu1


> 
Commit Log for Mon Jun 12 19:04:50 2006


Installed the following packages:
libalut0 (1.0.1-1)
libopenal0a (1:0.0.8-1ubuntu1)
libphysfs-1.0-0 (1.0.0-5)
libsdl-image1.2 (1.2.4-1)
trigger (0.5.2-0ubuntu4)
trigger-data (0.5.2-0ubuntu1)


> 
Commit Log for Mon Jun 12 19:14:59 2006


Installed the following packages:
libsdl-mixer1.2 (1.2.6-1.1)
libsmpeg0 (0.4.5+cvs20030824-1.7)
planetpenguin-racer (0.3.1-5ubuntu2)
planetpenguin-racer-data (0.3.1-5ubuntu2)
planetpenguin-racer-extras (0.5-2)


Also, please let me stress, I have not done ANYTHING else except install Ubuntu, download and install these packages, go to these support forums, and run the commands mentioned above. I hope this helps you solve my problem!

Thanks.

---

### Post by Patrick-Ruff on 2006-06-13
I believe I followed someone elses directions from this thread about the 'mesa' issue. it was something about restricted modules and whatnot, look around the thread and you see it, thats why I'm here lol. I switched to KDE and noticed a lot better performance, I would LOVE to get gnome working perfectly, but I don't think thats an option :(

---

### Post by KLineD on 2006-06-13
Cataphract, try the following (if you have already done some of the following, skip those steps):

```

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo aticonfig &#8211;initial
sudo aticonfig &#8211;overlay-type=Xv
sudo gedit /etc/modules

```

At this point, gedit opens and you have to add the following (one per line)

```

fglrx
agppart

```

Restart your computer so those modules load. I tried restarting X and they would not load. If anyone knows how to do this without restarting it would be great.

Now you need to replace libGL.so.1.2 located in /usr/lib with another version. To do this first download [this deb file]("http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=i386&file=pool%2Frestricted%2Fl%2Flinux-restricted-modules-2.6.15%2Fxorg-driver-fglrx_6.9.0-8.24.8%2B2.6.15.10-2_i386.deb&md5sum=17bfd5dc12263fa4efb717a9b09db3b9&arch=i386&type=main") and open it with file roller (right click, open with) we are esentially decompressing the deb file to extract libGL.so.1.2 inside the deb file. Once you get libGL.so.1.2 out of the deb, replace the one in /usr/lib with the one you just got from the deb file.

If you type glxinfo in a console, you should get Direct Rendering YES as part of the output (look at the beginning).

Hope it helps.

*Edit: Corrected package name*

---

### Post by Cataphract on 2006-06-13
KLineD, here is the output of the first four commands you told me to run:

> 
karl@karlsdell:~$ sudo apt-get install xorg-driver-fgl
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-driver-fgl
karl@karlsdell:~$ sudo aticonfig –initial
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
karl@karlsdell:~$ sudo aticonfig –overlay-type=Xv
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2


It says as output to the first command that it couldn't find the package. Hmmm.

Then I added those lines to /etc/modules.

Rebooted, then downloaded a file called xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_i386.deb from the link you provided. But I can't open the file with file roller, as I get a dialog box:

> 
Could not open "xorg-driver-fglrx_6.9.0-8.24.8+2.6.15.10-2_i386.deb"

Archive type not supported.


Went ahead and did **glxinfo** anyway, and it says "direct rendering: No"

---

### Post by KLineD on 2006-06-13
I'm sorry, that package really is named xorg-driver-fglrx so:
```

sudo apt-get install xorg-driver-fglrx

```

You also need to have installed the restricted modules if you haven't already, you can do this with:
```

sudo apt-get install linux-restricted-modules-$(uname -r)

```

If you can't extract the deb file, try with the 'ar' command. I'm not sure it will work as I'm @ work right now:
```

ar x debfile.deb

```

The x option extracts. It will create three files: control.tar.gz, data.tar.gz and debian-binary. The second file contains the actual program so decompress it with file roller or
```

gunzip data.tar.gz
tar xvf data.tar

```

---

### Post by Cataphract on 2006-06-13
Ok, did that, and re-typed **glxinfo**, but still getting this:

> 
karl@karlsdell:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None


And I still can't open the .deb file in file roller.

EDIT: sorry, I posted right after you did.

---

### Post by KLineD on 2006-06-13
Please see my last post (I edited it to explain the deb file thing)

Also, after you installed fglrx, did you do the following??:
```

sudo aticonfig –initial
sudo aticonfig –overlay-type=Xv

```

It seems to me that your xorg file is not correctly configured so if you didn't please run those commands. After you do restart your computer and overwrite the file extracted from the deb file as I posted earlier.

---

### Post by Cataphract on 2006-06-13
My terminal can't find the 'ar' command. Did you mean something else instead?

EDIT: Yes, I ran those two sudo aticonfig commands afterward as well...still no luck.

EDIT: Hmmmm...for some reason my distro didn't come with support for ar, so I figured out I have to install binutils. Now I can use ar.

---

### Post by KLineD on 2006-06-13
not this time. As I said I don't knew if that particular command would work in Ubuntu as I'm not running Ubuntu right now, but you could try and search google and/or these forums for "decompress deb" or "extract deb" to see what you get.

Ok try this:
```

dpkg --fsys-tarfile package.deb | tar -xf - libGL.so.1.2

```

substitute package.deb for your deb package name. If it doesn't work, you have to understand I'm basically shooting in the dark here.

*EDIT: Ok I didn't saw you could already unpack the deb.*

---

### Post by Cataphract on 2006-06-13
Ok, I've tried this twice now...restarting after both times:

> 
karl@karlsdell:~$ sudo cp Desktop/usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2
Password:
karl@karlsdell:~$ glxinfo
name of display: :0.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None


I keep noticing the line:

> 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".


Could that have anything to do with it?

---

### Post by KLineD on 2006-06-13
> OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Actually what bothers me is that you still get Mesa GLX instead of fglrx.

Could you post your [Device] section of xorg.conf?

---

### Post by Cataphract on 2006-06-13
Ok, Here it is.

---

### Post by KLineD on 2006-06-13
```

Section "Device"
	Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

```

You have two Device sections, one with the open source ati drivers, the other one with the fglrx. Try commenting out the first Device section where "ati" is.

Also, my device section looks like this:
```

Section "Device"
        Identifier      "ATI Technologies, Inc. M9+ 5C63 [Radeon Mobility 9000 (AGP)]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection

```

I don't know what the BusID line does, but if it still doesn't works with your config, try commenting the second Device section, then changing ati for fglrx and see if it works for you.

---

### Post by Cataphract on 2006-06-14
OK, I re-installed Ubuntu and re-did the initial commands, then tried editing the xorg.conf file for the Device section(s) like so:

> 
#Section "Device"
#	Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
#	Driver      "ati"
#	BusID       "PCI:1:0:0"
#EndSection

#Section "Device"
#	Identifier  "aticonfig-Device[0]"
#	Driver      "fglrx"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
#EndSection

Section "Device"
        Identifier	"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection


...while not changing the Identifier in the first Screen section from "Default Screen" to "aticonfig-Screen[0]". That produces a problem when I went to reboot, as I got this X-server error screen that said:

> 
Data Incomplete in file /etc/X11/xorg.conf
Undefined Device "aticonfig-Device[0]" referenced by Screen "aticonfig-Screen[0]"
(EE) Problem parsing the config file
(EE) Error parsing the config file


This xorg.conf file is the key to the whole mess, isn't it?

(BTW, I figured out how to revert the changes and restart the X-server...Luckily I had read somewhere that you could restart the X-server by typing **startx**.)

---

### Post by KLineD on 2006-06-14
Ok do this, comment out all Device sections and leave the following:

```
#Section "Device"
# Identifier "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
# Driver "fglrx"
# BusID "PCI:1:0:0"
#EndSection
```

Make sure the modules required load, to do so:
```

lsmod 

```

You should see there listed fglrx. Restart X and you should be done.

---

### Post by Cataphract on 2006-06-14
I think I made a breakthrough:

I studied the xorg.conf file to figure out how it works...judging from the error screen before, I figured the X-server looked at the Screen variable in the ServerLayout section first:

> 
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection


So, it was looking for "aticonfig-Screen[0]". My next step was to make sure I commented out the Screen section that pointed to the ati driver as opposed to the fglrx driver which I left uncommented:

> 
Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
	Monitor    "LCD2060NX"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

#Section "Screen"
#	Identifier "aticonfig-Screen[0]"
#	Device     "aticonfig-Device[0]"
#	Monitor    "aticonfig-Monitor[0]"
#	DefaultDepth     24
#	SubSection "Display"
#		Viewport   0 0
#		Depth     24
#	EndSubSection
#EndSection


Now, the Device variable in that section points to "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]", so I took your advice and created a new Device section, commenting out the other two:

> 
#Section "Device"
#	Identifier  "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
#	Driver      "ati"
#	BusID       "PCI:1:0:0"
#EndSection

#Section "Device"
#	Identifier  "aticonfig-Device[0]"
#	Driver      "fglrx"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
#EndSection

Section "Device"
        Identifier	"ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
EndSection


Therefore, the Driver now has the value "fglrx"! So, now when I run **fglrxinfo**, I get this output:

> 
karl@karlsdell:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 2.0.5814 (8.25.18)


Also, **glxinfo** now says "direct rendering: Yes".

---

### Post by Cataphract on 2006-06-14
EDIT: I ran **lsmod** and found fglrx and agpgart both in there.

Ok, I tested all of this out on some games and screensavers:

Planet Penguin Racer runs well.
Trigger runs awesome.
Hufo's Tunnel screensaver runs much faster, although it still seems a little "stop and go" to me (is it supposed to be perfectly smooth?)
Hyperspace screensaver is good but it has this weird image at the bottom left at the beginning that goes away after about 1.5 seconds.

Also, I noticed that the games are running in Fullscreen now.

Do you think there is anything here to be concerned about? If not, thanks for all your help! I've tried other Linux distros such as Mandrake, Red Hat, and most recently Debian, but the cloogeyness of them especially in how they interact with computer hardware has always made me shy away from Linux. Ubuntu might be the first Linux distro that I can actually get to work with all my computer's hardware devices. If so, it's about time! :p

---

### Post by kvonb on 2006-06-14
------------------------------------------------------------------------------------------------------
This is a copy of my post to the cedega forum after spending a week messing with my ATI 9200SE and Dapper and getting no help or support from Cedega themselves!  I left the whole thing intact but you can ignore the parts about Battlefield 1942 and Cedega if you don't need them.

** COPY THESE INSTRUCTIONS TO YOUR COMPUTER BEFORE REBOOTING **

PLEASE don't complain about getting less than 10,000,000 FPS, it is extremely ridiculous, childish, and unimportant as anything above 30FPS is playable in any game!  The human eye can't make out the difference above 30FPS, this is an accepted scientific fact :rolleyes:
------------------------------------------------------------------------------------------------------
OK, in the hope that this will help someone else keep their hair, these are the EXACT steps I took to get BF1942 working with an ASUS Radeon 9200SE on Ubuntu Dapper (6.06 release).

I started with a CLEAN install of Dapper and a CLEAN xorg.conf, I STRONGLY suggest you do the same to avoid any problems!
------------------------------------------------------------------------------------------------------
Enable "universe" and "multiverse" in Synaptic
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo gedit /etc/default/linux-restricted-modules-common
Change DISABLED_MODULES="" to DISABLED_MODULES="fglrx"
sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
Download the ATI driver installer from [www.ati.com](www.ati.com) (I used 8.25.18-x86)
Make a folder for this work, I used ~/ati-install and move the downloaded file into it, this will make it easier later
Change to the new folder: cd ~/ati-install
chmod +x ati-driver-installer-8.25.18-x86.run
./ati-driver-installer-8.25.18-x86.run --buildpkg Ubuntu/dapper
sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.25.18-1_i386.deb
sudo dpkg -i fglrx-control_8.25.18-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
## and now for the trick part ##
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
Download older libGL.so from: [http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2) Move the downloaded libGL.so.1.2 to ~/ati-install
sudo mv /usr/lib/libGL.so.1.2 /usr/lib/old-libGL.so.1.2
sudo cp ./libGL.so.1.2 /usr/lib/
sudo cp ./libGL.so.1.2 /usr/lib/fglrx/
Check /usr/lib/libGL.so.1 link and make sure it points to /usr/lib/libGL.so.1.2
Reboot
------------------------------------------------------------------------------------------------------
Test:
Run: fglrxinfo
If all went well, you should see a version of the following:
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9xxx Generic
OpenGL version string: 2.0.5814 ( 8.25.18 )

Run: fgl_glxgears
This will give you a good framerate. TIP: make the window smaller to get a higher framerate!
------------------------------------------------------------------------------------------------------
Install Cedega:
Search the web for xlibs_6.8.2-77_all.deb and download it
sudo dpkg -i xlibs_6.8.2-77_all.deb
sudo dpkg -i cedega_5.1_i386.deb
Run Cedega and do an on-line update which will include the latest engine
------------------------------------------------------------------------------------------------------
Install BF1942:
Install whatever version you have as normal (I have the original 1.0 I think)
Search for and download the 1.45 update, then install
Search for the 1.45 no-cd patch and install
Search for merciless_1942_v.4.1.4.zip, unzip and install (this bypasses the intro movies solving that problem and also gives better textures and flags)
In Cedega, right click on the BF1942 icon and select "edit profile"
Select the "Graphics" tab and untick ARB_VBO Extension
Apply and OK
Run BF1942 and see if it works, if not, bang head on desk and start again!
------------------------------------------------------------------------------------------------------
I turned my graphics settings up to maximum with everything enabled and it works well. I get a flickering on the "Health" box (bottom left of screen) but it is not critical and everything else works. With the ARB_VBO enabled I got blank screens in-game and my weapon vanished at random, although it did still work. I can now fly my "Stuka" and strafe nasty allies with glee Very Happy
------------------------------------------------------------------------------------------------------
ADDITIONAL:

It seems that BF1942 won't start if you try to start it in 1024x768x32 mode! It does work if you start in 800x600x32 and then change to 1024x768x32 (sometimes!)
------------------------------------------------------------------------------------------------------

I'm not the brains behind these instructions, I just found them, condensed them, and followed them to the letter and it worked for me.

Special thanks to "escape" and "joshrobinson" on ubuntuforums.org for the real work behind this.
------------------------------------------------------------------------------------------------------
I believe the main problem lies in the ATI drivers which is a shame because I get a much crisper and cleaner desktop picture with my 9200 over my nvidia GeForce and ATI cards are half the price of nvidia!  They are getting better however :)

Regards,

Kev :cool:

---

### Post by KLineD on 2006-06-14
[QUOTE=Cataphract]EDIT: I ran **lsmod** and found fglrx and agpgart both in there.

Ok, I tested all of this out on some games and screensavers:

Planet Penguin Racer runs well.
Trigger runs awesome.
Hufo's Tunnel screensaver runs much faster, although it still seems a little "stop and go" to me (is it supposed to be perfectly smooth?)
Hyperspace screensaver is good but it has this weird image at the bottom left at the beginning that goes away after about 1.5 seconds.

Also, I noticed that the games are running in Fullscreen now.

Do you think there is anything here to be concerned about? If not, thanks for all your help! I've tried other Linux distros such as Mandrake, Red Hat, and most recently Debian, but the cloogeyness of them especially in how they interact with computer hardware has always made me shy away from Linux. Ubuntu might be the first Linux distro that I can actually get to work with all my computer's hardware devices. If so, it's about time! :p[/QUOTE]

It seems like you nailed it! Glad I could help. Enjoy your full 3D acceleration.

---

### Post by Cataphract on 2006-06-14
[QUOTE=KLineD]It seems like you nailed it! Glad I could help. Enjoy your full 3D acceleration.[/QUOTE]

Wow, you are so selfless :D 

Now, is there any way to get full 32-bit (as opposed to 24 bits as, according to xorg.conf, it is now) screen color?

---

### Post by KLineD on 2006-06-14
Now that is out of my league unfortunately... :?:

---

### Post by alejandrops on 2006-06-19
Hi! 
I already installed Ati drivers and my XGL is working OK, glxgears ir giving me around 5000 fps and everithing seems to work OK.
however when I type fglrxinfo the result is
```

alejandrops@alejandrops-laptop:~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.5814 (8.25.18)

```

I already change some stuff in xorg.conf and my xorg.comf looks like

```


Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "es"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "on"
	Option	    "MaxTapTime" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

# Section "Device"
# 	Identifier  "ATI Technologies, Inc. ATI Default Card"
# 	Driver      "vesa"
# 	BusID       "PCI:1:0:0"
# EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "aticonfig-Device[0]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

is there any problem with the line 

Xlib:  extension "XFree86-DRI" missing on display ":1.0". ?????

Mi former xorg.conf was:

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "es"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. ATI Default Card"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

and worked just like my new one!
thanks in advance.

alejandrops

---

### Post by alejandrops on 2006-06-19
Forgot to add: I'm usung an ati x1400 in a Dell 9400, my resolution is 1920x1200.

---

### Post by alejandrops on 2006-06-19
also, glxinfo says: direct rendering: No!!!!
how can be possible that XGL works OK?
```

alejandrops@alejandrops-laptop:~$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 1.2 (2.0.5814 (8.25.18))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
alejandrops@alejandrops-laptop:~$ sudo gedit /etc/X11/xorg.conf
Password:

alejandrops@alejandrops-laptop:~$ sudo gedit /etc/X11/xorg.conf
xorg.conf             xorg.conf.backup      xorg.conf.original-0
xorg.conf~            xorg.conf.fglrx-0     xorg.conf.raro
alejandrops@alejandrops-laptop:~$ sudo gedit /etc/X11/xorg.conf.backup
alejandrops@alejandrops-laptop:~$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 1.2 (2.0.5814 (8.25.18))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr,
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon

```

---

### Post by KLineD on 2006-06-19
That's Ok AFAIK it reports that way precisely because of the Xgl server. Run the same command with normal X server and see the difference for yourself

---

### Post by firetux on 2006-06-20
[QUOTE=Cataphract]Wow, you are so selfless :D 

Now, is there any way to get full 32-bit (as opposed to 24 bits as, according to xorg.conf, it is now) screen color?[/QUOTE]

The linux-24bit is the same as windows-32bit, with windows the last bits are for alpha transparency and are hardly ever used. Both give you 16 million colours, which is the max any monitor can handle.

---

### Post by gumbald on 2006-06-21
[QUOTE=kvonb]------------------------------------------------------------------------------------------------------
I started with a CLEAN install of Dapper and a CLEAN xorg.conf, I STRONGLY suggest you do the same to avoid any problems!
------------------------------------------------------------------------------------------------------
Enable "universe" and "multiverse" in Synaptic
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo gedit /etc/default/linux-restricted-modules-common
Change DISABLED_MODULES="" to DISABLED_MODULES="fglrx"
sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
Download the ATI driver installer from [www.ati.com](www.ati.com) (I used 8.25.18-x86)
Make a folder for this work, I used ~/ati-install and move the downloaded file into it, this will make it easier later
Change to the new folder: cd ~/ati-install
chmod +x ati-driver-installer-8.25.18-x86.run
./ati-driver-installer-8.25.18-x86.run --buildpkg Ubuntu/dapper
sudo dpkg -i xorg-driver-fglrx_8.25.18-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.25.18-1_i386.deb
sudo dpkg -i fglrx-control_8.25.18-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
## and now for the trick part ##
sudo ln -s /usr/lib/dri /usr/lib/xorg/modules/dri
Download older libGL.so from: [http://www.ground-impact.com/libGL.so.1.2](http://www.ground-impact.com/libGL.so.1.2) Move the downloaded libGL.so.1.2 to ~/ati-install
sudo mv /usr/lib/libGL.so.1.2 /usr/lib/old-libGL.so.1.2
sudo cp ./libGL.so.1.2 /usr/lib/
sudo cp ./libGL.so.1.2 /usr/lib/fglrx/
Check /usr/lib/libGL.so.1 link and make sure it points to /usr/lib/libGL.so.1.2
Reboot

Regards,

Kev :cool:[/QUOTE]

Worked for me :lol: But one thing to ask, if I now change my kernel to a 686 will this undo all the hard work? Could be a silly question, just wanna make sure. I'd rather have working 386 than non-working 686...

---

### Post by gumbald on 2006-06-22
Just done updates, and I've gone back to Mesa...

I went back through the process above again and it immediately told me that I had updates available, fglrx-control and fglrx-kernel-source. How do I adapt the above to cope with these or stop it asking me about them?

---

