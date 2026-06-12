---
title: "GUI for mounting iso, bin/cue files?"
date: 2006-06-17
forum: General Help
---

### Post by rekahsoft on 2006-06-17
Does anyone know of a GUI for mounting iso, bin/cue files? some kind of program that will do it (like Alcohol 120% [deamon tools])? Thanks.

---

### Post by mlind on 2006-06-18
I dunno about gui, but you can mount .iso images using loopback device

```

sudo mkdir -p /mnt/image
sudo mount -o loop /path/to/image.iso /mnt/image
nautilus /mnt/image

```

For .cue/.bin or any other format that contain more than one datatrack
you need to either convert image to .iso (bchunk, mdf2iso, etc.) or build a [cdemu]("http://cdemu.sourceforge.net/")
kernel module that supports other formats.

---

### Post by Fred Doolie on 2006-06-18
Could some kind of wildcard be used and the iso file just drag and dropped onto the script icon? Then another "unmount" script to remove whatever was mounted on "image".  

Not a GUI but kinda closer-like.

Maybe the script file could be made the default opertion for ISO files?
---------------------
It should (guessing) be possible to make some kind GUI thing with C++ or whatever that would do that.

---

### Post by rekahsoft on 2006-06-18
It still would be nice to have a gui to do it (like alcohol 120%)...Any developers want to join me and make one? Also i have not been able to get a dvd ripper that works well and doesn't crash all the time...i have tried dvd::rip, acidrip and Thoggen. Anybody have any suggestions?

---

### Post by spockrock on 2006-06-18
how about the nautilus scripts for mounting and unmounting images, just right click on the image in nautilus and mount, and then right click and unmount.  easier then alcohol.

---

### Post by mlind on 2006-06-18
Nautilus script sounds good. Minor downside is that it would require root privileges..
I don't know if you to mount something on loopback device without them.

---

### Post by spockrock on 2006-06-18
yeah but I get that cute little popup thats all wobbly and the screen gets wobbly and then I put in my passwd and the blamo mounted.  meuh its not a bad trade off, I did loopback before and yes I hated mounting with it, but I pefer the nautilus script now to say alcohol but he advantage of alcohol was that you could open it up pick your iso and mount or burn, this you have to navigate to your image to mount and unmount.

---

### Post by rekahsoft on 2006-06-18
Yeah...it would be nice to have a alcohol 120% like program for linux...anybody want to help code one?

---

### Post by Doytch on 2006-06-18
I'm not positive about this, but maybe something like this would work.  I'd love to check to see if it works, but I don't have any iso's to check.  One thing that I know you'll have to do is edit the /etc/fstab to accomodate that virtual drive, but I don't know what stuff to put in there for that.

Maybe someone else could fix up what I messed up in it :P

**First, install zenity:**
sudo apt-get install zenity

**Create your image mount folder:**
sudo mkdir -p /mnt/image

**Create the bash script:**
sudo gedit /usr/bin/isomount

**Enter the following into the file:**
#!/bin/bash
cd *PATH TO YOUR ISO FILES*
FILE=$(zenity --title "Image Mounter" --window-icon=*PATH TO ICONS* --file-selection)
sudo mount -o loop $FILE /mnt/image

**Make the file executable:**
sudo chmod a+x /usr/bin/isomount

Now you can just make a shortcut that runs the program isomount, or run it from the terminal.
A lot of the info was gleaned from joshuapurcell's guide on making a gui for fceu(Don't have a link, I c/ped it into a file for myself)

---

### Post by Brachabre on 2006-06-18
messed

---

### Post by Brachabre on 2006-06-18
[QUOTE=Brachabre]sorry if this is a little rude and/or flaming sounding  but     you have to be kidding me if their isn't already a GUI for a program that handles something as simple as mounting a cd image iso, bin/cue what have you.    No wonder linux hasn't already replaced most windows desktop-user platforms already. All the window managers for *nix are more 'clunky' and non-ergonomic in many aspects.  I always find myself having to do some kind of detour because im so used to the ease-of-use of windows. :mad: 


Yes i am aware that until just a few years ago GUI's were hard to find for *nix based systems. but you would think something like this would be far more common for ppl's everyday tasks......alcohol was a hit before I left windows   and especially daemon tools ;)

---

### Post by roax on 2006-06-18
Try kde and kiso.

---

### Post by Fred Doolie on 2006-06-18
[QUOTE=Doytch] I don't have any iso's to check.[/QUOTE]

Won't "dd /media/cdrom whatever_name_you_want.iso" create an ISO of whatever CD is in the drive?

Here's a chance for a plug! Go to [www.puppyos.com](www.puppyos.com) and download the ISO (65 Megs I think) for the most kick-*** Linux in the world.

---

### Post by Fred Doolie on 2006-06-18
[QUOTE=roax]Try kde and kiso.[/QUOTE]

---------------
Disclaimer: I have all three desktops installed but run Gnome. The following statement may not apply to a Gnome-only system.
-------------------------------------------------------------
It installs into Gnome and shows up in the menus just fine.

It seems to just mount the iso within the app's window and not actually mount the ISO as if it were a real CDROM drive like Daemon Tools or Alcohol 120 would. Did I miss something?

---

