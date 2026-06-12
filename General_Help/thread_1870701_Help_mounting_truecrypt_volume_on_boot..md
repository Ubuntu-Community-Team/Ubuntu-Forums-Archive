---
title: "Help mounting truecrypt volume on boot."
date: 2011-10-27
forum: General Help
---

### Post by echo59 on 2011-10-27
Hey,

I've a dual-boot Windows 7 / Maverick system.  I've a seperate partition for documents, which is shared by both OSs.  Because of work I installed Truecrypt 7.1 in both OSs, so that I can encrypt my data.

My data partition is encrypted in Windows using truecrypt.  In Windows the device auto-mounts on boot and a dialog box appears prompting for my key.  My Dropbox folder is inside this partition, so I've a script that loads Dropbox after my device is mounted.

In Ubuntu I've my Documents / Music / Video etc folders mapped to inside my Truecrypt volume.

My question is, how do I do something similar in Ubuntu?  I have 2 parts to my question:
1) How do I automatically mount my Truecrypt device on booting into Ubuntu.  I want a prompt to type in my key and then for the device to be mounted automatically to /media/truecrypt1.  The ecrypted volume/device is held at /dev/sda5.

2) Can I delay Dropbox from starting at boot until the truecrypt1 device has been mounted?

I've browsed the forum and done google searches but things don't quite make sense to me, so I'd appreciate some basic help.


Thanks!

J

---

### Post by echo59 on 2011-11-02
OK, so I've figured out how to automount the TrueCrypt volume without having to enter an administrator password as well as the volume decryption key.  Here's what I've done so far....

1)Disable "Start Dropbox on system startup" (in Dropbox/Preferences)

2)Create a bash script at ~/.TrueCrypt called truecrypt_automount.sh  This file contains
```
#!/bin/sh
truecrypt --mount /dev/sdb1 /media/truecrypt1
```

3)Save the file

4)In a terminal type
```
cd .TrueCrypt
chmod 755 truecrypt_automount.sh
```

5)In System/Preferences/Startup Applications add a new startup called TrueCrypt with a command path of /home/jason/.TrueCrypt/truecrypt_automount.sh

6)Add TrueCrypt to the sudoers list so that it does not ask for an administrators password to run.  The instructions can be found at [http://newbiedoc.berlios.de/wiki/How_to_configure_Sudo_to_run_programs_as_a_different_user]("http://newbiedoc.berlios.de/wiki/How_to_configure_Sudo_to_run_programs_as_a_different_user")

Essentially:
6a)In a terminal type sudo visudo

6b)Add the following text to the section marked # User alias specification
```
User_Alias MAINTAINERS = chris
```
**Insert your own username instead of "chris"**

6c)Add the following text to the section marked # Cmnd alias specification
```
Cmnd_Alias DEB = /usr/sbin/synaptic, /usr/bin/aptitude, /usr/bin/apt-get
```

6d)Add the following text to the section marked # User privilege specification
```
root ALL=(ALL) ALL
MAINTAINERS ALL = DEB
```

6e)Add the following text to the end of the file
```
# Additional line to allow TrueCrypt to run as root
ALL ALL=NOPASSWD:/usr/bin/truecrypt
```

6f)Save the file (<Ctrl> X) as /etc/sudoers

Now when you reboot TrueCrypt should ask you for the password/keyphrase for your encrypted volume but should not ask you for an administrators password as well.

Now all I've got to do is figure out how to trigger Dropbox to start AFTER the TrueCrypt volume has been mounted!

---

### Post by echo59 on 2011-11-02
Next I'm looking for help from people familiar with bash scripting.
I need to add to the truecrypt_automount.sh script so that the script checks to see if the truecrypt volume is mounted to /mount/truecrypt1 and only starts Dropbox once this is mounted.  There is a batch script that works in Windows like this:
```
@echo off
rem Every second, check to see if volume is mounted
echo Waiting for volume...
:keepwaiting
ping -n 1 -w 1000 127.0.0.1 > nul
if not exist D:\ goto keepwaiting
start "Dropbox" "C:\Documents and Settings\YourUserName\Application Data\Dropbox\bin\Dropbox.exe"
```

I'd appreciate it if anyone who is familiar with bash could help me translate this script.

---

### Post by echo59 on 2011-11-03
Thanks to Vaphell for helping me with the bash script [http://ubuntuforums.org/showthread.php?t=1874351]("http://ubuntuforums.org/showthread.php?t=1874351")

My truecrypt_automount.sh now reads:
```
#!/bin/sh
truecrypt --mount /dev/sdb1 /media/truecrypt1
sleep 4

dbox_dir=/media/truecrypt1/Dropbox
while true
do
  if [ -d "$dbox_dir" ]
  then
    echo Dropbox folder is ready
    break
  else
    echo Dropbox folder not available
  fi
  sleep 2
done

echo DO DROPBOX STUFF HERE
dropbox start -i
```

My PC boots and after I log in I'm asked for the pass phrase for my TrueCrypt volume.  Once I enter this and the volume is mounted then Dropbox starts and synchronises.  Sweet!

---

