---
title: "Canon Vixia HF M31"
date: 2012-03-02
forum: General Help
---

### Post by AlmightyMokona on 2012-03-02
Hey guys, I just started using this new camcorder and the transfer seems it was intended for Windows 7, because I can just plug the USB in on there and transfer over all my videos.  Is there a working Canon drive for Linux?...because the editing programs I use are Linux based and it would be very annoying to have to transfer my files on Windows  reboot and then edit on Ubuntu every time.

---

### Post by Jerry N on 2012-03-02
I can connect my Canon HFM 300 to a Linux based computer and read the video files just fine through the supplied USB cable.  You have to work your way down through the folders but you should find a bunch of .mts files.  This goes AVCHD to BDMV to STREAM. The .mts files are in the STREAM folder.   

Jerry

By the way, I use the Canon software in Windows to merge the small .mts files into larger .m2ts files.  Other merging software I have tried screws up the sound synchronization.

---

### Post by AlmightyMokona on 2012-03-03
Where would the folder be?  I figured I would see the files or folders in a mount when I connected it to the USB...Absolutely nothing is popping up for me.

---

### Post by Jerry N on 2012-03-03
> **AlmightyMokona said:**
> Where would the folder be?  I figured I would see the files or folders in a mount when I connected it to the USB...Absolutely nothing is popping up for me.

I don't normally connect the Canon directly to the computer.  Mine does not have built-in memory, so I just remove the SD card and plug it in to the computer.  

The camera does not automount when you plug it in.  You need to press the little button called DISP (onscreen display), shown on Page 11 of my manual.  When the DISP is pressed, the camera recognizes that it is connected to the computer and the camera display requests that you select how it is to be connected.  When you select "Computer/Printer", the camera should automatically mount as a USB device and you should see a folder named "PRIVATE".  From there, select AVCHD, BDMV, and STREAM.  Under STREAM, you should see a bunch of .mts files.  Let me know if this works OK for you.  

For me, this works the same way with Mint 12 (Ubuntu 11.10), and Windows 7.

I use the HD setting that uses 8gb per hour of recording.  With an AMD Phenom II 3.2 ghz 4 core processor VLC can play the .mts video but any attempt to fast forward or reverse will throw the video completely out of sync.  The Win 7 Media player will play these .mts files without a hitch on an old dual core 2ghz processor.  I find that VLC doesn't do so well in Windows.

Jerry

---

### Post by AlmightyMokona on 2012-03-03
> **Jerry N said:**
> I don't normally connect the Canon directly to the computer.  Mine does not have built-in memory, so I just remove the SD card and plug it in to the computer.  

The camera does not automount when you plug it in.  You need to press the little button called DISP (onscreen display), shown on Page 11 of my manual.  When the DISP is pressed, the camera recognizes that it is connected to the computer and the camera display requests that you select how it is to be connected.  When you select "Computer/Printer", the camera should automatically mount as a USB device and you should see a folder named "PRIVATE".  From there, select AVCHD, BDMV, and STREAM.  Under STREAM, you should see a bunch of .mts files.  Let me know if this works OK for you.  

For me, this works the same way with Mint 12 (Ubuntu 11.10), and Windows 7.

I use the HD setting that uses 8gb per hour of recording.  With an AMD Phenom II 3.2 ghz 4 core processor VLC can play the .mts video but any attempt to fast forward or reverse will throw the video completely out of sync.  The Win 7 Media player will play these .mts files without a hitch on an old dual core 2ghz processor.  I find that VLC doesn't do so well in Windows.

Jerry

OMG THANK YOU SO MUCH!  Is there a thanks button on these forums, because you definitely deserve it?  My camera works very similar, instead of the display it is the play/stream button for me that brings up those options.  Now I just have to see if I can get the image mixer that came with it going, I will test that out later and let you know how it goes. Many thanks Jerry!

---

### Post by Jerry N on 2012-03-03
> **AlmightyMokona said:**
> OMG THANK YOU SO MUCH!  Is there a thanks button on these forums, because you definitely deserve it?  My camera works very similar, instead of the display it is the play/stream button for me that brings up those options.  Now I just have to see if I can get the image mixer that came with it going, I will test that out later and let you know how it goes. Many thanks Jerry!

Glad to be of assistance!

Jerry

---

### Post by AlmightyMokona on 2012-03-03
btw I am on an amd quadcore as well and vlc works fine for what i need it to do as far as viewing purposes, slowdown works fine, but speedup gets a little choppy after about 1.2...I am just using this for initial viewing to check video though, and I have no issues jumping frame, I use kdenlive for editing.

---

