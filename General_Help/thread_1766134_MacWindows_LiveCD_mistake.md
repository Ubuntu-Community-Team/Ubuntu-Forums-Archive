---
title: "Mac/Windows LiveCD mistake"
date: 2011-05-24
forum: General Help
---

### Post by troyguffey on 2011-05-24
I used my brother-in-law's high-speed connection to download an Windows image of Natty Narwhal 11.04 LiveCD amd64 on his MacBook.  But when I burned it to disk there was only a single folder named "Ubuntu 11.04 amd". It doesn't boot

Is there any way to fix this back to a working LiveCD without having to spend weeks downloading the image again over dial-up?

---

### Post by Hedgehog1 on 2011-05-24
> **troyguffey said:**
> I used my brother-in-law's high-speed connection to download an Windows image of Natty Narwhal 11.04 LiveCD amd64 on his MacBook.  But when I burned it to disk there was only a single folder named "Ubuntu 11.04 amd". It doesn't boot

Is there any way to fix this back to a working LiveCD without having to spend weeks downloading the image again over dial-up?

If the file ends with '.iso', you are in luck.

Copy the ISO file to your hard drive, and the use it to make a proper bootable CD.  Your burning software should offer a 'burn CD from image' or 'burn CD from ISO' option.

***The Hedge***

:KS

---

### Post by kilowattradio on 2011-05-24
> **troyguffey said:**
> I used my brother-in-law's high-speed connection to download an Windows image of Natty Narwhal 11.04 LiveCD amd64 on his MacBook.  But when I burned it to disk there was only a single folder named "Ubuntu 11.04 amd". It doesn't boot

Is there any way to fix this back to a working LiveCD without having to spend weeks downloading the image again over dial-up?

You can use the 'Disk utility' program in the finder Applications/Utilities folder. Just load the image and burn to disk.

---

### Post by troyguffey on 2011-05-24
> **kilowattradio said:**
> You can use the 'Disk utility' program in the finder Applications/Utilities folder. Just load the image and burn to disk.

I downloaded it while I was visiting my sister, and don't have access to the MacBook, or the downloaded image.  Only what got burned onto the CD.

There's only a single file folder on the CD named "Ubuntu 11.04 amd" with no .iso extension.

---

### Post by linuxinstalledfromhdd on 2011-05-24
No, you would need to download Ubuntu again.  You can do it on any computer you want. 

**From Windows**
                                                                                             
[LIST=1]
[*]                       If you do not have software to burn an ISO image, download [Infra Recorder]("http://infrarecorder.sourceforge.net/"), open source image burning software.
[*]                       Insert a blank CD-R, if a dialog box pops up - click *Cancel*.
[*]                       Open Infra Recorder, and select the *Actions* menu, then *Burn image*.
[*]                       Select the Ubuntu CD image file you want to use, then click *Open*.
[*]                       In the dialog box that opens, click *OK*.
[/LIST]
                 
                                                                                                              **From a Mac**
                 
                 To burn most ISOs, you can use Apple's Disk Utility (Disk Copy in older versions).
                                    
[LIST=1]
[*]                       Launch Disk Utility (Applications/Utilities/Disk Utility)
[*]                       Drag the ISO to the sidebar of the Disk Utility main window.
[*]                       Select the ISO where you just dragged it, and choose (Menu/Image/Burn...)
[*]                       In Disk Utility, ensure that the Verify burn  checkbox is ticked (you may need to click on the disclosure triangle to  see the checkbox).
[*]                       Insert a blank CD and select Burn
[/LIST]

---

