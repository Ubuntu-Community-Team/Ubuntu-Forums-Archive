---
title: "how to enable s-video on laptop"
date: 2006-05-25
forum: General Help
---

### Post by tomslopez on 2006-05-25
I have a HP Pavilion ze5270 laptop, and my video card is one of these, I honestly don't know which one is it:
```
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device cbb2 (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 340M
```
And I would like to connect my computer to the TV using an S-Video cable, but I was told that I needed to enable something and I don't know what that is, if anyone could help me that would be great.
Thanks.

---

### Post by brettr on 2006-05-25
I have been searching for a while on how to do this.. As far as i have been able to find you pretty much have to edit your xorg.conf and restart the x server.

```
sudo gedit /etc/X11/xorg.conf
```
of course back it up first

here is the relevant section notice the Option "Clone... and MonitorLayout
```

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option          "MonitorLayout" "TV,LFP"
        Option          "Clone" "true"
EndSection
```


Anyways search around on this forum and on google and you can find some other configurations. 

Also check here: [NvidiaTvout]("https://wiki.ubuntu.com/NvidiaTVOut?highlight=%28Svideo%29")

---

