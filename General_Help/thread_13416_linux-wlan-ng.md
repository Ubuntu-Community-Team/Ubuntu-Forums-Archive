---
title: "linux-wlan-ng"
date: 2005-01-31
forum: General Help
---

### Post by travail101 on 2005-01-31
is there anyway that we could get the linux-wlan-ng package onto the liveCDs in the future, the only liveCD i have seen which specifically states having it is the Linux Router Pro livecd (or something like that) and.... they charge for it, so it's not really an option.

so yeah, I can see no reason why not to include the linux-wlan-ng package, it's not like an insainly large package, and it will increase the wireless support on the LiveCD, specifically I need the prism2_usb module, and any required tools to get it to work (D-Link DWL-122) 

If any of you are asking yourself "why does this guy even need wireless support on the LiveCD, why doesn't he just install Ubunto and download the linux-wlan-ng package for himself?" well I would, (well no I guess I wouldn't, I'm really a Gentoo man) but the problem is, I am poor, and my hard drive is plagued with bad blocks, and I am 6000 miles from home and don't have all my tools at my hands, or my friends tools, and I need a livecd that get's my wireless working, and Samba working, so I can save as much data from my rapidly failing harddrive. and secondly so I can use my computer for Chat and websurfing without worrying about my rapidly failing harddrive...

I haven't yet ruled out the possibility that I'm just retarded and can't read, and linux-wlan-ng is actually already on the liveCD or something, but if that is the case please do tell me how to use it, because if it's there it certainly doesn't autoload, and I can't modprobe prism2_usb...

and if you can offer no solution thanx for at least reading.

---

### Post by dickinsd on 2005-02-26
[QUOTE=travail101]is there anyway that we could get the linux-wlan-ng package onto the liveCDs in the future, the only liveCD i have seen which specifically states having it is the Linux Router Pro livecd (or something like that) and.... they charge for it, so it's not really an option.

so yeah, I can see no reason why not to include the linux-wlan-ng package, it's not like an insainly large package, and it will increase the wireless support on the LiveCD, specifically I need the prism2_usb module, and any required tools to get it to work (D-Link DWL-122) 

If any of you are asking yourself "why does this guy even need wireless support on the LiveCD, why doesn't he just install Ubunto and download the linux-wlan-ng package for himself?" well I would, (well no I guess I wouldn't, I'm really a Gentoo man) but the problem is, I am poor, and my hard drive is plagued with bad blocks, and I am 6000 miles from home and don't have all my tools at my hands, or my friends tools, and I need a livecd that get's my wireless working, and Samba working, so I can save as much data from my rapidly failing harddrive. and secondly so I can use my computer for Chat and websurfing without worrying about my rapidly failing harddrive...

I haven't yet ruled out the possibility that I'm just retarded and can't read, and linux-wlan-ng is actually already on the liveCD or something, but if that is the case please do tell me how to use it, because if it's there it certainly doesn't autoload, and I can't modprobe prism2_usb...

and if you can offer no solution thanx for at least reading.[/QUOTE]
 Hello.

You may want to look at this:

[https://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo](https://www.ubuntulinux.org/wiki/LiveCDCustomizationHowTo)

You could simply create your own livecd (as long as your dodgy hard drive can hold up to making the customised live cd.

Dave

---

### Post by ssam on 2005-02-26
i agree, linux-wlan-ng should be part of the default install. if someones only conection to the internet is with wireless card that need this, then how can they use synaptic to get linux-wlan-ng.

good hardware support 'out of the box' is something that linux needs. i think it is great how i can plug a random printer/scanner/camera into linux and it just works, whereas windows people need to install drivers. if this could work for everything that would be very cool.

so i vote for as many drivers as posible to be installed as default (also things like winmodem drivers). if there is a chance that a desktop user might have a device, and its possible for linux to support it then it should. i'd contribute to a bounty for this.

ssam

---

### Post by dickinsd on 2005-02-26
[QUOTE=ssam]i agree, linux-wlan-ng should be part of the default install. if someones only conection to the internet is with wireless card that need this, then how can they use synaptic to get linux-wlan-ng.

good hardware support 'out of the box' is something that linux needs. i think it is great how i can plug a random printer/scanner/camera into linux and it just works, whereas windows people need to install drivers. if this could work for everything that would be very cool.

so i vote for as many drivers as posible to be installed as default (also things like winmodem drivers). if there is a chance that a desktop user might have a device, and its possible for linux to support it then it should. i'd contribute to a bounty for this.

ssam[/QUOTE]
 Yeah, but no longer would Ubuntu be a one disc install, it would be **HuGE** imagine how many devices there are out there - it would be impossible.

However I do think that (especially live distros) linux distros should come with a pretty large selection of wireless drivers as it really is a modern technology that is used more and more.

I know your kinda stuck in a catch 22 situation, as you can't get the drivers with out the NIC, but you can activate the NIC with out the drivers.

There is only so much they can fit on a CD.

Dave

---

### Post by Slavakion on 2005-03-04
I don't know how easy/possible this would be, but how about this: One CD for the default Ubuntu installation. A second *optional* CD that contains a bunch of drivers. I know that if CD2 had wlan and madwifi on it, I wouldn't hesitate to download it. But that's just me.

---

### Post by xen on 2006-05-19
I'm stuck in exactly the same situation as you!

---

