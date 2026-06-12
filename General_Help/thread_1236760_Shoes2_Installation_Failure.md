---
title: "Shoes2 Installation Failure"
date: 2009-08-10
forum: General Help
---

### Post by Sprawn! on 2009-08-10
I am trying to install the fun, little toolkit for Ruby called "Shoes" available at shoooes.net. I downloaded the shoes2.run file, changed it to executable, and ran the installer. The program initializes... the splash screen comes up. But in the installer window, I get several error messages:

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so

And the program does not install. It is possible to install the program using add/remove or apt-get, but the version installed is 1.0 and many features are not available. Version 3.0 is in the "daily builds" prototype stage, and 2.0 is stable (apparently). I can't find an alternative package repository so it installs smoothly. And I am rather new to this, so if I am posting in the wrong forum or using improper ettiquette, I'd not mind hearing about it. Thanks!

---

### Post by bodyharvester on 2009-08-10
> **Sprawn! said:**
> And the program does not install. It is possible to install the program using add/remove or apt-get, but the version installed is 1.0 and many features are not available. Version 3.0 is in the "daily builds" prototype stage, and 2.0 is stable (apparently).

thanks for adding the error thingymajig, you ran the executable with WINE right? if its a linux thing natively you shouldnt need to make it an executable.

i cant remember but is the run file an executable script file?

why not try 2.0 if its stable?

-joe

---

### Post by Sprawn! on 2009-08-10
> **bodyharvester said:**
> thanks for adding the error thingymajig, you ran the executable with WINE right? if its a linux thing natively you shouldnt need to make it an executable.

i cant remember but is the run file an executable script file?

why not try 2.0 if its stable?

-joe

Thanks for the reply Joe!

Do the errors mean anything to you... the "ELFCLASS64" stuff?

2.0 is the version I tried to install with Shoes2.run. I merely mentioned that I made it executable so that no one would post and say, "you need to find the file and 'chmod -777 shoes2.run' then ./shoes2.run" I believe it was executable as it came. I certainly did not install it with WINE, it was the Linux file. I don't even have WINE installed. Shoes runs under Linux, it's just a Ruby Toolkit, really...

- Ron

---

### Post by bodyharvester on 2009-08-10
i have no idea what those errors mean:), did you try installing it the same way a second time? you may get a different result, or a different error message to think about.

heres another post i just found after searching for "ELFCLASS64" [http://ubuntuforums.org/showthread.php?t=1235148&highlight=elfclass64](http://ubuntuforums.org/showthread.php?t=1235148&highlight=elfclass64)

i think this error may be an installation thing not just a specific program

---

### Post by Sprawn! on 2009-08-10
I've tried *everything!* I turned it on and off. I cleaned the gunk out of the mouse. I even vacuumed.

I want to go to this ELFCLASS.

What happens is the program starts just as if it were properly installed, but then when the installation window closes, the program is not installed...

$ ./shoes2.run
Installing..........

and then the program works... ONCE. After I close the shoes window.
$ shoes
The program 'Shoes' is not currently installed. You can install it by typing:
sudo apt-get install shoes

BUT... if I install it, it uses ubuntu's package tracker and I get version 1.0 with missing features. If I try to install 2.0 in top of 1.0, it still doesn't work.

---

### Post by bodyharvester on 2009-08-11
i guess your stuck wwith v1.0 for now, until 3.0 is better

try reposting in updates section, someone with specialised knowledge of how they work may be able to help there

good luck

EDIT: sorry about the time it took to reply, i was sleeping :)

---

### Post by Sprawn! on 2009-08-11
I will retry in that section. Thanks, bodyharvester.

I have tried the "daily build" style .run files for 2.0 and 3.0beta versions. More errors of the same type.

---

