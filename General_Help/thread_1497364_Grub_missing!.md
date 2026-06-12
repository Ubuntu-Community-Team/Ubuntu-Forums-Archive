---
title: "Grub missing!"
date: 2010-05-30
forum: General Help
---

### Post by ankit.vader on 2010-05-30
i installed lubuntu on an external hard disk. but now when i want to boot to my computer without external hard disk it shows an error and the grup prompt comes saying 'grub>rescue'. do i need to install grub on my computer again, r is there another solution..........

PS: grub menu comes when the external disk is connected, and then i can log into my computer...

---

### Post by Ozymandias_117 on 2010-05-30
It installed the /boot folder on the external, but the MBR on your internal. 

What operating system do you have on your internal?

---

### Post by ankit.vader on 2010-05-30
> What operating system do you have on your internal?

i have ubuntu 10, only, on my internal..

---

### Post by WorMzy on 2010-05-30
You're going to have to boot a live CD, and reinstall grub so that it points the mbr to your internal /boot directory, rather that your external.


This may help: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html]("http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html")

---

### Post by ankit.vader on 2010-05-30
> you're going to have to boot a live CD, and reinstall grub so that it points the mbr to your internal /boot directory, rather that your external.

so will i be able to use lubuntu which i installed on external, without any problems???

---

### Post by WorMzy on 2010-05-30
Not immediately, you'll need to boot into Ubuntu, connect the external hard drive and create an entry for lubuntu. I have grub legacy, so I don't know how you'd manage this in grub2; however, I think you need to edit a file in /etc/grub.d, then run 'sudo update-grub'.

---

### Post by Zerocool Djx on 2010-05-30
> **WorMzy said:**
> Not immediately, you'll need to boot into Ubuntu, connect the external hard drive and create an entry for lubuntu. I have grub legacy, so I don't know how you'd manage this in grub2; however, I think you need to edit a file in /etc/grub.d, then run 'sudo update-grub'.

How do you do you edit grub like that? Cause I wanted to have windows on an external HD for back up if need be and just leave Ubuntu on my internal..

---

### Post by Ozymandias_117 on 2010-05-30
No editing required. Just fix your MBR, boot to your internal, hook up your external and run ```
sudo update-grub
```

---

### Post by ankit.vader on 2010-05-30
```
sudo update-grub
```

this didn't work. i'm still getting the same error, that is, "No such Device" and then grub prompt comes.

---

### Post by Ozymandias_117 on 2010-05-30
I meant after reinstalling GRUB on your internal hard drive, you don't have to do any config file hacking to get it to boot your external. You will still have to go through the steps to fix your MBR.

1. Boot to a liveCD of 10.04

2. Mount your Internal hard drive's Ubuntu partition

3. (Assuming your internal hard drive is sda - if not, just change this) ```
 sudo grub-install --root-directory=/media/name_of_your_drive /dev/sda
```



If you can't figure out what you need to put for that last command, mount your Ubuntu partition, and post the output of ```
mount
``` and ```
sudo fdisk -l
```

---

