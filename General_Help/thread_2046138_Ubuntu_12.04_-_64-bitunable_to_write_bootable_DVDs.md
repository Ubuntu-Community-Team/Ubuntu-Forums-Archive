---
title: "Ubuntu 12.04 - 64-bit:unable to write bootable DVDs."
date: 2012-08-22
forum: General Help
---

### Post by t0p on 2012-08-22
I can use the default CD/DVD burner in 12.04 (Brasero?) to make back-up disks... data disks.  But if I try to use it to Bburn a bootable disk from a .iso image, it just won't work - when I hit "Burn the disk" the window just disappears.

It insists on calling the disk a DVD-ROM, even though it is clearly a DVD-R - like I already said, it will burn data files like image or video files just fine.  But it won't burn bootable DVDs.  I can get past this by using UNetbootin to make bootable USB sticks.    But that's just an unsatifactory plaster tape over the problem, isn't it?

So how in Ubuntu 12.04 can I make bootable DVDs?

---

### Post by t0p on 2012-08-23
Bump!

---

### Post by mike555 on 2012-08-23
you are burning these .iso as an image , right?

 if so and it still isn't working you might install " Xfburn" , it's a light weight burner that I use to burn dvd image files.

---

### Post by pakguru on 2012-09-10
The best way I have found  to burn a downloaded, Ubuntu operating system iso file to a blank CD/DVD is  not to use Brasero, it never seems to work and always tells me that my  blank disc has insufficient space. 
  I use GnomeBaker CD Writer/DVD Writer, which can be installed from Ubuntu  Download Centre. After opening GnomeBaker be careful NOT to select one of the three tabs  in the 'Make new project' section - otherwise you will just copy the iso  file. You need to go to 'Tools' in the top menu bar and select 'Burn DVD  Image' - that way you will get all the other files that you need to  install your new version of Ubuntu.
  Good Luck

---

