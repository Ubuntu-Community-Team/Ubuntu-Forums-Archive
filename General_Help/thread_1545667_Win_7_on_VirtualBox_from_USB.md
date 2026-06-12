---
title: "Win 7 on VirtualBox from USB"
date: 2010-08-04
forum: General Help
---

### Post by jesuisbenjamin on 2010-08-04
Hello there,

I am aiming at installing Flash Builder 4 on Ubuntu, which is impossible according to the web. There is no Linux alternative as good as the former (unfortunately).

So i want to install Win 7 to install Falsh Builder 4. I thought first of doing a dual boot but then found the process complicated somehow and also very much polluting. (It don't like the idea of partitioning, restoring grub etc.). Installing Win in Ubuntu however, seemed like a better idea.

So i found [this nice tutorial]("http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html") on how to install Windows in Ubuntu with the Oracle VM VirtualBox. It's quite amazing really.

The first part of the tutorial went fine (i.e. installing VirtualBox and creating a new Virtual Machine).

The second part (i.e. installing Win 7) is trickier. The main reason is that i have an ISO file of Win 7 and no blank DVD. Before i go to the store and spend money on that i'd like to figure out how to install Win 7 by my own means.

What i (naively) did was to mount -o loop the .iso into a repertory and copy the content to a USB storage key. When i want to install Win 7 on my VM however it does not allow me to select my USB as an installer.

How can i install Win 7 from my ISO, either from USB or HD (i don't mind)? I'd rather not spend more money on this than i already did. Is there something i am not understanding? Why would a DVD be more installable than a USB or HD? It comes down to O's and 1's right?

Well thanks in advance :)

Benjamin

---

### Post by ronnielsen1 on 2010-08-04
If you open virtualbox, click on the Storage tab on the Windows 7 machine. This will open a new window. Click on the Storage tab. This will open a new window. You should see your cd/dvd device listed. Click on this. To the right, you will see cd /dvd device and an icon with a green arrow. If you click on the icon, you can navigate to the place on your hard drive where your iso is located.

---

### Post by jesuisbenjamin on 2010-08-04
Hey thank you so much!
I had no idea it could just pick up the .iso file! This is awesome.
So i can go on and have fun with this new thing.

Cheers!
B.

---

### Post by ronnielsen1 on 2010-08-04
There's usually an easier way Picking up on the iso makes it a breeze to try another distro. Choose a different file, you have a new machine running

---

