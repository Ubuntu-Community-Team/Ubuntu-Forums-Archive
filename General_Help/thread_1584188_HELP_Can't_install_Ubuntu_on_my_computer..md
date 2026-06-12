---
title: "HELP: Can't install Ubuntu on my computer."
date: 2010-09-28
forum: General Help
---

### Post by spartan9910 on 2010-09-28
Hello, I need some help with installing Ubuntu. I have tried many times with USBs,burnt CDs, even manage to get one from Ubuntu them sevles, and followed many tuts to no avail. 

SPECS: Toshiba Satellite, AMD TurionII dual-Core Mobile M500 2.20 GHz, with 3.00 GB of RAM

Heres the image I get when I try to install/try:

[IMG]http://s695.photobucket.com/albums/vv313/sperten9910/?action=view&current=100_1230.jpg[/IMG]
    
 heres the straight link to pic: [http://s695.photobucket.com/albums/vv313/sperten9910/?action=view&current=100_1230.jpg](http://s695.photobucket.com/albums/vv313/sperten9910/?action=view&current=100_1230.jpg)

If anyone could help me that would be appreciated
THx!!!

---

### Post by coolman98 on 2010-09-28
probably something to do with pci card try another cd

---

### Post by NathanDTaylor on 2010-09-28
That happened to me... But I got a solution..

When the live CD is loading press F6. Once in the menu turn of ACPI. It is in 'Advanced' or something.. just find it. But then start the installation after you turn acpi off.

However, after the installation is done, do the following to load the os.
On the screen with the list of os's, hover over Ubuntu. Then press E. After "Quiet Splash" put "acpi=off". So It will end up as "Quiet Splash acpi=off" then press Ctrl+X to boot into the OS. This is something you will have to do every time you boot, I have not found a permanent fix to this yet.

---

### Post by spartan9910 on 2010-09-28
thanks I will try this now will post if this works

---

### Post by spartan9910 on 2010-09-28
Yeah it works!!!
Thx :)

---

### Post by Iowan on 2010-09-29
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

### Post by Cycledoc on 2010-09-29
I had problems with acpi as well and found that you can permanently add acpi=off to the boot options.   Look here for detailed instructions: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

In summary you have to edit the file /etc/default/grub file and save the changes.

I used the following in the terminal

*sudo gedit /etc/default/grub*

It opened the file /etc/default/grub

I changed the file by adding "acpi=off" just prior to quiet splash.  It looks like this  "acpi=off quiet splash"   

I then updated and saved the changes in the terminal by running

*update-grub*

The change is permanent and runs whenever I start Ubuntu.

Hope this helps.

---

