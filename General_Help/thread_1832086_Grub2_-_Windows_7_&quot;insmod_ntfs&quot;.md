---
title: "Grub2 - Windows 7: &quot;insmod ntfs&quot;"
date: 2011-08-24
forum: General Help
---

### Post by Intrepid Ibex on 2011-08-24
Is there a specific meaning for this? Grub2 reads my Windows 7's NTFS partition just fine anyway:

```
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
[B]	insmod part_msdos
	insmod ntfs[/B]
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root 3C64FEFF64FEBAAA
	chainloader +1
}
```

Or is the "ntfs" module auto-loaded?

Also what are the classes for ("--class windows/os")?

---

### Post by Intrepid Ibex on 2011-08-29
Finally found the official Grub2 documentation: [[COLOR="DarkSlateGray"]_http://www.gnu.org/software/grub/manual/grub.html[/COLOR]_]("http://www.gnu.org/software/grub/manual/grub.html")

Here's what it has to say about **classes**:

> **[[COLOR="DarkSlateGray"]6.2.6 Boot Menu[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#Theme-file-format")**

The boot menu where GRUB displays the menu entries from the “grub.cfg” file. It is a list of items, where each item has a title and an optional icon. The icon is selected based on the *classes* specified for the menu entry. If there is a PNG file named “myclass.png” in the “grub/themes/icons” directory, it will be displayed for items which have the class *myclass*. The boot menu can be customized in several ways, such as the font and color used for the menu entry title, and by specifying styled boxes for the menu itself and for the selected item highlight.

> **[[COLOR="DarkSlateGray"]14.1.1 menuentry[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#menuentry")**

[...]

[INDENT]The --class option may be used any number of times to group menu entries into classes. Menu themes may display different classes using different styles.[/INDENT]


And here's about the **insmod** thing:

> **[[COLOR="DarkSlateGray"]4.1.2 Chain-loading an OS[/COLOR]]("http://www.gnu.org/software/grub/manual/grub.html#Loading-an-operating-system-directly")**

[...]It is normally also necessary to load some GRUB modules and set the appropriate root device.[...]

menuentry "Windows" {
	insmod chain
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}

So what I would take from this is that the modules are simply auto-inserted.

---

