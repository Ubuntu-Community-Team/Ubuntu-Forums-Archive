---
title: "Trying to access encrypted LUKS LVM volume in nautilus..."
date: 2010-05-02
forum: General Help
---

### Post by Linewbie on 2010-05-02
Hi I was trying to access my encrypted drive using the LiveCD:

I've read this thread:
How to access encrypted LVM drive?
[http://ubuntuforums.org/showthread.php?t=1202286]("http://ubuntuforums.org/showthread.php?t=1202286")

which redirected me to this thread:

Rescue an encrypted LUKS LVM volume
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html")

The commands were:

sudo apt-get install lvm2 cryptsetup

sudo modprobe dm-crypt

sudo cryptsetup luksOpen /dev/sdb1 crypt1

key slot 0 unlocked.
Command successful.

sudo vgscan --mknodes
  Reading all physical volumes.  This may take a while...
  Found volume group "volume-name" using metadata type lvm2

sudo vgchange -ay
  2 logical volume(s) in volume group "volume-name" now active

sudo mkdir /volume

sudo mount /dev/volume-name/root /volume


But when I try to open nautilus in the terminal, I get this error:

sudo nautilus /volume

(nautilus:4612): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

Actually the terminal does open, I can navigate to my home/userdirectory,
there is a link that is titled "Access Your Private Data" and a Readme.txt file that contains this: 
"
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
"

I have tried clicking on the link, nothing happens.

Also the command 
ecryptfs-mount-private
results in:
ERROR: Encrypted private directory is not setup properly

-------------------------------------------------------------------------

I don't think that I made any obvious errors, I am trying to recover what's on my drive after my system failed to boot correctly (actually I installed Silverlight on my other drive (Vista, which I hate, but cannot access Netflix without), tried to boot back to Ubuntu and got these errors:
1)
Could not update ICEauthority file /home/username/.ICEauthority
2)
There is a problem with the configuration server.
(/user/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
3)
Nautilus could not create the folowing required folders:
/home/username/Desktop, /home/username/.nautilus.

---------------------------------------------------------------------
I have tried to follow multiple instructions to repair the "ICEauthority" problems repeatedly, I am at the point now :sad: that I just want to backup some files from the LiveCD to a thumb drive, and reinstall Ubuntu!

Thanks profusely! :smile:

---

