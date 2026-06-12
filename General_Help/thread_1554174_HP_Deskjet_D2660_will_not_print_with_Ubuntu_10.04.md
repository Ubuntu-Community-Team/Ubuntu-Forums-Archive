---
title: "HP Deskjet D2660 will not print with Ubuntu 10.04"
date: 2010-08-16
forum: General Help
---

### Post by Miller7 on 2010-08-16
[SIZE=3]Hello everyone[/SIZE][SIZE=3]

[/SIZE]   [SIZE=3]I recently installed Ubuntu 10.04 on my computer. Everything works except for my HP Deskjet D2660 printer. The printer is recognized, but it will not print. HP-check shows no errors or warnings.  [/SIZE][SIZE=3]
[/SIZE]   [SIZE=3]The printer works fine on another computer with Ubuntu 9.10[/SIZE][SIZE=3]
[/SIZE]   [SIZE=3]Any ideas on what could be wrong?[/SIZE][SIZE=3]
[/SIZE]   [SIZE=3]Thanks for your attention.[/SIZE]

---

### Post by cloudscream on 2010-09-01
The current driver for HP D2600 series printers has **bugs** (the ones installed with Ubuntu Lucid 10.04 by default).
[https://bugs.launchpad.net/hplip/+bug/588081](https://bugs.launchpad.net/hplip/+bug/588081)

I'm also using HP Deskjet 2660. By using the following workaround, I got it to work normally again.

1. Install the package **hplip-cups** using Synaptic or Ubuntu Software Center.
2. Go to the **Main Menu**, **System**>**Administration**>**Printing**. **Right click on the printer icon**(HP-Deskjet-D2600-Series) and select **Properties**.
3. On **Settings**, **Make and Model**, click **Change...** (It will search for drivers, then the **Change Driver** window will appear)
4. **Choose Driver**, **Select printer from database**, **HP**. Click **Forward**.
5. From the list of **Models**, select **Deskjet d2600**. On the list of **Drivers**, select **HP Deskjet d2600 Series, [COLOR="Red"]hpcups[/COLOR] 3.10.2 [en]**. Click **Forward**.
6. Select anything from the options (Use the new PPD as is, or Try to copy option settings over...). Then click **Apply**.
7. Now Print a Test Page or something.

---

### Post by Jechem on 2010-10-21
I recently purchased this printer D2660 and had it working based on the instructions from above thread but now the when I print in color the letters that are supposed to be black are printed in brown. I tried it on grayscale an it printed in black ink. I've tried deleting the printer and installing it again. but the problem persists.

Any suggestions?

---

### Post by gengiskanhg on 2011-04-07
The solution continue to be valid for kernel: 2.6.32-30-generic und:
Ubuntu 10.04 LTS - the Lucid Lynx

Thanks and Regards. :)

---

### Post by elliotn on 2011-04-30
wow that helped thanks alot

---

### Post by Nobunaga on 2013-01-17
thanks cloudscream, that worked!

---

### Post by wlraider70 on 2013-03-08
if you are using a server edition or just like the CLI.

1. sudo apt-get install hplip-cups
2. go <server-ip>:631
      2.5 you may need to edit /etc/cups/cupsd.conf
      2.6 add "Allow All"
3. admin tab -> Add new printer
4. Select HP Deskjet d2600 Series, hpcups 3.10.2 [en]

---

