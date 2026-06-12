---
title: "bricked flash drive. help!"
date: 2010-10-13
forum: General Help
---

### Post by motorhead6776 on 2010-10-13
not really sure where to put this but here it is.

i tried to create a bootable ubuntu drive from my mac for my windows pc following these steps on the ubuntu site.

   1.  Download the desired file
   2. Open the Terminal (in /Applications/Utilities/ or query Terminal in Spotlight)
   3. Convert the .iso file to .img using the convert option of hdiutil (e.g., hdiutil convert -format UDRW -o ~/path/to/target.img ~/path/to/ubuntu.iso)
   4. Note: OS X tends to put the .dmg ending on the output file automatically.
   5. Run diskutil list to get the current list of devices
   6. Insert your flash media
   7. Run diskutil list again and determine the device node assigned to your flash media (e.g. /dev/disk2)
   8. Run diskutil unmountDisk /dev/diskN (replace N with the disk number from the last command; in the previous example, N would be 2)
   9. Execute sudo dd if=/path/to/downloaded.img of=/dev/rdiskN bs=1m (replace /path/to/downloaded.img with the path where the image file is located; for example, ./ubuntu.img or ./ubuntu.dmg).
  10.
          * Using /dev/rdisk instead of /dev/disk may be faster.
          * If you see the error dd: Invalid number '1m', you are using GNU dd. Use the same command but replace bs=1m with bs=1M.
          * If you see the error dd: /dev/diskN: Resource busy, make sure the disk is not in use. Start the 'Disk Utility.app' and unmount (don't eject) the drive.
  11. Run diskutil eject/dev/diskN and remove your flash media when the command completes
  12. Restart your Mac and press alt while the Mac is restarting to choose the USB-Stick


needless to say it didnt work and whenever i pulg my flash drive into my pc it prompts me to format it, and what was an 8gb drive now shows up as 200mb. any ideas how to fix this?

---

### Post by lukeiamyourfather on 2010-10-13
Any disk partition tool should be able to restore the full capacity. For example GParted in Linux. Note that if partitioning the flash drive again doesn't work, the flash drive might have failed coincidentally. They do go bad (more often than you might think) but that doesn't mean installing Ubuntu was the cause.

---

### Post by motorhead6776 on 2010-10-13
ive tried the diskutil in osx but it always seems to format as hfs or something despite what i tell it to do >.<  once my 10.10 install finishes im hoping gparted will straighten everything out as it still shows the full 8gb in osx.

---

