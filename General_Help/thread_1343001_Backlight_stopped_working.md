---
title: "Backlight stopped working"
date: 2009-12-01
forum: General Help
---

### Post by ragein on 2009-12-01
I have come across an interesting problem in that the night before last I went to sleep with my screen set to 15% backlight using xbacklight, turned off the machine from the power button when I went to work and once I got home my backlight controls don't work anymore.

I'm running Karmic on a macbook 2,1 dual booting osx (adding all the info I can think of incase it helps).

I normally use xbacklight to set my screen as I haven't got round to making my function keys work in ratpoison yet, when I do this command:-

xbacklight -set 15%

I get

No outputs have backlight property

When I booted into gnome to see if it was just ratpoison my function keys don't work either (they were working before although they don't on first install with the macbook).

Hope thats enough info :) any help would be great or I'm stuck with osx for my audiobook bed time story ;p

---

### Post by ragein on 2009-12-01
Oh whilst I think about it before the re-boot in I was learning how to mount drives from a command, this did lead to me playing with my fstab and mstab files but I think I put them back to the original, if this could be the cause then I can post them although I don't think a screen would be mounted.

---

### Post by ragein on 2009-12-02
I have done quite abit of google'in about this and not got very far, I did find out about the below files don't know if their contents will be of any help or not but here goes.

cani@macintux:/proc/acpi/video/GFX0/LCD$ ls
brightness  EDID  info  state
cani@macintux:/proc/acpi/video/GFX0/LCD$ cat brightness
<not supported>
cani@macintux:/proc/acpi/video/GFX0/LCD$ cat EDID
<not supported>
cani@macintux:/proc/acpi/video/GFX0/LCD$ cat info
device_id:    0x0400
type:         LCD
known by bios: yes
cani@macintux:/proc/acpi/video/GFX0/LCD$ cat state
state:     0x1f
query:     0x01

---

