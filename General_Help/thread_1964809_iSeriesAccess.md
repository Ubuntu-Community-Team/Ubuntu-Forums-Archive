---
title: "iSeriesAccess"
date: 2012-04-24
forum: General Help
---

### Post by gypsumwolf on 2012-04-24
I successfully have this working correctly, except one thing.

When a user is using iSeriesAccess every once in a while it will say it lost its connection and resets back to the login screen. This is very annoying. Any ideas?

**Specific Software: iSeriesAccess-5.4.0-1.6.i386.rpm on Lubuntu 11.10 32-bit**

> 
+++++++++++++++++++++++WHAT I DID+++++++++++++++++++++++++++

Instructions on how to make a lightweight Linux terminal for the AS400.

-

Specific model: ASUS EB1007

Note: Some scripts I (name) provided, you just need to copy them to the correct location.

-
Index

1...........ASUS EB1007 Booting from USB

2...........HOW TO BUILD THE SYSTEM

3...........A few BASH commands you may want to reference

4...........Fixing APT GPG errors


======================================================
======================================================
1. ASUS EB1007 Booting from USB
======================================================
======================================================

1. On boot, hit the F2 key.

2. Once you are in BIOS, go to the BOOT section.

3. Select 'Hard Disk Drives'.

4. In the hard drives list, move the USB device to the top of the list.

5. Save and exit BIOS (F10).

======================================================
======================================================
2. HOW TO BUILD THE SYSTEM
======================================================
======================================================

NOTE: Anytime you see "$" infont of text it is a bash command, run in terminal.

NOTE: Do steps 1 - 13 on outside line; Do steps 15 - 17 on inside line. (Outside line is for skipping watchguard filter).

1. Install Lubuntu for i386. 

	*Use (all lowercase) "administrator" as username, for the password use the default.
	*Set administrator to login automatically.

2. $sudo -i

3. $apt-get update && apt-get upgrade

4. Change hostname by editing both files: 
$nano /etc/hosts
$nano /etc/hostname

5. $apt-get install likewise-open openssh-server docker numlockx alien libmotif4 libxaw7 libstdc++5

6. $nano /etc/lxdm/default.conf
Comment out (using "#") "session=/usr/bin/startlubuntu
add: "session=/usr/bin/openbox-session"

7. Copy scripts folder from "\\dir\dir\dir\Linux\Asus Neo Replacements" and place the folder in "/home/administrator" on the ASUS.

8. Copy "\\dir\dir\dir\Linux\Asus Neo Replacements\iSeriesAccess-5.4.0-1.6.i386.rpm" and place the file in "/home/administrator" on the ASUS.

9. Copy files in the openbox folder from "\\dir\dir\dir\Linux\Asus Neo Replacements\openbox" and place the files in "/etc/xdg/openbox/" on the ASUS & overwrite if asked.

10. On ASUS, $chmod a+x /home/administrator/scripts/*

11. reboot. ($shutdown -r now).

12. $alien -i iSeriesAccess-5.4.0-1.6.i386.rpm -cv

13. Run all these in terminal:

ln -sf /usr/lib/libXm.so.4 /usr/lib/libXm.so.3
ln -s /opt/ibm/iSeriesAccess/lib/libcwbcore.so /usr/lib/libcwbcore.so
ln -s /opt/ibm/iSeriesAccess/lib/libcwbodbc.so /usr/lib/libcwbodbc.so
ln -s /opt/ibm/iSeriesAccess/lib/libcwbodbcs.so /usr/lib/libcwbodbcs.so
ln -s /opt/ibm/iSeriesAccess/lib/libcwbrc.so /usr/lib/libcwbrc.so
locale-gen en_US

----
NOTE: To run the program: (include full path)
/opt/ibm/iSeriesAccess/bin/ibm5250 -LANGID en_us (Enter
Host name here.) -DISPLAY_NAME (Display name)
----

14. reboot & switch to inside line.

15. $domainjoin-cli join domain.com username

(If errors then retry and type password correctly, or the hostname is already used.)

16. Add static information to nm-applet in upper left corner of screen.

IP= xx.xx.xx.xx
Subnet= xx.xx.xx.xx
Gateway= xx.xx.xx.xx
DNS= xx.xx.xx.xx, xx.xx.xx.xx

17. Reboot & Test. While testing iSeriesAccess, change the keyboard mapping for the numberpad "+" to "FieldExit()".

18. Deploy.

======================================================
======================================================
3. A few BASH commands you may want to reference:
======================================================
======================================================

sudo -i (for root prompt)

sudo shutdown -h now (shutdown computer now)

sudo reboot (restart computer now)

nano (text editor, more simple than vi)

pkill (kill process)

chromium-browser (if you need to enter mobile + mobile for watchguard)

ifconfig (like MS Windows ipconfig)

---> Need more? Use Google or ask me.

======================================================
======================================================
4. Fixing APT GPG errors:
======================================================
======================================================

1. Open a terminal and try ALL of these commands.

	sudo -i
	apt-get clean
	cd /var/lib/apt
	mv lists lists.old
	mkdir -p lists/partial
	apt-get clean
	apt-get update

2. If it does not work, Google it.

---

### Post by gypsumwolf on 2012-04-25
<bump>

---

