---
title: "General question about installing on Ubuntu."
date: 2009-12-03
forum: General Help
---

### Post by bns1968 on 2009-12-03
The biggest issue I have aside from being a newbie who has yet to even pick up a book is on installing. I have this on a VMWare workstation. I am trying to install the VMare tools and the CD Mounts and it is displayed on the desktop, I open a terminal and the fun begins. First, I try install using 
1. su or sudo as the commands, su authentication fails and when I in sudo I get a LOT of switch information none of which I am familiar with.
2. When I try to run it, I change the directory, and see the files I want are listed in red, problems with permissions, I can't change the folder, because I am not the owner.
3. I don't KNOW the password for root or any other user because I was never prompted for it on installation, so I have no admin rights, and I can't change something without the information and credentials I need to change it.
4. When I tried to run the .RPM file it tells me to run "Debian" I am not familiar with Debian at all.
5. When I run it any other way, there is a permission issue.
6. Why can't I use "root" or even have been prompted for a password for "root" is there a default password?
7. If I am the person who installed Ubuntu, why don't I have admin rights by default?

How do I know what to use for the installation?
I know I can dig and search all of this and I know that this is a lot of detail, but I really would like information on what to do to get this up and running, I am sure it is not too difficult for you seasoned pros, but I am very very in the dark here and would appreciate any light you can shed on this.
Help please!!!
Thank you...

---

### Post by marshmallow1304 on 2009-12-03
In Ubuntu, the root password is not enabled by default for security reasons.  You can execute a single command with root powers by prefixing the command with
```
sudo 
```
The sudo password is your own, assuming you are an administrator (if you are the only user, you almost certainly are).
If you must work as root or prefer to do so, you can use
```
sudo su
```
or
```
sudo -i
```
When finished, you can use
```
exit
```
to return to your regular user.


.rpm is used by some other distributions, but not Ubuntu.  If you can find a .deb, that's the one you want.

---

### Post by lackoblacko on 2009-12-03
to install vmware tools first copy the VMWaretools package to a directory.  the sudo password is your user account password.
```

sudo cp /media/cdrom/VMwareTools*.tar.gz ~/Desktop

```
next extract the tools package
```

tar xvf VMwareTools*.tar.gz

```
now go into the the directory and run the install script
```

cd ~/Desktop/vmware-tools-distrib
sudo ./vmware-install.pl

```

---

### Post by bns1968 on 2009-12-04
> **lackoblacko said:**
> to install vmware tools first copy the VMWaretools package to a directory.  the sudo password is your user account password.
```

sudo cp /media/cdrom/VMwareTools*.tar.gz ~/Desktop

```next extract the tools package
```

tar xvf VMwareTools*.tar.gz

```now go into the the directory and run the install script
```

cd ~/Desktop/vmware-tools-distrib
sudo ./vmware-install.pl

```

The first command runs and extracts....
This is what happens when I run the 2nd command

tar: VMwareTools*.tar.gz: cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by lackoblacko on 2009-12-04
you have to change directory to where you copied the tar.gz file or specify the file location. try typing
```

tar xvf ~/Desktop/VMwareTools*.tar.gz

```
instead

---

