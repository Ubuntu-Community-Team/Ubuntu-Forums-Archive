---
title: "Trouble installing nvidia drivers"
date: 2010-01-08
forum: General Help
---

### Post by BAleR187 on 2010-01-08
I downloaded drivers for my nvidia geforce 9400gt for linux, ran it in terminal and it said failed because i have to run it as root. how do i go about doing so?

---

### Post by audiomick on 2010-01-08
put "sudo" and a space before the command
```
sudo command
```
You will be asked for your password, the one you log in with. You will not see what you are typing as you enter the password.

This allows you to execute a command with root privileges. Be careful with this; as root you are in a position to break your system. Make sure you know what the commands do.

---

### Post by ratcheer on 2010-01-08
Follow these steps, exactly:

Ctrl-Alt-F1
cd to the directory where the driver file is stored.
sudo service gdm stop
sudo sh ./xxxxxxx.run
(...........^^ that is the driver file name)
When the installation script asks if you want to autoconfigure xorg, select Yes
sudo init 6

Tim

---

### Post by pbrane on 2010-01-08
I would recommend following this thread. Just replace the nvidia driver name with the one you downloaded.

[http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")

This will allow for kernel updates without having to re-intall your nvidia drivers.

---

### Post by BAleR187 on 2010-01-08
> **audiomick said:**
> put "sudo" and a space before the command
```
sudo command
```You will be asked for your password, the one you log in with. You will not see what you are typing as you enter the password.

This allows you to execute a command with root privileges. Be careful with this; as root you are in a position to break your system. Make sure you know what the commands do.



well when i open the driver file, it says its a text executable and askes if i want to view its content or run it in terminal


just to note, if it matters or not, when i go to hardware drivers via system, administration, there are no drivers listed.

---

### Post by BAleR187 on 2010-01-08
> **ratcheer said:**
> Follow these steps, exactly:

Ctrl-Alt-F1
cd to the directory where the driver file is stored.
sudo service gdm stop
sudo sh ./xxxxxxx.run
(...........^^ that is the driver file name)
When the installation script asks if you want to autoconfigure xorg, select Yes
sudo init 6

Tim



when i press Ctrl-Alt-F1 and it asks for my login and password, it tells me its incorrect have just not set one? i already have one when i boot up? am i missing something?

---

### Post by BAleR187 on 2010-01-08
> **ratcheer said:**
> Follow these steps, exactly:

Ctrl-Alt-F1
cd to the directory where the driver file is stored.
sudo service gdm stop
sudo sh ./xxxxxxx.run
(...........^^ that is the driver file name)
When the installation script asks if you want to autoconfigure xorg, select Yes
sudo init 6

Tim



When I run this command, "sudo sh ./nvidia.run" which is the name of the driver file, it says cannot open??


p.s. I figured out why i couldnt log in, type the password wrong, lol

---

### Post by 3rdalbum on 2010-01-08
On Ubuntu, you typically don't install Nvidia or ATI drivers manually, because the process isn't user-friendly and the driver would need to be reinstalled every time you update the kernel.

Instead, we use the Hardware Drivers program to download and install the drivers. If you don't see anything listed in this program, then you need to go to Synaptic Package Manager and hit the Reload button so Ubuntu has an idea of what's available in the repositories.

Then go back to Hardware Drivers and download and activate the driver (use the latest version listed for your 9400). Reboot and you'll have 3D acceleration that will never need to be reinstalled.

Also, to the people trying to help: The 'sh' command will ONLY run shell scripts, NOT binary programs.

---

### Post by BAleR187 on 2010-01-08
> **3rdalbum said:**
> On Ubuntu, you typically don't install Nvidia or ATI drivers manually, because the process isn't user-friendly and the driver would need to be reinstalled every time you update the kernel.

Instead, we use the Hardware Drivers program to download and install the drivers. If you don't see anything listed in this program, then you need to go to Synaptic Package Manager and hit the Reload button so Ubuntu has an idea of what's available in the repositories.

Then go back to Hardware Drivers and download and activate the driver (use the latest version listed for your 9400). Reboot and you'll have 3D acceleration that will never need to be reinstalled.

Also, to the people trying to help: The 'sh' command will ONLY run shell scripts, NOT binary programs.


well thanks for the help, i know i could prolly do this way with ease, the only problem is im having trouble setting up my wireless usb adapter, which is this here, [http://www.pcrush.com/images/hi-res/112517.jpg](http://www.pcrush.com/images/hi-res/112517.jpg)

it doesnt find it eather and the only other way i could get internet, is through tethering my iphone so i think im prolly S-O-O-L for now. I guess the only way to get anything to work really is with a wired connection. which i dont have access to and nor will I for a while. thank you for all the help to everyone

---

