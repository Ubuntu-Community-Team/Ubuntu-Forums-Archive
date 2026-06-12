---
title: "Install VMware tools"
date: 2011-11-14
forum: General Help
---

### Post by oldtraveler on 2011-11-14
Trying to install VMware tools I get to "VMwareTools-8.8.0-471268.tar.gz" but when I try to extract the files I get "You don't have the right permissions to extract archives in the folder "file:///media/VMware%20Tools"

I assume I need to do a sudo command, but I can't find any syntax that will work.

Suggestions?

---

### Post by 2F4U on 2011-11-14
Why don't you extract in another folder?

---

### Post by oldtraveler on 2011-11-14
How? That's the folder that contains the tar file.

---

### Post by e79 on 2011-11-14
Unpack the .tar file using this command (it shouldn't need sudo to unpack it but I will add it anyway)

```
sudo tar -zxvf VMwareTools-8.8.0-471268.tar.gz
```

Then change directory into the newly created folder (something like):

```
cd vmwareTools-8.8.0-471268
```

And finally lauch the installer (something like this again):

```
sudo ./vmwaretools-install.pl
```

hope this helps

---

### Post by oldtraveler on 2011-11-14
In your first code above it shows an error as follows:

phil@ubuntu:~$ sudo tar -zxvf VMwareTools-8.8.0-471268.tar.gz
[sudo] password for phil: 
tar (child): VMwareTools-8.8.0-471268.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

P.S.  I did manage to drag the tar.gz file to my desktop.

P.P.S.  The "vmwaretools-install.pl" file is located at /home/phil/Desktop/vmware-tools-distrib

---

### Post by e79 on 2011-11-14
then simply type

```
sudo sh /home/phil/Desktop/vmware-tools-distrib/vmwaretools-install.pl
```

or

```

cd /home/phil/Desktop/vmware-tools-distrib/
sudo ./vmwaretools-install.pl

```

---

