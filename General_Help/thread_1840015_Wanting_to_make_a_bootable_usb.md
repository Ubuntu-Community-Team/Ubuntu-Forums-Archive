---
title: "Wanting to make a bootable usb"
date: 2011-09-06
forum: General Help
---

### Post by 3lud13 on 2011-09-06
I am currently running ubuntu 11.04 but wanting to try linux mint.
I have downloaded the iso and would have assumed I could use the startup disc creator app to burn the iso to usb however after many tries this fails to work. I do not recall the error message that comes up when I try to boot from it but can check if it will help more.  I can not burn the iso to cd and run it that way as I am using a netbook with no optical drive.
Is there some other way I can burn the iso to usb so I can boot from it.

---

### Post by Frogs Hair on 2011-09-06
Many people use the program at the link .[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by WorMzy on 2011-09-06
When I made my bootable USB stick, I just copied everything (bar cached packages) from / into the root directory of the USB stick's partition, then manually installed and configured grub (legacy, not 2), and updated the /etc/fstab file on the USB stick. Boots fine.

---

### Post by Hakunka-Matata on 2011-09-06
Ctrl Q

---

### Post by Hakunka-Matata on 2011-09-06
> **3lud13 said:**
> I am currently running ubuntu 11.04 but wanting to try linux mint.
I have downloaded the iso and would have assumed I could use the startup disc creator app to burn the iso to usb however after many tries this fails to work. I do not recall the error message that comes up when I try to boot from it but can check if it will help more.  I can not burn the iso to cd and run it that way as I am [COLOR=Red]using a netbook[/COLOR] with no optical drive.
Is there some other way I can burn the iso to usb so I can boot from it.

Hi, welcome. what kind of netbook are you working with?  Does it have a plastic "plug" sort of that lives in the sd slot when not in use?  It has given other people trouble be making a usb not visible during BIOS first boot assignments. 

unetbootin works fine

---

### Post by 3lud13 on 2011-09-06
> **Hakunka-Matata said:**
> Hi, welcome. what kind of netbook are you working with?  Does it have a plastic "plug" sort of that lives in the sd slot when not in use?  It has given other people trouble be making a usb not visible during BIOS first boot assignments. 

unetbootin works fine

Im using an asus eepc 1008P no plastic plug in sd slot sd slot actually no longer works as I damaged the connector awhile back when I upgraded harddrive. Have had no issues before booting from usb thats actually how I installed ubuntu along with a few other distros at various times though I was dual booting with windows then and was using windows to create my bootable usb (using the program Universal-USB-Installer-1.8.6.2) now that I am only using ubuntu Im not overly sure how to do it properly.

Am checking out the above link that frogs hair posted and its kind of looking promising though the other 2 posts dont seem to make much sense to me.

---

### Post by Hakunka-Matata on 2011-09-06
> **3lud13 said:**
> Im using an asus eepc 1008P no plastic plug in sd slot sd slot actually no longer works as I damaged the connector awhile back when I upgraded harddrive. Have had no issues before booting from usb thats actually how I installed ubuntu along with a few other distros at various times though I was dual booting with windows then and was using windows to create my bootable usb (using the program Universal-USB-Installer-1.8.6.2) now that I am only using ubuntu Im not overly sure how to do it properly.

Am checking out the above [COLOR=Red]link that frogs hair posted[/COLOR] and its kind of looking promising though the other 2 posts dont seem to make much sense to me.

Yes, that's the link for unetbootin.  You have to download and extract the unetbootin package. you'll end up with a file unetbootin-linux-549 and it'll be an executable.  Double click on that file and it should start up, unless it needs to have it's permissions set to be executable.

right  button on file name, 
select: properties
select Tab: Permissions
tick the box, 
Allow executing file as program

double click on it again now

---

### Post by 3lud13 on 2011-09-06
Program downloaded fine and yes I did end up having to set the permission to executable I was kind of worried at first when it downloaded and wouldnt start but went back through and read the webpage currently it is burning mint 11 to a usb and shall see how I go after that

---

