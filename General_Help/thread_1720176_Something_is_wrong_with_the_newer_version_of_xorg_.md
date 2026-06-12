---
title: "Something is wrong with the newer version of xorg (11.04)"
date: 2011-04-02
forum: General Help
---

### Post by alazou on 2011-04-02
Hi everyone
I hope I'm posting this in the correct section of the forums.
A while ago I was using opensuse 11.4 and I had some issues when using nouveau. Please read the first post of this thread for more information
see :[http://forums.opensuse.org/english/get-technical-help-here/pre-release-beta/453621-my-experience-nvidia-opensuse-factory.html]("http://forums.opensuse.org/english/get-technical-help-here/pre-release-beta/453621-my-experience-nvidia-opensuse-factory.html")

Those issues are what made me switch to kubuntu, and I thought there were less present in here. Indeed in 10.10 I used the xorg-edgers ppa, and the 2.6.38 kernel so I thought I was using more or less the same configuration than when I was using opensuse. But today I upgraded to kubuntu 11.04 and the problems were back.

Do all, some or none of you experience those problems when using nouveau :confused:? I'll like to hear your input.

thanks

---

### Post by pjbgravely on 2011-04-03
I have no experience but it could be the newer version of Xorg. Try rolling back if you can. The touch pad showing as a PS-2 mouse may be a clue that it is a hardware problem, or a mouse driver problem. I was surprised to hear the nouveau was giving you 3D acceleration, I didn't know it was that far yet.

Paul

---

### Post by ankspo71 on 2011-04-03
Hi,
On the xorg-edgers PPA page it recommends using ppa-purge to remove their packages before attempting any upgrades. Have you already done that before upgrading? [https://launchpad.net/~xorg-edgers/+archive/ppa/](https://launchpad.net/~xorg-edgers/+archive/ppa/)  

It would be a good idea to double check to see if the repository URL is set for natty (not maverick) too. The location of the repository URL should be located in /etc/apt/sources.list.d/ , but if not, it might be located in /etc/apt/sources.list 

I'm using an Nvidia GeForce8400GS 512M PCI-E16 graphics on a Biostar/VIA P4M900-M4 motherboard, and using USB keyboard and mouse (no touchpad). The only issues I've had with nouveau drivers is that they felt too sluggish for my system, so I have been using the non-free Nvidia drivers provided through Ubuntu. The version "current"(270.30-0ubuntu3) is working good for me in Ubuntu/Kubuntu 11.04 beta. 

I had an opportunity to try the opensource "experimental" accelerated driver (nouveau?) for 11.04, and it worked pretty good, but I don't see it listed in my "additional drivers" utility anymore.  

Hope this helps you find the problem.

---

### Post by alazou on 2011-04-03
> **pjbgravely said:**
> I have no experience but it could be the newer version of Xorg. Try rolling back if you can. The touch pad showing as a PS-2 mouse may be a clue that it is a hardware problem, or a mouse driver problem. I was surprised to hear the nouveau was giving you 3D acceleration, I didn't know it was that far yet.

Paul

Thanks for your input Paul. The 3D acceleration (provided in the package of libgl1-mesai-dri-experimental) of nouveau works pretty well for me. Using KDE it provides me an even smoother experience than NVIDIA. Only problem is this one (now) and the fact that the GPU is some 8 to 10 degrees hotter. Nouveau especialy outplays it in the 2D acceleration department for my card. I'm interested in testing, that's why I upgraded so early. I really can't figure why I have the issue with nouveau but not with Nvidia, but I do have a phantom PS/2 Mouse even when using the later one :

```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]                                                                     
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]                                                                     
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                  id=10   [slave  pointer  (2)]                                                                     
&#9116;   &#8627; PS/2 Mouse                                id=11   [slave  pointer  (2)]                                                                     
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]                                                                     
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]                                                                     
    &#8627; Video Bus                                 id=6    [slave  keyboard (3)]                                                                     
    &#8627; Power Button                              id=7    [slave  keyboard (3)]                                                                     
    &#8627; Sleep Button                              id=8    [slave  keyboard (3)]                                                                     
    &#8627; AT Translated Set 2 keyboard              id=9    [slave  keyboard (3)]                                                                     
    &#8627; Dell WMI hotkeys                          id=12   [slave  keyboard (3)]
```
This is really puzzling. Now that you mention it I did have the same list using 10.10. Maybe the ALPS inplementation of the synaptic driver is broken ? but then why would the keyboard generate random input event too ? and why does it happen so often when I'm looking at a video or listening to music ?
> **ankspo71 said:**
> Hi,
On the xorg-edgers PPA page it recommends using ppa-purge to remove their packages before attempting any upgrades. Have you already done that before upgrading? [https://launchpad.net/~xorg-edgers/+archive/ppa/](https://launchpad.net/~xorg-edgers/+archive/ppa/)  

It would be a good idea to double check to see if the repository URL is set for natty (not maverick) too. The location of the repository URL should be located in /etc/apt/sources.list.d/ , but if not, it might be located in /etc/apt/sources.list 

I'm using an Nvidia GeForce8400GS 512M PCI-E16 graphics on a Biostar/VIA P4M900-M4 motherboard, and using USB keyboard and mouse (no touchpad). The only issues I've had with nouveau drivers is that they felt too sluggish for my system, so I have been using the non-free Nvidia drivers provided through Ubuntu. The version "current"(270.30-0ubuntu3) is working good for me in Ubuntu/Kubuntu 11.04 beta. 

I had an opportunity to try the opensource "experimental" accelerated driver (nouveau?) for 11.04, and it worked pretty good, but I don't see it listed in my "additional drivers" utility anymore.  

Hope this helps you find the problem.

Thanks to ankspo71 too for your interest 
I did a clean install of 11.04 beta like I did with opensuse 11.4 (back in the beta). I'm really wondering what is the specific package that breaks things. It happens without the experimental driver (base nouveau) too.

I did notice that the name of the nouveau package changed it's now libdrm-nouveau1a instead of libdrm-nouveau1. Does someone know why ? And there is another package witch is not installed : nouveau-firmware. I though nouveau generated the firmware needed by the cards should I install it ?

---

