---
title: "ATI Driver"
date: 2009-11-22
forum: General Help
---

### Post by lewisforlife on 2009-11-22
I downgraded to Ubuntu 8.10 because I was told there was not a proprietary video driver for my card past 8.10.  Below is my video card:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

```

I have tried to install ATI Catalyst 9.11 downloaded from their website.  When I run aticonfig from the shell I get that I don't have any supported video interfaces.  Next I tried running:

```
sudo apt-get install xorg-driver-fglrx
```

Now I am running in low graphics mode, so I guess this didn't work.  How can I install the correct proprietary ATI driver for my card?

Thanks for your help,

David

---

### Post by Dakra on 2009-11-22
You need a previous release:
[http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/previous/Pages/radeon_linux.aspx)

Try the Catalyst 9.3, which worked with Ubuntu 8.10.

But I think the open source drivers should work fine. I have installed Kubuntu 9.04 with a radeon x1950 pro, not supported any more by the proprietary drivers, and the open source driver works fine with video and 3D.

---

### Post by jocko on 2009-11-22
ATi haven't made any driver for that card since 2006, so you will have to downgrade back to dapper (6.06) if you really want to use ati's proprietary driver. But the driver back in 2006 wasn't that good anyway, so the current open source driver in karmic (9.10) is probably a lot better...

FYI: ATI's support for anthing older than radeon 9500 was dropped in 2006, and anything older than radeon HD 2000 was dropped in april this year...

---

### Post by khelben1979 on 2009-11-22
I don't think it's worth downgrading. Maybe you can get a cheap video card somewhere which allows you to use the latest driver instead?

If you're asking for trouble (or good at compiling source code), you could always try to compile an older version of the x server which is compatible to the old graphics driver. That would allow you to use Karmic with the proprietary driver together with your present graphic card. Don't ask me for support though.. :-\"

---

### Post by SeePU on 2009-11-27
The only option is to to use an older distribution or only use 2D.  I've tested it but with a laptop with the RV250 card (which is a Radeon 9000) mobility chip.

The official requirement is that you have to use the open source radeon driver (or radeonhd as an alternative).  But, it only works for 2D in Karmic, 9.10 - in my experience.  

It can be used in Ubuntu 9.04 with either 2D or 3D.  But, NOT 9.10.  Karmic crashes or locks up, whatever you want to call it.  I think there should be a sticky about this and if there is any solution that can work at a universal level, it should be posted.

I've read conflicting reports and tried various suggestions and instructions to no avail.

Karmic crashes or locks up when booting the LiveCD.  As we know, there is no xorg.conf file no more in 9.10.  So, I've tried various settings in creating an xorg.conf file and the best result was a flickering screen that wouldn't 'repaint' correctly so the newly configured file was of no use.  If you can't see the screen and it's all corrupted, it's of no use.

With the default setup (that is, no xorg file), Firefox and Synaptic were tried.  On separate occasions, though, since the computer would totally lock up after opening the application.  

Why doesn't anyone care about this?  Either state that 3D effects aren't usable or report a solution, please?

I know I can boot up a Live CD of Mandriva 2010 and 3D Desktop Effects work fine so it is doable with the right configuration setup.

---

