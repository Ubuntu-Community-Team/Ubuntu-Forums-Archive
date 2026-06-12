---
title: "C Header file location"
date: 2006-06-19
forum: General Help
---

### Post by evandec on 2006-06-19
I am trying to get VMWare running on my computer. However when I configure it I get this message.

> 
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes] yes

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.


What can I do to resolve this. Where are my C header files?

---

### Post by llamakc on 2006-06-19
You could run this from a terminal:

apt-cache search `uname -r` | grep headers

and then apt-get install them or search for them in Aptitude|Synaptic.

---

### Post by llamakc on 2006-06-19
Or this to just go ahead and install them:

```

sudo apt-cache search `uname -r` | grep headers | awk '{print $1}' | sudo xargs apt-get install -y

```

---

### Post by llamakc on 2006-06-19
Sorry for the flood of posts, but I just realized that doesn't set the symlink in /usr/src.

I guess you'll have to also do:

```

sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux

```

That worked for me.

---

### Post by evandec on 2006-06-19
Did that and got this.

> 
evandec@dhcp56:~$
evandec@dhcp56:~$ apt-cache search `uname -r` | grep headers
linux-headers-2.6.15-23-686 - Linux kernel headers 2.6.15 on PPro/Celeron/PII/PI II/PIV SMP/UP
evandec@dhcp56:~$ udo apt-cache search `uname -r` | grep headers | awk '{print $ 1}' | sudo xargs apt-get install -y
bash: udo: command not found
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 92 not upgraded.
evandec@dhcp56:~$ sudo ln -s /usr/src/linux-headers-`uname -r` /usr/src/linux
ln: creating symbolic link `/usr/src/linux' to `/usr/src/linux-headers-2.6.15-23 -686': File exists
evandec@dhcp56:~$ cd ..
evandec@dhcp56:/home$ cd ..
evandec@dhcp56:/$ cd usr
evandec@dhcp56:/usr$ cd bin
evandec@dhcp56:/usr/bin$ ./vmware-config.pl
Please re-run this program as the super user.

Execution aborted.

evandec@dhcp56:/usr/bin$ sudo ./vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]


Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]
Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.


---

### Post by llamakc on 2006-06-19
When you cut-pasted you left the letter s off of sudo, so it never bothered to install the headers.

Also, if you already have a symlink at /usr/src/linux you need to check where it points, and whether or not you're running that kernel at this moment.

I use the Ubuntu kernel images and not a home-rolled one. I should have been clear and said so above.

You still need to install the linux-headers for your running kernel before trying that vmware config script.

---

