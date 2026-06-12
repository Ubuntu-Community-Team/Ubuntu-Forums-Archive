---
title: "the infamous disappearing gnome panel"
date: 2010-09-01
forum: General Help
---

### Post by mamboze on 2010-09-01
What is it with the gnome panel that causes its inexplicable disappearance? Is it a bug? I've been using Ubuntu since 7.04 and I think this panel disappearance phenomenon has become more frequent in recent distros. Since I installed 10.04 nearly 2 months ago, I've had to rebuild gnome twice, the last time today. 

I've looked at some (maybe most) of the forum posts on this issue and there doesn't seem to be any clear reason why the panel drops out as it does, not that I can see anyhow. 

Ubuntu developers, please don't get me wrong. I respect your work and will certainly stick with Ubuntu, no doubt about that. But the evaporation of the panel is a niggling issue, having to restore and then setup the panel with the file browser and all the rest. 

Any suggestions or comments would be much appreciated.

---

### Post by philinux on 2010-09-01
> **mamboze said:**
> What is it with the gnome panel that causes its inexplicable disappearance? Is it a bug? I've been using Ubuntu since 7.04 and I think this panel disappearance phenomenon has become more frequent in recent distros. Since I installed 10.04 nearly 2 months ago, I've had to rebuild gnome twice, the last time today. 

I've looked at some (maybe most) of the forum posts on this issue and there doesn't seem to be any clear reason why the panel drops out as it does, not that I can see anyhow. 

Ubuntu developers, please don't get me wrong. I respect your work and will certainly stick with Ubuntu, no doubt about that. But the evaporation of the panel is a niggling issue, having to restore and then setup the panel with the file browser and all the rest. 

Any suggestions or comments would be much appreciated.

Never encountered this at all in my 3 years with ubuntu. Have you customised something to create this instability.

I have compiz running on a nVidia 8600gt.

Try resetting the panels back to their default.

```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by mamboze on 2010-09-01
Hi philinux,

My system has not changed that much over the time I've been using Ubuntu. The CPU is a Pentium 4 2.80Gb. The video card has a nvidia FX 5200 processor with 128MB of memory (maybe a bit marginal??). I've increased the system RAM to 2.5Gb and upgraded to a 500Gb hard disk. I don't think any of these changes are relevant. 

On the software side, I'm running gnome without compiz, a pretty vanilla setup really, since the video card is by no means cutting edge. The only customizing I've done is add various Applications menus to the panel and 2 file browsers. I thought perhaps the file browser might be the cause of the instability, but I have no evidence. It is a useful little applet but I can do without it.

Following your advice, I reset gnome to its default values. I guess I'll run it like this for a while and see what happens. One question, are there any log files or other sources which might give a clue to what's happening?

Thanks for your help.

---

### Post by Ginsu543 on 2010-09-01
Like philinux, I too have never had a gnome panel disappear on me except for one occasion: when I changed the setting for the panel to autohide, turned off animation, and set all delays to 0. This setting used to work just fine until Karmic, but when I upgraded to Lucid my top panel disappeared. The problem disappeared though when I turned animation back on.

---

### Post by hangfire on 2010-09-01
> **mamboze said:**
> My system has not changed that much over the time I've been using Ubuntu. The CPU is a Pentium 4 2.80Gb. The video card has a nvidia FX 5200 processor with 128MB of memory (maybe a bit marginal??). I've increased the system RAM to 2.5Gb and upgraded to a 500Gb hard disk. I don't think any of these changes are relevant.

Is your Nvidia card AGP or PCIe (or PCI)? I have had so many problems with AGP support versus KMS in 9.10 and 10.04 that I was forced to upgrade to PCIe.

-HF

---

### Post by mamboze on 2010-09-01
@hangfire

My video card is AGP. I had no problems I can remember with nvidia drivers until Ubuntu 9.10 Karmic. The main issue with Karmic for me was getting the settings in the xorg.conf file right - it took a while! Anyhow, Lucid installed perfectly, the video driver included. 

At the moment, I'm focusing on whether the file browser app is at fault. I've only been using it recently.

I had thought about trying Kubuntu as an alternative GUI, but let's see. 

Thanx

---

### Post by Cypress421 on 2010-09-01
Never experienced this. What drivers are you running? Proprietary or built-in?

---

### Post by mamboze on 2010-09-02
I'm using the proprietary nvidia driver, 173.14.22, from the repositories. I've just checked the nvidia linux driver site and version 173.14.27 is available.

Has anyone had any experience with this later driver? Does it work OK with Lucid? It is, of course, generally preferable to use the most recent drivers. I wonder tho whether the panel problem is a driver issue.

Thanx guys for your help

---

### Post by Cypress421 on 2010-09-02
Can you try the built in drivers to see if you can replicate the issue?

---

### Post by mamboze on 2010-09-02
@Cypress421

When you say 'built in drivers', you're referring to the driver available from the nvidia site, 173.14.27, right?

---

### Post by Cypress421 on 2010-09-02
> **mamboze said:**
> @Cypress421

When you say 'built in drivers', you're referring to the driver available from the nvidia site, 173.14.27, right?

I mean disabling all other drivers except those that come built into Ubuntu, so in Hardware Drivers, disable anything proprietary and reboot, otherwise you can try compiling the latest Nvidia drivers yourself.

---

