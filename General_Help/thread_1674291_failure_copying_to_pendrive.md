---
title: "failure copying to pendrive"
date: 2011-01-23
forum: General Help
---

### Post by HotForLinux on 2011-01-23
Today, I simply wanted to copy a 4.4GB (4723265536 bytes) file from a NTFS partition (with 497MB free spacve) mounted in an Ubuntu Hardy system to a Windos user's pendrive with I don't know what filesystem (probably fat16 or fat32) using Nautilus.

Two times the process failed when exactly 4GB had already been copied. Ubuntu displayed a message saying that it couldn't finish ... bla, bla, bla ... "File too long" and also not enough space.

Before that, in Windos, I made enough space in the pendrive for the new file, and double checked that in windoze, first, and in Ubuntu, then.. There were around 4.8GB of free space and then, after the partial copy & failure, Nautilus showed 8MB free.


Does any one have an idea of what could have happened?
Can there be a 4GB limitation somewhere?

---

### Post by TeoBigusGeekus on 2011-01-23
FAT32 can only handle up to 4gb in a file.
Make a rar from the file splitting it into two or more parts.

---

### Post by HotForLinux on 2011-01-23
> **TeoBigusGeekus said:**
> FAT32 can only handle up to 4gb in a file.
Make a rar from the file splitting it into two or more parts.

Yeah.. I see... I am realizing that. Oh my!.. Never had a problem with that so I had forgotten about that limitation. Still exists?!

Why winrar? What would be an easy and fast way to split and join in each system?
(In Ubuntu I would join with **cat** and split with ... **split**?)

**I**s there another "good" solution, other than slicing the files?, like another format which is not too slow and compatible with new Windos and usual Ubuntu installs?

---

### Post by TeoBigusGeekus on 2011-01-23
> **HotForLinux said:**
> Yeah.. I see... I am realizing that. Oh my!.. Never had a problem with that so I had forgotten about that limitation. Still exists?!

Why winrar?

Is there another "good" solution, other than slicing the files?, like another format which is not too slow and compatible with new Windos and usual Ubuntu installs?
ntfs?

---

### Post by HotForLinux on 2011-01-23
> **TeoBigusGeekus said:**
> ntfs?

I know it is slow, but I will suggest to try it to this person.
What about splitting and joining? Could you explain me very shortly how would you do it fast and easy in each system?

---

### Post by TeoBigusGeekus on 2011-01-23
[http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html]("http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html")

---

### Post by HotForLinux on 2011-01-23
> **TeoBigusGeekus said:**
> [http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html]("http://www.ubuntu-unleashed.com/2008/05/howto-create-split-rar-files-in-ubuntu.html")

Thanks!. That sounds good for Linux's side. We'll have to try it. I hope is not too slow.


YESSSS!!!...Please make Autocad Civil 3d and Archicad work on Linux!, Please make Autocad Civil 3d and Archicad work on Linux!, Please make Autocad Civil 3d and Archicad work on Linux!,....

---

### Post by TeoBigusGeekus on 2011-01-23
> **HotForLinux said:**
> YESSSS!!!...Please make Autocad Civil 3d and Archicad work on Linux!, Please make Autocad Civil 3d and Archicad work on Linux!, Please make Autocad Civil 3d and Archicad work on Linux!,....

Amen...

---

### Post by HotForLinux on 2011-01-23
> **TeoBigusGeekus said:**
> Amen...
ok. Thanks!

---

### Post by HotForLinux on 2011-01-24
Hi! I used rar (in the command line) to slice that 4.4GB file in 3GB chunks with the option "-m3g" **_not described in the man page_**, and save them directly in the pendrive. It's easy and everything went fine until the end when I had problems unmounting the volume. I checked that the process had finished, then I synced and closed all nautilus windows showing its contents but the system continued complaining. I had to unmount with sudo (why!?). I wonder what can a non administrator do in these cases?

I don't know if Hardy Heron is still receiving support but maybe someone should check if this is happening in the new releases.

---

