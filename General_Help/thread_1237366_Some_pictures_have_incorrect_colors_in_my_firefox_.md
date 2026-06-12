---
title: "Some pictures have incorrect colors in my firefox 3.5 (shiretoko). Why?"
date: 2009-08-11
forum: General Help
---

### Post by lethalfang on 2009-08-11
Some pictures have incorrect colorings in firefox 3.5, even though the colors show up correctly in all of my other browsers. What's the problem?

Below is a screenshot. On the left is the incorrectly colored picture in Shiretoko (firefox 3.5). On the right is the correct picture in Firefox 3.0.

---

### Post by lethalfang on 2009-08-11
Anyone with any possible solutions to the odd problem?
Thanks.

---

### Post by dcstar on 2009-08-12
> **lethalfang said:**
> Some pictures have incorrect colorings in firefox 3.5, even though the colors show up correctly in all of my other browsers. What's the problem?

Below is a screenshot. On the left is the incorrectly colored picture in Shiretoko (firefox 3.5). On the right is the correct picture in Firefox 3.0.

Because there is a new "feature" on rendering images, do a search for the solution as it is quite common.

---

### Post by lethalfang on 2009-08-12
Got it: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/386132](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/386132)

Type "about:config" in the address bar, find "gfx.color_management.mode" and change the value from 2 to 0.

---

### Post by P4man on 2009-08-12
Its not a bug. Its a feature. Can't you tell from those screenshots that ubuntu is colouring the debian logo.. in.. ubuntu colors ? ROFL!

---

### Post by Inarius on 2009-08-18
Hey, You'll be pleased to know that I am also having the same problem (I think), though my colours look to be even more screwed up.  I don't like the option of setting colour management to 0 (i.e. off), as that is just sweeping the problem under the carpet.  Searching online has offered nothing, just how to turn it on (for ff-3.0), and how to turn it off for (ff-3.5)

I've attached 2 pics from ff-3.5, saving them as untagged, so that you don't see a doubly screwed up picture.

The picture of the mountain comes from [http://www.color.org/version4html.xalter](http://www.color.org/version4html.xalter) which is a testing site to see how the browser performs, the picture on the left is what I see in firefox-3.5, the image on the right is how I SHOULD see the image, and I do on the windows version of 3.5.

I have no idea where the problem lies, whether it is ff-3.5 or ubuntu, missing libraries, or what.

Earlier, I opened up the pdf file on that site on 3.5 using the acrobat plugin (on Ubuntu) and that displays perfectly (ICC 4 + 2).  I am using Jaunty btw, with the firefox-3.5 package installed.

---

### Post by kibster on 2009-08-18
lethalf,
I have the same problem...I've looked for an answer and found none to be had...I did the trick for looking at the config file..and mine was already set  0  And that was only fix I found and it didn't work.

---

### Post by lavinog on 2009-08-18
is this an ATI bug? If so what drivers are you using?
The new fglrx was released yesterday.

---

### Post by kibster on 2009-08-18
I'm sorry for not knowing ...But how would I look to see what drivers I am using.

---

### Post by Inarius on 2009-08-18
> **lavinog said:**
> is this an ATI bug? If so what drivers are you using?
The new fglrx was released yesterday.

Hmm, I guess that could be it, I have Integrated UMA Graphics ATI Mobility Radeon HD 3200, so I am using the ATI/AMD FGLRX driver.  Do you know what version the new one is, I have 2:8.600 currently installed.

---

### Post by lavinog on 2009-08-18
> **Inarius said:**
> Hmm, I guess that could be it, I have Integrated UMA Graphics ATI Mobility Radeon HD 3200, so I am using the ATI/AMD FGLRX driver.  Do you know what version the new one is, I have 2:8.600 currently installed.

8.64.3 is the August version (9-8)

---

### Post by Inarius on 2009-08-18
> **kibster said:**
> I'm sorry for not knowing ...But how would I look to see what drivers I am using.

System -> Administration -> Hardware Drivers, I then got the version number from Synaptic.

---

### Post by lavinog on 2009-08-18
> **kibster said:**
> I'm sorry for not knowing ...But how would I look to see what drivers I am using.

What model video card do you have?
```
lshw -c video
```

```

grep 'ATI Proprietary' /var/log/Xorg.0.log

```
should result in something like this if you are using the restricted driver:
```

(II) ATI Proprietary Linux Driver Version Identifier:8.64.3
(II) ATI Proprietary Linux Driver Release Identifier: 8.64                                 
(II) ATI Proprietary Linux Driver Build Date: Jul 14 2009 21:18:29
(WW) This ATI Proprietary Linux Driver does not guarantee support of video driver ABI higher than 2.0

```

---

### Post by Inarius on 2009-08-18
> **lavinog said:**
> 8.64.3 is the August version (9-8)

Is that in Jaunty or Karmic or both?  I can't see it here [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=fglrx](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=fglrx)

I am using Jaunty btw.

---

### Post by lavinog on 2009-08-18
> **Inarius said:**
> Is that in Jaunty or Karmic or both?  I can't see it here [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=fglrx](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=fglrx)

I am using Jaunty btw.

I am using jaunty. It is on the ati website.

envy used to be a package that would automatically install it, but I can't find any information about the package in jaunty. Most likely it will update to the 9-7 version (which is very buggy in my opinion)

What video card do you have? You may be able to use the open source driver.

I don't know how easy installing the proprietary driver is anymore. Once installed, it is easy to do the updates, but the initial install used to require messing with some config files.  Some of the how-tos are more complicated than it should be like on [wiki.cchtml.com](wiki.cchtml.com) because in the past the gui install method didn't work.

---

### Post by Inarius on 2009-08-18
> **lavinog said:**
> I am using jaunty. It is on the ati website.

envy used to be a package that would automatically install it, but I can't find any information about the package in jaunty. Most likely it will update to the 9-7 version (which is very buggy in my opinion)

What video card do you have? You may be able to use the open source driver.

I don't know how easy installing the proprietary driver is anymore. Once installed, it is easy to do the updates, but the initial install used to require messing with some config files.  Some of the how-tos are more complicated than it should be like on [wiki.cchtml.com]("http://wiki.cchtml.com") because in the past the gui install method didn't work.

I have just looked at Xorg and it says I am using 8.60.40, before I was going by Synaptic.

lshw gives:
```
  *-display               
       description: VGA compatible controller
       product: RS780M/RS780MN [Radeon HD 3200 Graphics]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=fglrx_pci latency=0 module=fglrx
```

---

### Post by kibster on 2009-08-18
The Grep command didnt give any results.. but .

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by nanonils on 2009-08-31
> **lethalfang said:**
> Got it: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/386132](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/386132)

Type "about:config" in the address bar, find "gfx.color_management.mode" and change the value from 2 to 0.

Excellent! That fixed it for me after 3 psychedelic weeks. Curious that Epiphany looked normal - I thought the two browsers would share more than just the "chrome".

---

### Post by philinux on 2009-08-31
Looks like another ATI driver problem eh.

---

### Post by nanonils on 2009-08-31
> **philinux said:**
> Looks like another ATI driver problem eh.

Uurgh! You are right. And I thought I had an NVIDIA in my WildDog. Will notify System76.com Might help once this browser comes out of its "Shiretoko" wild park status... 

lshw produces: 
 *-display
                description: VGA compatible controller
                product: RV770 LE [Radeon HD 4800 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx

---

### Post by joshuapurcell on 2010-10-30
Same problem here after installing 10.10 and the latest ATI driver. I'm on a Thinkpad W500. This may be an old thread related to an old problem, but it's still a problem.

---

### Post by jvdurme on 2010-12-13
> **lethalfang said:**
> Got it: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/386132](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/386132)

Type "about:config" in the address bar, find "gfx.color_management.mode" and change the value from 2 to 0.

Thanks, worked like a charm!

---

### Post by ayalsule on 2011-03-29
> **lethalfang said:**
> Got it: [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/386132](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/386132)

Type "about:config" in the address bar, find "gfx.color_management.mode" and change the value from 2 to 0.


worked for me after

---

