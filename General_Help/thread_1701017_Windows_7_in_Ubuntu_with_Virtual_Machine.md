---
title: "Windows 7 in Ubuntu with Virtual Machine"
date: 2011-03-05
forum: General Help
---

### Post by Rikeshar on 2011-03-05
Hello everyone. I'm currently using Ubuntu 10.10 on an external hdd. My internal HDD has Windows 7 installed. Is there a way to run Windows from within Ubuntu, off of the hdd that's currently installed on?

---

### Post by joberly on 2011-03-05
You can't run the installation from where it resides, but you can migrate that installation to a Virtual Machine. (You won't be running your 'actual' install, therefore any changes you make in the VM won't exist if you decide to fully boot into windows.)

Start [here.]("http://www.virtualbox.org/wiki/Migrate_Windows")

---

### Post by seawolf167 on 2011-03-05
You can image your Windows installation and restore that image to a virtual drive in VBox. I've done this a couple times to restore files from an image for a computer that was replaced.

I found a [how-to]("http://jlorenzen.blogspot.com/2010/07/restoring-clonezilla-image-using.html") online that you should be able to follow (rather than typing everything out), but ask if you've got questions.

You can also use [Disk2vhd]("http://technet.microsoft.com/en-us/sysinternals/ee656415.aspx") to image your drive to a virtual machine - I haven't used it personally, but have heard good things about it.

---

### Post by Rikeshar on 2011-03-06
Thanks everyone!

---

