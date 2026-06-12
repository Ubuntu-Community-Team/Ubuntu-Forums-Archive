---
title: "Usplash difficulties"
date: 2006-06-28
forum: General Help
---

### Post by Kensey on 2006-06-28
I can't get usplash to display custom artwork -- I just get the dreaded black screen no matter what I do.  I followed SilentChaos' HOWTO that he posted for Breezy, and tried the Usplash Customization page on the Ubuntu Wiki as well -- neither worked.  Stock Ubuntu/Kubuntu art works fine.

Has anyone successfully created custom usplash art from scratch under Dapper?  If so, what version of gcc and libbogl-dev do you have?  Is this a known issue with Usplash under Dapper?

---

### Post by mbeierl on 2006-06-28
I have created my own bootsplashes quite successfully.  I've attached one that my kids rather enjoy.  I borrowed it from somewhere and added some Madagascar penguins to it :)

I have:
gcc                                    4.0.3-1
libbogl-dev                           0.1.18-1.4ubuntu2

Are you using an initrd?

---

### Post by Kensey on 2006-06-28
I must be using initrd; the stock screens work when I replace my own with them.

I have gcc-4.0 4.0.3-1ubuntu5, but interestingly I don't have the "gcc" dependency package installed.  I wonder if there's something missing because of that.  I have the same libbogl-dev as you.

I'll try installing the gcc dependency package and we'll see what that does for me.

---

### Post by Kensey on 2006-06-28
Nope, no dice.  Still a black screen on boot, and on virtual terminal 1 I get this message:

[17179570.376000] PCI: Failed to allocate I/O resource #7:1000@10000 for 0000:00:1e.0

followed by a normal login prompt.  Everything seems to work normally apart from that error.

---

### Post by mbeierl on 2006-06-28
Funny I get the same message.  Are you running a dell d610? :)

Are you using the make-usplash.sh script from (I think) one of the howtos?  I've attached it here again just in case.

Also, what does your grub boot line look like (ie: splash vga=xxx)

---

### Post by Kensey on 2006-06-28
Sure am :)  I don't get it with the stock art; maybe the stock art covers it up.  There's not a lot out there about it, but it seems to have something to do with loading a RAM image off disk on the D610 (I saw it referenced in the context of resuming from suspend-to-RAM, and showing up just after initrd decompresses).

I hadn't seen that script before, but I was running the commands in it by hand so it comes out the same anyway.  My menu.lst default boot option line looks like this:

# defoptions=quiet splash vga=769

This works fine with stock art.

Grasping at a couple of straws here, I generally boot kernel version 2.6.15-25-686, how about you?

---

### Post by mbeierl on 2006-06-28
I've compiled my own kernel because the stock kernel's suspend/hibernate functionality doesn't quite work for me:  see I've got this weird error with my cdrom drive where it goes into some funky read state and hangs.  The stock kernel can't hibernate at that point, but the Software Suspend2 patch can, so I compile my own with that.

So I'm using 2.6.17 with Con Kolivas' performance patch and Software Suspend2.

But my usplash works with the stock kernel...  Did you try the image attached?

---

### Post by Kensey on 2006-06-28
Just tried it -- no luck.  Earlier I tried creating a new PNG that was just a flat green 640x400 rectangle and that failed too.

At this point I think it's one of two things:

* I'm creating my PNGs in an incorrect way somehow.  I've been letting GIMP pick the palette with a 16-color restriction.  Do the actual colors in the palette matter somehow?

* Somehow a bug on my system is preventing the C code or object code from being generated correctly.

So I guess the next thing is to try comparing C code.  I'm attaching my flat green PNG -- can you attach the C code that you get with pngtobogl so I can compare it to what I get?

[IMG]http://vento.tomsvw.com/~kensey/pics/usplash-basic.png[/IMG]

---

### Post by mbeierl on 2006-06-28
I'll give it a try tomorrow...

---

### Post by Kensey on 2006-06-29
OK, solved it, and it was right in front of me the whole time: you **have** to name the original PNG file "ubuntu-artwork.png" or it won't work.  This should probably be emphasized in the USplashCustomizationHowto.

Thanks for puttin' up with my boneheadedness :rolleyes:

---

### Post by Kensey on 2006-06-29
...Make that "usplash-artwork.png", of course.

---

### Post by mbeierl on 2006-06-29
Excellent.  I did try yours and it did work, btw!  It showed the green field background and the progress bar was yellow with white.  The text was the same color as the background, though, so that didn't show up.

Somewhere there should be a repository of usplashes for people to browse.  I couldn't find one with significant content, though.

---

### Post by Kensey on 2006-06-29
You know, I was thinking the same thing.  Given that we're talking 640x400/480 and 16 colors, I could see things based on old video game art as one obvious source of art.  I was also thinking last night that shots based on APOD photos would be great too, but not every APOD would work well as a splash.

---

### Post by adverseyaw on 2006-08-25
I am having a problem doing this also.  When I reconfigure with dpkg I get this output:
```

Reconfiguring kernel...
Not touching initrd symlinks since we are being reinstalled (2.6.15-23.39)
Not updating image symbolic links since we are being updated (2.6.15-23.39)
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
**Searching for splash image ... *none found, skipping* ...**[Emphasis added]
Found kernel: /boot/vmlinuz-2.6.15-23-686
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Also I changed 
[FONT="Courier New"]dpkg-reconfigure *kernel*-image-$(uname -r)[/FONT]
to read
[FONT="Courier New"]dpkg-reconfigure **linux**-image-$(uname -r)[/FONT]
Is there something else I should be doing?
Thanks
AdverseYaw

[COLOR="Red"][EDIT: Ok, I see now that it does work.  Is there a way to move the progress bar down 10 pixels or so?][/COLOR]

---

### Post by Kensey on 2006-09-11
Not that I know of -- as far as I know all of the elements are fixed in place.

---

