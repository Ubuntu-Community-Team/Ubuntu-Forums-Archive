---
title: "Gparted does no longer read the partitions on Ubuntu10.04"
date: 2010-12-10
forum: General Help
---

### Post by el10 on 2010-12-10
I do not know what I have done but I used to be able to see the partitions on Hard Disk wich has WinXP and Ubuntu 10.04 as well as other partitions I have created.

I can access the partitions but cannot any longer see them with Gparted. Enlosed 2 screenshot ( Gparted and Disk Utility which shows the partition)

Can anyone help ?

Thanks 
elio

---

### Post by Quackers on 2010-12-10
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by dcstar on 2010-12-10
> **el10 said:**
> I do not know what I have done but I used to be able to see the partitions on Hard Disk wich has WinXP and Ubuntu 10.04 as well as other partitions I have created.

I can access the partitions but cannot any longer see them with Gparted. Enlosed 2 screenshot ( Gparted and Disk Utility which shows the partition)

Can anyone help ?


If you are in fact running 8.04 then I believe that version of gparted has a bug that has been fixed in later versions.

Boot off a 10.10 Live CD and see if that gparted works ok.

---

### Post by srs5694 on 2010-12-12
See [this Web page of mine,](http://www.rodsbooks.com/missing-parts/index.html) which describes one possible cause of the problem you're reporting. If that doesn't help, please post the output of "sudo fdisk -lu", between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for clarity. Note that the "u" in "-lu" is critical; without this character, fdisk reports partition sizes in cylinders, which is hopelessly imprecise for diagnosing this problem.

---

