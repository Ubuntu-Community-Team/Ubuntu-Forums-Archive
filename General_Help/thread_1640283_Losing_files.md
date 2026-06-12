---
title: "Losing files"
date: 2010-12-07
forum: General Help
---

### Post by Inquirer002 on 2010-12-07
I run Ubuntu from a USB. I downloaded the Ubuntu file from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) and placed it into the USB using the Universal USB installer. 

I ran Ubuntu and then installed a program and a couple of files, and when done I restarted the computer and started using Windows. Today when I again used Ubuntu, all the programs I installed yesterday, and also the files are missing. 

I wondered if I made a mistake so I only downloaded one file and restarted the computer and returned to Ubuntu,  and again the file is missing. None of these files were in a sort of temp folder.

---

### Post by Slim Odds on 2010-12-07
You need to create a persistent USB install.

Try this: [http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by Inquirer002 on 2010-12-07
Thanks for the quick reply! That looks like the solution, I know I selected 'No persistence' in the USB installer.

Thanks again :)

---

### Post by Inquirer002 on 2010-12-07
Another question...
I am using a 16GB USB, any chance of increasing the space set aside. The USB installer only sets aside a max of 4GB.

---

### Post by Slim Odds on 2010-12-07
> **Inquirer002 said:**
> Another question...
I am using a 16GB USB, any chance of increasing the space set aside. The USB installer only sets aside a max of 4GB.

If the USB stick is FAT32, that's probably the limitation. I'm not completely sure how those installers work.

---

### Post by Inquirer002 on 2010-12-08
Solution: I figured out how to create a persistent drive larger than 4GB
Here is the link :[http://www.pendrivelinux.com/create-...per-partition/]("http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/")

A note: When I created a casper-rw ext2 partition, it hanged. I redid the installation, but this time with casper-rw ext4 partition and it seems to work

---

