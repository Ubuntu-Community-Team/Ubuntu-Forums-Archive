---
title: "ipod help: iTunesDB does not exist. sort of."
date: 2006-02-28
forum: General Help
---

### Post by iand675@gmail.com on 2006-02-28
I just got my ipod working a little while ago in windows, and got it mountable in linux, but gtkpod gives me the following error: 

'mnt/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.

whats wrong with my ipod? i navigated to the directory that it lists, and iTunesDB is in that file, so i don't understand whats wrong. Please help me!

---

### Post by Edward The Bonobo on 2006-03-01
Yup!  Been there.  The easiest way will be to go to a Windows machine first and load up at least one song via iTunes.  After that, gtkpod should work.

First, though...I'm having problems at the moment with gtkpod.  I installed the version in Breezy (v0.94), set up the iPod as above, and it worked...after a fashion.  However - the other day I upgraded to gtkpod v0.99.2, and now I'm getting the same error that you had again.

My guess would be to sensible make sure that you have the latest version before you start.  To get that:

1) Go to this forum: [http://www.ubuntuforums.org/showthread.php?t=104937&highlight=libgpod](http://www.ubuntuforums.org/showthread.php?t=104937&highlight=libgpod) scroll down to post #9 and download the latest gtkpod and libgpod from the links.

2) When I did it, they arrived as .htm.  Just change that to .deb

3) In terminal:
```

sudo dpkg -i whatever_the_name_of_the_gtkpod_file_is.deb
sudo dpkg -i whatever_the_name_of_the_libgpod_file_is.deb

```

4) For me, in Xubuntu, this deleted gtkpod from my Applications window, so I have to 
```

run gtkpod

```
until I can figure out how to edit the menu (which will be easy enough, but I've been more concerned with fixing my iPod first)

Good luck!

---

### Post by Edward The Bonobo on 2006-03-01
Correction...

Not 
```

run gtkpod

```
just
```

gtkpod

```

(or open up a 'Run' dialogue and type 'gtkpod')

---

