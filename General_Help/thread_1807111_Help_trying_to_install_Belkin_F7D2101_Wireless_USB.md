---
title: "Help trying to install Belkin F7D2101 Wireless USB"
date: 2011-07-18
forum: General Help
---

### Post by seandd29851 on 2011-07-18
Epic Ubuntu Noob, need help installing my wireless belkin adapter F7D2101 

ID 050d:845a Belkin Components 

I've just installed Ubuntu 10.10 since I couldn't get 11.04 to work and all I've done with it was follow these steps from:  

[http://www.ehow.com/how_8598699_install-belkin-f7d2101-ubuntu.html](http://www.ehow.com/how_8598699_install-belkin-f7d2101-ubuntu.html)

        1

        Click "Dash," "More Apps," "Accessories" and "Terminal" to open the terminal in Ubuntu.
        2

        Type "sudo gedit /etc/udev/rules.d/network_drivers.rules" to open the network driver's rules script in the text editor. Add "ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="845a", RUN+="/sbin/modprobe -qba r8192s_usb"" anywhere in the text. Click "File" and "Save," then close "gedit."
        3

        Type "sudo gedit /etc/modprobe.d/network_drivers.conf" to edit the network driver's configuration script. Add the line; "install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 845a" > /sys/bus/usb/drivers/rtl819xU/new_id" anywhere in the file. Save and close "gedit" again.
        4

        Navigate to Debian firmware download page and download the latest revision to your system (see Resources). Type "sudo mkdir /lib/firmware/RTL8192SU" into the terminal. Type "cp rtl8192su.bin /lib/firmware/RTL8192SU/" to copy the file to the needed directory.
        5

        Plug in the Belkin F7D2101, Ubuntu can now recognize it.


On Step 4, I'm guessing that you have to be connected to the internet for it so I switched to Win 7 and searched it up and downloaded rtl8192sfw.bin and didn't figure out how to install it after finding out how to chmod it and whatever, it still didn't work. I've got to the point where it shows Wireless Disconnected in the networking tab, but I tried to connect to a hidden wireless network. I've done everything I should there but it didn't connect. Any help is much appreciated, thanks.

---

### Post by thefasterblueone on 2011-07-18
I don't think you need to chmod it, just put it in the directory like the tut says.

Here is another post that might help.
[http://ubuntuforums.org/showthread.php?p=9759011]("http://ubuntuforums.org/showthread.php?p=9759011")

---

### Post by seandd29851 on 2011-07-18
thanks I had to figure out how to do that... gksudo nautilus ... worked not very good with commands right now but thanks for the help.

---

