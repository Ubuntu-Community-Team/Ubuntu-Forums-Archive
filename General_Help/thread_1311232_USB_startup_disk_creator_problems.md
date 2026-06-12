---
title: "USB startup disk creator problems"
date: 2009-11-02
forum: General Help
---

### Post by tcpa41 on 2009-11-02
Hello guys,today,while trying to reinstall 9.10 i encountered a strange problem. I downloaded the official image from the net and using the usb startup disk creator burned it.All went ok,no errors were reported during the burning process. Then i restarted my pc and went to bios to edit my bootsequence,again, as always i set the first boot device to my usb,saved the setting and restarted my compo... Gues what,it skipped the usb boot and went straigt to my HDD,grub started booting and the only odd thing i saw in the top left corner of the screen there was written "multiple active partitions" but it passed away as grub continued to load.
Guys,how do i fix this problem,bcus previously boot from usb worked ok on my compo.USB key is the same,nothing changed from hardware part.

---

### Post by Giblet5 on 2009-11-02
Either your stick did NOT burn OK, or your PC can't boot from a USB stick.

Most BIOS understands special key sequences at POST (self tests) for presenting an explicit boot menu.

On this box, it's F8. On the one next to it, it's F12, as is my laptop.

If you explicitly boot from the USB stick (it must be in the USB port **during** system reset!), then the image didn't burn as you anticipated. In that case, go to [pendrivelinux]("http://www.pendrivelinux.com/") and use their procedure for creating a stick (they are experts).

---

### Post by Carlie Powell on 2009-11-02
I have the same problem after loading KK the USB stick stopped booting...=\

---

### Post by Mighty_Joe on 2009-11-02
> I have the same problem after loading KK the USB stick stopped booting...=\ 

Does [this]("http://ubuntuforums.org/showthread.php?t=1311097") sound like what happened?  Maybe one of you guys who's experiencing this problem can [open up a bug]("https://help.ubuntu.com/community/ReportingBugs").

---

### Post by tcpa41 on 2009-11-02
Nope,thats not the problem I'm experiencing.Mine problem is that computer skips booting from usb although in bios it's set as first boot device and i also am sure that a month ago booting from usb worked ok. The only odd thing is the Multiple active partitions text on the top left corner of the screen along with grub loading text on second line,but it vanishes after grub is loaded up

---

### Post by Mighty_Joe on 2009-11-03
> **tcpa41 said:**
> Nope,thats not the problem I'm experiencing.

Sorry. I was speaking to Carlie Powell, whom I quoted ;)

---

