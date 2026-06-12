---
title: "Fabulously high success rate at breaking things!"
date: 2006-04-25
forum: General Help
---

### Post by Mookawaka on 2006-04-25
It is quite nice that Linux based systems are nearly immune to corruption from external sources, but I have discovered that I am incredibly proficient at breaking it myself. YAY!
I am definitely out of my depth on this one and now that I finally have Ubuntu set up and customized just the way I like, I have run into a frightful error.
err . . . Pardon my rambling . . .

Upon booting everything seems to be running fine until I arrive at:
"checking root file system . . ."

After some CPU cycling I am dumped into a console and my robot overlord continues working hard while spitting out this long list attempting to explain an error with the root file system.  And I quote:

/ contains a file system with errors, check forced.

[429470725.020000] buffer i/o error on device hda7, logical block 65931
(following is a reasonably long list nearly identical to this line apart from the numbers)

Error reading block 65924 (Attempt to read block from filesystem resulted in short read) while doing inode scan.

/: unexpected inconsitency; run fsck manually. (i.e., without -a or -p options)

* fsck failed.  Please repair manually and reboot.  Please note that the root file system is currently mounted read-only.  To remount it read-write:
  # mount -n -o remount, rw /

My brand spanking new command line reads with the mildly shocking and depressing label:

root@(none):~#

At this point none of my chanting, sorcerous hexes, or banging face against the keyboard are of any use.  The witch inside the box that makes it work is obviously sick.  Can anyone help out with this or do I need to go get a new witch?

Reinstalling would make me sad.

I recently changed the size on a couple of partitions with the GPARTED LIVECD, but I did not touch any of which my Ubuntu installation are on.  I wonder if I messed something up indirectly?

---

### Post by dg_w on 2006-04-25
Nicley broken :) 

Ok as the error states, it looks like a read error to the drive \ partition
Have you tried running fsck and seen the results ?
How did you partition the drive up for ubuntu ?

Here a good fsck guide

[http://www.adminschoice.com/docs/fsck.htm](http://www.adminschoice.com/docs/fsck.htm)

Let us know how you got on

---

### Post by Mookawaka on 2006-04-25
I read the guide, but frankly there are many foriegn languages that make more sense to me.  Though I did discover the source of my woes.
Mental note:  Abnormal shutdown due to hardware error, power failure, or ignorant computer user is BAD.

I booted the computer again and when I got to the scary root@(none) command line I ran **fsck**.
Presented with the seemingly unending list of "ignore error, force rewrite" I got frightened and aborted.
So then I tried **fsck -y** which answers "yes" to all that babble.

This has fixed everything and I can once again go back to wasting time on my computer and looking for creative ways to break things.  JOY!

Thank you very much for the help dg_w.

---

