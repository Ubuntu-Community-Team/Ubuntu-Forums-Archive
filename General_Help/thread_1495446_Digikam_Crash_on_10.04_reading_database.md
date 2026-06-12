---
title: "Digikam Crash on 10.04 reading database"
date: 2010-05-28
forum: General Help
---

### Post by FerBatista on 2010-05-28
I can't get digikam to work at all on 10.04, it never pass from reading my pictures folder, usually stops in any folder and crashes after sometime.

Here's what shows at the terminal:
> 
Warning: Exif IFD NikonPreview not encoded
Warning: Exif tag Exif.NikonPreview.JPEGInterchangeFormatLength not encoded
Warning: Exif IFD NikonPreview not encoded
Warning: Exif tag Exif.NikonPreview.JPEGInterchangeFormatLength not encoded
Warning: Exif IFD NikonPreview not encoded
<unknown>: Fatal IO error 9 (Bad file descriptor) on X server :0.0.
KCrash: Application 'digikam' crashing...
sock_file=/home/fernando/.kde/socket-fernando-desktop/kdeinit4__0
kdeinit4: preparing to launch /usr/lib/kde4/libexec/drkonqi

[1]+  Stopped                 digikam
fernando@fernando-desktop:~$ 

The warning lines are repeated over and over again, so I just pasted the last ones.

I've searched this forums and google about it but found no one with the exact similar issue. Can anyone help me out? Digikam always worked fine for my on my older installations.

If I cancel the database reading, digikam will work as it should but obviously without all the photos on my folder.

I'd really appreciate the help on this.

---

### Post by dino99 on 2010-05-28
maybe some help there:

[https://launchpad.net/ubuntu/+ppas?name_filter=digikam](https://launchpad.net/ubuntu/+ppas?name_filter=digikam)

[http://ubuntuforums.org/showthread.php?t=1366174](http://ubuntuforums.org/showthread.php?t=1366174)

---

