---
title: "USB drive becomes crazy in Linux"
date: 2006-02-07
forum: General Help
---

### Post by Gundamdriver on 2006-02-07
Hi. I had got a 1GB USB drive to store data.
Yesterday I plugged in the USB drive as usual, and try to copy some data.

I found that some files were inside my USB drive, wihch were unknwon, un-readable.
It is sure that the computer doesn't have virus.

More interesting, I found that the total files volume is 3GB! But my USB drive hs got only 1GB capacity!!!
And, there was a file named "USBC" created, stored in my USB drive.

When I plug the USB drive in MS Windows, half of the files cannot be seen, and a file named "USBC" is found. Do you know how large is the file? ~3GB!
[B]
I want to ask why this problem exist? What is the "USBC"?[/B]

I don't trust Linux as previous...:( 
iPod cannot be mounted, 1GB USB drive has got a 3GB file inside...

Please someone leave a comment...
And, please read the attached picture for reference.

---

### Post by bernardfrancois on 2006-02-07
Probably the inodes on your USB stick are containing wrong information about the size of that file.

Maybe some problems occured and half of the files have been put in a seperate file after some rescue operation... (but Linux normally puts all rescued files in a folder called *lost+found*).

You could post the output of the following commands (after making your usb stick's mount point your working directory)
```

ls -l
du -b USBC
du -h USBC
du -b --apparent-size USBC
stat USBC
file USBC

```

---

### Post by pihbar on 2006-09-02
if you deleted something there is a hidden .trahs dir from gnome



remove it. it worked for me :)

---

