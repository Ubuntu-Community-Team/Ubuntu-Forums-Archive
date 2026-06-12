---
title: "Howto: install ksensors in maverick"
date: 2010-10-30
forum: General Help
---

### Post by Yako no Kai on 2010-10-30
Since the virtual machine test passed, I went on to test maverick on real hardware (except I'm avoiding the kernel upgrade because of [http://ubuntuforums.org/showthread.php?t=1592245](http://ubuntuforums.org/showthread.php?t=1592245)). And the first place I found hardware support failing is where I never expected: hardware monitoring.

ksensors, the best KDE hardware monitor (of an admittedly small number of candidates) does not have a package for maverick and no replacements have been provided.  When you add in the fact that the Hardware Temperature plasmoid is now broken (it shows no available temperatures), it means that KDE no longer provides a means of easily seeing temperatures of fan speeds.  Only ksysguard (clunky, no alarms), xsensors (simple, ugly, no alarms), and cat'ing the values from the relevant area in /sys/devices (...).

When I found this out, my first thought was my god, what a bunch of idiots.  How could anyone be so shortsighted when building an operating system?

My opinion has not changed, but luckily there is a workaround.  The lucid package for ksensors still works and there is nothing that conflicts with anything in maverick.  It looks bad in the system tray if desktop effects are on, because it is not transparent like the panel is, but it works fine, and that's all I need.  

For me, I don't even notice because I rarely see desktop effects after the first week (in karmic they add 20-25% CPU to vdpau decoding).  And you can always hide the icon (like I do with the kpackagekit icon; that thing keeps coming back like a bad rash if you have packages locked).

So here is the actual howto part of this howto, which was mostly rambling (sorry):

```

1. Go to http://ns2.canonical.com/lucid/kde/ksensors
2. Download the deb for ksensors_0.7.3-18ubuntu2 that fits your architecture.
3. Install the deb file (gdebi, dpkg -i, whatever).

```

I'm still on the lookout for replacements.  [http://gitorious.org/kwatchman](http://gitorious.org/kwatchman) intends to do just that.  It doesn't have alarms yet, but perhaps it will eventually and will be included in the repository.  There are probably others evading my google-fu.

Next up, testing vdpau. Here's hoping.

---

