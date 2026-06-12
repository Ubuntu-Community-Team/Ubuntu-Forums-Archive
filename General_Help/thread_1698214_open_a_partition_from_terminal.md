---
title: "open a partition from terminal"
date: 2011-03-01
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-03-01
i am trying to use a command to open a partition or disc from the top... like open up external drive, and not have to be externaldrive/videos or whatever. the reason being is to use in cairo dock, i have tried to drag n drop like i am able to with regular folders, but no good. i seen the option to run a command, and figured i would try it that way. 

i have the partitions and discs i want to access mounted. they are:
External Drive (/dev/sdc1)
Storage          (/dev/sdb1)
Windows         (/dev/sda2)

i tried to open them in terminal, /media/storage: no such file or directory; 
/dev/sdc1: Permission denied; 
open /media/storage  or   /dev/sdc1   Couldn't get a file descriptor referring to the console;
se7en@PC:~$ nautilus /media/storage   or   nautilus /dev/sdc1
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x1d06480)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-input-feedback-sounds' of type `gboolean' from rc file value "((GString*) 0x1d06320)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-button-images' of type `gboolean' from rc file value "((GString*) 0x1d06620)" of type `gboolean'
se7en@PC:~$ nautilus /dev/sdc1
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x2242480)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-input-feedback-sounds' of type `gboolean' from rc file value "((GString*) 0x2242320)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-button-images' of type `gboolean' from rc file value "((GString*) 0x2242620)" of type `gboolean'

along with a pop-up saying 'the location is not a folder'

if someone could give me a good push in the right direction, i would appreciate it. hopefully with 'External Drive' because i heard somewhere i have to do something special for a location that has a space in it. something like '/External\ Drive' maybe?

thanks a bunch guys...

---

### Post by Krytarik on 2011-03-02
Check with the command
```
cat /etc/mtab
```
where the devices are actually mounted, should be indeed a directory in "/media". If there is indeed a space in the name, the use of "External Drive" or 'External Drive' will be sufficient.

And I assume, you could also drag&drop those folders into your dock.

Greetings.

---

