---
title: "ubuntu 12.04 extreeemely slowww on very good pc"
date: 2012-05-25
forum: General Help
---

### Post by realflow100 on 2012-05-25
no matter what i do or what theme gui or interface i use ubuntu always runs slooowwwwwwwwww and takes ages to load firefox and i cant even bare to go on youtube videos play like they're rendering one pixel a second it is totally un usable

my pc is aspire r1600

1.6ghz intel atom processor
nvidia 2gb video ram
2.7GB physical memory
1 75gb hard drive
it runs like crap and its even worse after installing all the updates i can BARELY do anything it took me half an hour to post this because my text keeps freezing when i type! why does my ubuntu run so crappy??? i used to run windows 7 ultimate 64bit just fine and dandy and was extremely fast too then i replaced it with ubuntu just to try it out now its slower than a half drunken dead snail! i want my windows 7 back!

---

### Post by PhantomTurtle on 2012-05-25
Did you install the nVidia drivers? (To do it, open Additional Drivers and install the one you want).

---

### Post by realflow100 on 2012-05-25
yes and it made no difference at all

---

### Post by PhantomTurtle on 2012-05-25
hmmmm, was it slow on the live cd as well? Try this, open terminal and type this in,
```
sudo apt-get install gnome-panel
```
After it installs, log out, press the little Ubuntu logo next to your name and select Gnome Classic(No effects). Tell me how that works out for you.  Maybe you could try one of the lighweight Ubuntu "spins", if that doesn't work, such as Lubuntu or Xubuntu. Maybe its just unity.

---

### Post by realflow100 on 2012-05-25
i didnt use live cd i downloaded web app onto my pc and installed from that my pc doesnt have a cd or dvd drive and yes i already tried that but it still lags like crazy and takes forever to load anything cant watch youtube at all its worse than a slideshow

---

### Post by PhantomTurtle on 2012-05-25
By web app, do you mean WUBI? (WUBI installs Ubuntu inside Windows).

---

### Post by realflow100 on 2012-05-25
yes whatever its called and i replaced my windows 7 operating system

---

### Post by PhantomTurtle on 2012-05-25
WUBI does not replace Windows. You can boot into Windows by restarting and selecting Windows 7 at the bootloader. If it did replace Windows, then you must have done a full install. You didn't use a live USB did you?(it seems to be the only other way, since you don't have a CD drive).

---

### Post by realflow100 on 2012-05-25
no i didnt use a usb flash drive or anything when i installed ubuntu it replaced my windows 7 there is no reason why ubuntu is running this slowly! i can run windows 7 ultimate why not ubuntu?? i thought ubuntu was for crappy old computers anyways!!

---

### Post by PhantomTurtle on 2012-05-25
Then it might be a problem with WUBI. I do not understand why it would be slow, but why don't you try a Live USB and dual boot it without using WUBI(its really easy, here's a tutorial if you want to try it - [http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/]("http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/")). The Live USB will tell you if it is a WUBI problem. Also Ubuntu is not built only for "crappy old computers", in fact Unity doesn't work very well with older hardware because it requires a higher system requirements. That is the reason Lubuntu and Xubuntu exist, for older systems. I run Ubuntu only on my computer and it is not a "crappy old computer" because my computer has higher specs than yours and Ubuntu runs perfectly. Anyways it could be a problem with WUBI is all I can say from what I have read. Try the live USB, see if it runs at full speed.

---

### Post by uRock on 2012-05-25
From your previous thread, > **realflow100 said:**
> came preinstalled with ubuntu
Please copy and paste the following commands into a terminal, then copy and paste the output from the terminal here, so we can better assess the situation.```
lspci
``````
lscpu
```

---

### Post by realflow100 on 2012-05-25
my pc doesnt support booting from usb flash drive there is no option in the boot menu for booting from any kind of storage device and my terminal windows wont open they are just black and empty i cant see anything in them

---

### Post by PhantomTurtle on 2012-05-25
> **realflow100 said:**
> my pc doesnt support booting from usb flash drive there is no option in the boot menu for booting from any kind of storage device and my terminal windows wont open they are just black and empty i cant see anything in them

Try what uRock said in the post above.

EDIT: sorry didn't notice the part about how you cant use the terminal.

---

### Post by uRock on 2012-05-25
Have you tried creating a bootable USB to see if the option becomes available with it inserted at start up? I have used systems that do not offer USB as an option unless one is present when powered on.

---

### Post by realflow100 on 2012-05-25
i dont have a usb and i cant afford to buy one either

---

### Post by uRock on 2012-05-25
How did you install ubuntu?  (WUBI will not run if Windows has been removed.)

Have you tried installing xubuntu or lubuntu? Both of which are lighter and faster on older machines.

Have you tried selecting a different kernel at start up?

---

### Post by realflow100 on 2012-05-25
when i installed ubuntu my windows 7 was gone afterwards there is no option to change kernel or whatever your saying it doesnt show any boot menu or anything it just stays black for a bit then i see my mouse pointer and my ubuntu starts up. i can hardly get to my bios because it appears and disappears in half a second then it stays black till my ubuntu starts up so i dont know what to do there and i dont even know how to install those i dont even know what those are i havent heard of them before i dont even know what a kernel is but im using xfce theme or something and it still lags like crazy and randomly freezes and locks up to when i have to manually pull the power cable on my computer

---

### Post by PhantomTurtle on 2012-05-25
> **realflow100 said:**
> when i installed ubuntu my windows 7 was gone afterwards there is no option to change kernel or whatever your saying it doesnt show any boot menu or anything it just stays black for a bit then i see my mouse pointer and my ubuntu starts up. i can hardly get to my bios because it appears and disappears in half a second then it stays black till my ubuntu starts up so i dont know what to do there and i dont even know how to install those i dont even know what those are i havent heard of them before i dont even know what a kernel is but im using xfce theme or something and it still lags like crazy and randomly freezes and locks up to when i have to manually pull the power cable on my computer

It shouldn't be gone. Can you mount your Windows partition in nautilus (the file manager)? At boot hold down the shift key, which will bring up the GRUB menu, select Windows 7 loader at the bottom of the list on it.

---

### Post by realflow100 on 2012-05-25
i dont see a windows partion to mount in file manager and when i looked in gparted and there was only ext file system or something and i tried holding shift key but it doesnt bring up any type of menu it just starts my ubuntu to the log in screen :(

---

### Post by MadmanRB on 2012-05-25
I have had issues like this WUBI, not on all computers but some even some high spec ones.
WUBI can be a little clunky.

---

### Post by lisati on 2012-05-25
When running Ubuntu (either "within" windows using Wubi, or in its own partition) the area containing your Windows files will not always have *exactly* the same name in Ubuntu as it does in Windows. Have a look for a folder/directory called "host".....

---

### Post by realflow100 on 2012-05-25
i dont have a folder called host in my ubuntu directory just some other folders and some system file things.. and a folder called root which i cant open

---

### Post by GregA on 2012-05-26
OK, interesting thread.

I don't think the OP installed Ubuntu using Wubi.  He doess't have a clue what Wubi is, in the first place.   It seems he did a "net-install" . . . downloading the install image direct from the web, and he botched the install by overwriting Windows (install using the whole disk).

So, Windows is likely permanently gone.   

The install runs crappy, because the system doesn't have the memory or processor speed to run all the Ubuntu desktop effects.   As I don't run Ubuntu - - I am not aware of how to have Unity disable the desktop effects.  If that doesn't improve performance, the OP might try to enable the standard Vesa graphics driver.

---

### Post by realflow100 on 2012-05-26
when i had windows 7 ultimate i could run it just fine windows 7 should be 10 times more resource intensive than ubuntu??? why does my ubuntu run so crappy my processor is fine and my graphics card is amazing i have way more than enough physical memory to run it too! why does it run soooo slooww???? i tried disabling all effects and tried using Xfce with no unity interface of any kind it still runs slooww! yes i know what webi is i used it to install ubuntu

---

### Post by uRock on 2012-05-27
> **realflow100 said:**
> when i had windows 7 ultimate i could run it just fine windows 7 should be 10 times more resource intensive than ubuntu??? why does my ubuntu run so crappy my processor is fine and my graphics card is amazing i have way more than enough physical memory to run it too! why does it run soooo slooww???? i tried disabling all effects and tried using Xfce with no unity interface of any kind it still runs slooww! yes i know what webi is i used it to install ubuntu

If you used Wubi, then Windows would be offered at startup. It sounds like your ubuntu install did not go right and the only way to fix your system would be to reinstall Windows and/or ubuntu.

---

