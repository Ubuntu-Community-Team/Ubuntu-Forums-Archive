---
title: "Question about booting with multiple operating systems"
date: 2010-01-13
forum: General Help
---

### Post by mikeee99 on 2010-01-13
I am new to Ubuntu, so forgive me if all the info I need isn't here. Ok so, I have both windows XP home and Ubuntu 9.10 installed on my computer. I started with Ubuntu 8.04 (i think that was the number) and it has updated a few times since then. You see the thing is that when I choose an operating system at the boot up, it lists all of the updates to ubuntu. so there are like 12 options to choose from besides windows XP and Ubuntu 9.10.

The thing is I found another post with the same question that recommended leaving the old kernals in case there is a problem with an update. That makes total sense, but I was hoping to find a way that I could get rid of all but the latest Ubuntu version and one older than that. The list is getting kinda long. 

Let me know if you need any more info. 

thanks!

---

### Post by JvIasterMind on 2010-01-13
There is a great explanation here (you basically just remove the old kernels through Synaptic)...
[http://stream-recorder.com/forum/edit-grub-entries-ubuntu-9-10-no-t5122.html](http://stream-recorder.com/forum/edit-grub-entries-ubuntu-9-10-no-t5122.html)

> 
If you want to remove entries with old kernels from Grub menu, remove the kernel and the Grub entry will be removed as well.

**How to remove old kernels**
[LIST=1]
[*]Go to Terminal and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: 2.6.31-16-generic.
[*]Go to **System** -> **Administration** -> **Synaptic Package Manager **
[*]Paste "**linux-image-**" (without quotes) **into the search box** of Synaptic Package Manager. The results should show every available and installed kernel. A green box on the left indicates that the package is installed.
[*]Once you have located an old kernel, right-click on it and select "**Mark For Complete Removal**". Repeat for every kernel that you want to remove (make sure to leave the current kernel!!!) and click the **Apply**.
[/LIST]

Please note that you need to be very careful with what you remove. Do NOT remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu otherwise!

Your computer and Grub menu should now be free of old kernels.

---

### Post by ssulaco on 2010-01-13
You can open a terminal and run```
sudo apt-get remove --purge 2.6.xx-xx-*
```
where xx is the kernel you **do not** want to keep,this removes the image and header.
yes,keep the backup kernel

---

### Post by mikeee99 on 2010-01-14
Thanks! That worked perfectly, I am still learning about ubuntu. Now I'm gonna have to learn all about kernals! :D

---

