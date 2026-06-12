---
title: "Front panel cant be detected"
date: 2011-01-13
forum: General Help
---

### Post by Mortis19 on 2011-01-13
Hello, Im having a trouble with ubuntu 10.10. I have connected in the mobo panel (in the green hole) my speakers and I also have a front panel connected to my mobo, where I connect my headset (mic and headphones). Although in Windows the headset works perfectly, in ubuntu my back panel works perfectly (I have sound from my speakers), but ubuntu dont detect my front panel. In sound settings, in input panel, I have 3 choices (microphone 1, 2 and line in) but none of them works. Also, in hardware tab, it shows me 2 devices, the hdmi output from my graphics card (dont care about it) and "Internal Audio". where analog stereo duplex is enabled (I tried all the others but they dont work). I tried to make it with alsa mixer and I upped the volume in all microphones but still nothing...

---

### Post by Mortis19 on 2011-01-18
Anyone??

---

### Post by Mark Phelps on 2011-01-18
I think the lack of response should tell you something ... that no one knows how to solve your problem.

I presume that the front panel audio has a cable and connector that plugs into your motherboard.  That being the case, it's the motherboard drivers that then "see" the hardware.

In MS Windows, you nearly always manually install drivers for the motherboard; in Linux, you never do.  Why? Because the drivers are bound to the kernel and are installed automatically when initial setup is done.

Which is another way of saying that if the proper driver was not installed, apart from manually rebuilding the kernel, there's little you can do to remedy it.

---

### Post by Mortis19 on 2011-01-19
I think I found the problem. In windows, to get the front panel work, in the driver software (in my case VIA HD Audio Deck) I had to deselect "Enable front panel detection". I had to do the same think with my old Gigabyte Mobo in the Realtek driver. I think this solution is also written in the manual of some mobos, like ASUS and Gigabyte. But how can I do this at ubuntu?

---

### Post by Mortis19 on 2011-01-22
Anyone knowing how to hande this problem?

---

### Post by Mortis19 on 2011-01-28
Nothing? :guitar:

---

### Post by Mark Phelps on 2011-01-28
NO -- nothing.  

As I tried to say last time, this is handled by the device drivers.  Obviously, the MS Windows drivers provided you an option that allowed for utilization of the front panel jacks. This is often handled in the Audio software itself by providing an options panel.

If you do not see these options in Ubuntu, it means the existing drivers don't support this.

---

### Post by mharrison on 2011-01-28
I am not pretending I know a solution, just trying to help:

Give this a read:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=audio+jack](http://ubuntuforums.org/showthread.php?t=205449&highlight=audio+jack)

---

