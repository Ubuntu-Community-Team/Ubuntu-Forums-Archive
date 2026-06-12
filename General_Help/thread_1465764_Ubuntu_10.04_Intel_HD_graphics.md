---
title: "Ubuntu 10.04 Intel HD graphics"
date: 2010-04-29
forum: General Help
---

### Post by talhaguy on 2010-04-29
Hey everyone,

I am looking to install Ubuntu 10.04 on my laptop.

The laptop has an intel core i3 330M 2.13 GHz processor with integrated graphics, more specifically Intel Graphics Media Accelerator HD (Core i3).

When I installed Ubuntu 9.10 on this laptop, the integrated graphics were not recognized and I had to use safe graphics mode.

So my question is: Is the Intel Graphics Media Accelerator HD (Core i3) finally supported in Ubuntu 10.04?

Thanks!

---

### Post by kaibob on 2010-04-29
There are quite a few threads on this. Lucid works fine with the Intel HD graphics.

---

### Post by talhaguy on 2010-04-29
Oops, sorry! I was in a big rush, gotta slow down, huh. Glad to hear it though!

---

### Post by kaibob on 2010-04-29
> **talhaguy said:**
> Oops, sorry! I was in a big rush, gotta slow down, huh. Glad to hear it though!
Please let us know how things work out. A lot of new machines are using the Intel HD graphics, and it would be helpful to get more user experiences.

---

### Post by talhaguy on 2010-05-01
> **kaibob said:**
> Please let us know how things work out. A lot of new machines are using the Intel HD graphics, and it would be helpful to get more user experiences.

Nice! Everything seems to be working great, including Compiz!

---

### Post by kaibob on 2010-05-02
> **talhaguy said:**
> Nice! Everything seems to be working great, including Compiz!
That's good news. The new Intel HD graphics seems to be fairly capable, and I suspect it will be used in many new machines. They needed to get this right in lucid and appear to have done that. Thanks for reporting back.

---

### Post by jason_m on 2010-05-02
I came across this thread before upgrading from 9.10 to 10.04 last night.  The integrated graphics on my Core i3 work great now.  Previously Compiz would hard crash my system, and video playback of just about any file would stop and buffer every 2-3 seconds.  Very happy with i3 purchase now!

---

### Post by danny2525 on 2010-05-02
Guys I have a new HP dv6 HP laptop with the I5 processor and Intel HD graphics.The only thing that didn't install automatically was the wireless card but I went to hardware drivers and installed the oem driver.All compiz effects work perfect great system now going to remove my winodws 7 partition

---

### Post by g2tftp on 2010-06-23
With 10.04, the brightness controls is not working. I have to use compiz accessibility function to tone down the brightness of individual windows. It seems to be a driver issue.

---

### Post by rakete on 2010-07-19
I am on a dell latitude E5410 with core i5 and Intel HD Graphics.

Installed ubuntu 10.04, my touchpad and Suspend mode won't work, I can live with that.

But: If I try to get an external Monitor working, ubuntu crashes. I mean, it crashed really, not only xserver crashing.

If I am logged in via ssh, the logged in Terminal crashed, too. I have to force the terminal to close via kill.

Maybe this is some vendor related issue, but It seems, as if there are some driver or kernel related bugs  with this new "On-Top-Of-CPU"-GPU.

I posted this bug to launchpad and dell... hopefully something happens soon. I have nightmares at night, where I have to prepare a presentation and windows keeps getting my workspace corrupted with win-encoding and all my colleagues laughing at me, because this FOSS guy (me) presents his stuff with windows, because ubuntu is hanging his system when attaching it to a beamer.

---

### Post by Jason H on 2010-07-20
E6510 is also unable to start X.  I've tried a LiveCD with/without a second monitor and docking station and it cannot even run the CD Diags without spinning down the drive and turning the monitor black.

Looks like there is ongoing development on this front:
[https://lists.ubuntu.com/archives/ubuntu-x/2010-February/000737.html](https://lists.ubuntu.com/archives/ubuntu-x/2010-February/000737.html)

---

### Post by rakete on 2010-07-28
I do not know exactly what happens in this script or prog, but crash can be provoked with 

xrandr --auto

---

### Post by bonfire89 on 2010-09-10
> **kaibob said:**
> There are quite a few threads on this. Lucid works fine with the Intel HD graphics.

I wish I knew about these threads that you speak off. Because if I did I could be getting my Ubuntu install up in running instead of being left to wonder.

Well, I guess there is hope.

---

### Post by perspectoff on 2010-09-10
> **bonfire89 said:**
> I wish I knew about these threads that you speak off. Because if I did I could be getting my Ubuntu install up in running instead of being left to wonder.

Well, I guess there is hope.

"Knowing that there is a book doesn't give you knowledge. You actually have to read the book."

---

### Post by Aikon- on 2010-12-28
> **perspectoff said:**
> "Knowing that there is a book doesn't give you knowledge. You actually have to read the book."

It is difficult to read a book that you cannot find.

---

### Post by pdwOnline on 2011-07-18
Ubuntu 10.04 works excellent with Intel HD Graphics. However, DO NOT UPGRADE to Ubuntu 11.4 !!

Unfotrunate I did, and graphics was set back to standard no 3GL stuff..

---

### Post by ATMOS_SKY on 2011-08-07
Hello all, so I am very noobish here and need help.

I have an HP Pavilion g4-1104dx Notebook PC You can see it's build [@ here]("http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=4063&lc=en&cc=us&dlc=en&sw_lang=&product=5128880")

I am working on a fresh ubuntu 10.04.3 install and after running

```
sudo lshw -C video
```
Output:
[HTML]  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Sandy Bridge Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:c0000000-c03fffff memory:b0000000-bfffffff(prefetchable) ioport:4000(size=64)[/HTML]

I installed virtualbox (which is awesome btw) and my I had it rate my system.  I did not install the windows video drivers btw (was I supposed to for guest OS's... does virtual box do this already?

*see VBox.png* [IMG]http://ubuntuforums.org/attachment.php?attachmentid=199414&stc=1&d=1312692342[/IMG]

I am not looking for a monster gaming machine, I just thought something was wrong.

I then read around and I think foolishly proceeded to add
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
```
[from this thread http://ubuntuforums.org/showthread.php?t=1779970]("http://ubuntuforums.org/showthread.php?t=1779970")

I then did a update manager and it updated what looked like some graphics drivers but after a restart it is still the * generic * configuration.
I intend on setting up compiz and eventually window snapping but I want to make sure my graphics drivers are installed correctly.

I am typing this from my ubuntu machine now but the * aspect ratio* I think that's it seems different and a little fuzzier than what it was before I updated the repository.

Any suggestions?

BTW, this is my first laptop where it is 100% linux.  Yes I have virtualbox but that is only for my dedicated windows programs I must use and only are for windows.  BTW virtual box is awesome.

Is there a checklist for installing ubuntu for fresh installs to make sure you have all your drivers installed correctly?

I found this forum [10.04 with Intel Sandy Bridge Integrated Graphics (max 800x600) - how to change it]("http://ubuntuforums.org/showthread.php?t=1747206")
that says

> **@Dilli said:**
> We're facing similar problems with a H67 motherboard. You could try to install a new intel driver from: [https://launchpad.net/~glasen/+archive/intel-driver](https://launchpad.net/~glasen/+archive/intel-driver)

The complete resolutions are shown with this driver, but our machine is jumping back to the login screen when we're trying to change them.

Should I follow it?

Thank you everyone,

ATMOS_SKY

---

### Post by Bbeto on 2012-01-23
> **pdwOnline said:**
> Ubuntu 10.04 works excellent with Intel HD Graphics. However, DO NOT UPGRADE to Ubuntu 11.4 !!

Unfotrunate I did, and graphics was set back to standard no 3GL stuff..
Hey pdw, i installed 10.04 but my graphics don't work well. I have intel HD graphics and i have a low resolution issue: the max resolution that ubuntu lets me set is 1024x768 and my screen supports 1366x768.

I've been weeks trying to fix this. Is there anyone who can help me?
Thanks

---

### Post by GusPS on 2012-03-06
I'm facing the same problem. There's still no solution I guess. I've filled this launchpad bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397)

Here is another thread: [http://ubuntuforums.org/showthread.php?t=1728526&page=4](http://ubuntuforums.org/showthread.php?t=1728526&page=4)

---

### Post by galapogos on 2012-07-24
> **pdwOnline said:**
> Ubuntu 10.04 works excellent with Intel HD Graphics. However, DO NOT UPGRADE to Ubuntu 11.4 !!

Unfotrunate I did, and graphics was set back to standard no 3GL stuff..
Hi,

How did you get 10.04 to work with Intel HD graphics?

I got it to work on 1 system with a 2nd gen intel Core i5-2x00 CPU with Intel HD 3000 series graphics. I can't remember what I did exactly, but I remember installing the glasen ppa drivers.

I tried to do the same thing on a newer Core i7 3x00 system with Intel HD 4000 series graphics, using the following commands, but it didn't work

```

sudo add-apt-repository ppa:glasen/intel-driver sudo apt-get update && sudo apt-get upgrade sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty

```

I have a dual monitor setup(1 VGA and 1 DVI) and only 1 unknown monitor is detected at a resolution of 1280x1024. My main monitor's native resolution is however 1920x1080.

Does anyone know how to get this working?

Thanks.

---

### Post by Gyokuro on 2012-07-24
Hi

I have tested 10.04 on a laptop with i3 (GPU HD3000) and the problem was that Xorg and shipped kernel were too old to support all graphic modes/hardware features. Therefore Vesa got used - if your really need 10.04 on this laptop you have to use alternative ppa's for xorg and kernel but I think it's some kind of wasted time - it's better to install 12.04 as it works (I'm writing this on a laptop with i5 and HD3000 GPU and everything runs fine).

---

### Post by galapogos on 2012-07-25
I managed to get 10.04 to work with the intel HD 4000 graphics with an updated oneiric kernel. The natty kernel wasn't new enough to support Ivy Bridge.

---

