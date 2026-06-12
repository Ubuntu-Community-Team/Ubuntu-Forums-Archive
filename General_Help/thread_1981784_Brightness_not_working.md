---
title: "Brightness not working"
date: 2012-05-17
forum: General Help
---

### Post by neophyte02 on 2012-05-17
My laptop is acer 4752. The brightness key(Fn + up/down) is not working in ubuntu 12.04

What should I do to make it working?

---

### Post by neophyte02 on 2012-05-22
no reply yet? please someone help me to fix this

---

### Post by black veils on 2012-05-22
try using the relevant **Fn** keys, use as if you were making it be the darkest, then press once or twice as if you were making it lighter. restart the laptop and see if it made a difference.

---

### Post by neophyte02 on 2012-05-24
this made my laptop go deem forever. the brightness didn't worked after restart also. didn't worked. any other solution please

---

### Post by black veils on 2012-05-24
attempt B.
try pressing **Fn** key without holding, and then press relevant brightness keys. does a pop-up show on the screen?  if yes, then set to a low-medium brightness level and restart laptop.


attempt C.
1.  System Settings

2.  In the Hardware section, click Power Management.

3.  Adjust the **Set display brightness** slider to a comfortable value. check other brightness settings in power management. then restart laptop

[COLOR=Green][I]
**(need tech people to help if those dont work****)**[/I][/COLOR]

---

### Post by neophyte02 on 2012-05-24
try pressing Fn key without holding? i didn't understood. I tried but there's not any pop up screen.
I think both didn't worked. Now what should I do to fix it?

---

### Post by Toz on 2012-05-24
Try the following kernel parameters one at a time to see if they work (will need to reboot each time):

1. acpi_backlight=vendor
2. acpi_osi=Linux
3. acpi_osi=Linux acpi_backlight=vendor

To add the kernel parameter, follow these instructions:

1. Edit the configuration file:
```
gksudo /etc/default/grub
```

2. Add the parameter from above on the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** after the word splash but inside the last quote. Example:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

3. Save the file

4. Configure grub:
```
sudo update-grub
```

5. Reboot and test

---

### Post by black veils on 2012-05-24
> **neophyte02 said:**
> try pressing Fn key without holding? i didn't understood.

usually people press **Fn** key and keep their finger on it, keeping it pressed, and use the other hand to press the brightness keys.


sorry i cannot help more than this, you will have to wait for other replies.

---

### Post by neophyte02 on 2012-05-26
first I've to test like GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" 			 		

then in 2nd time I've to add  two lines like GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" 			 		
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash aacpi_osi=Linux" 			 		

or 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash aacpi_osi=Linux"  			 		only?
> **Toz said:**
> Try the following kernel parameters one at a time to see if they work (will need to reboot each time):

1. acpi_backlight=vendor
2. acpi_osi=Linux
3. acpi_osi=Linux acpi_backlight=vendor

To add the kernel parameter, follow these instructions:

1. Edit the configuration file:
```
gksudo /etc/default/grub
```2. Add the parameter from above on the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** after the word splash but inside the last quote. Example:


3. Save the file

4. Configure grub:
```
sudo update-grub
```5. Reboot and test

---

### Post by Toz on 2012-05-26
First test should be:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

Second test should be:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux" 

Third test should be:
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor" 

---

### Post by neophyte02 on 2012-05-27
the file can't be saved. isn't there any easy way to configure it?

---

### Post by Toz on 2012-05-29
> **neophyte02 said:**
> the file can't be saved. isn't there any easy way to configure it?

Make sure you start the editing with gksudo so that you have root access to the file. Like this:
```
gksudo gedit /etc/default/grub
```
...this will open the file for writing with root privledges.

---

### Post by waffen on 2012-07-19
I own a Acer Aspire 4752-6600 and the config #1 fix the problem with the brightness! thanks!

> **Toz said:**
> First test should be:


Second test should be:


Third test should be:

---

