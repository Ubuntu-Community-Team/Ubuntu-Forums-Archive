---
title: "Operating system not found."
date: 2009-07-01
forum: General Help
---

### Post by Randomness6454564 on 2009-07-01
I had Ubuntu installed on a computer and decided to put windows on it to play games. So I used GParted to resize and then continued to the installation. Everything was going fine but when I turned the computer off and on again, it loaded straight to windows. Didn't even ask me. So I popped in the Ubuntu cd and the computer acted as if it wasn't even there. I put in the GParted and DBan to see if they would boot and they did. So I decided to delete the windows partition. Now when I boot it says: "Operating system not found." I used GParted to resize the Ubuntu partition to take the space of the windows one. It said it was successful so I rebooted. No game. I took a screenshot of the following: [IMG]http://img.photobucket.com/albums/v300/etabrutsam/Screenshot-2.png[/IMG]
This is the only partition.

"do not use the partition"? No mount point? I would just change it but I don't want to screw any thing up. What should I do? Thanks!

---

### Post by Sub101 on 2009-07-01
You would need to restore grub as the Windows bootloader will have removed it from the MBR.

To do this: [http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

In general it is easier to install Windows, then Ubuntu.

---

### Post by geo909 on 2009-07-01
If you have any problems, try that too:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It is supposed to restore the grub automagically..

Never tried it though, so I can't say, but it's pretty popular

---

