---
title: "How do i install vmware-tools in kubuntu ?"
date: 2006-02-12
forum: General Help
---

### Post by Programmer on 2006-02-12
Hello :-)
I'm running kubuntu inside a vmware machine.
After installing and configuring kubuntu to run properly, how do i install vmware-tools to enhance the performance of my kubuntu ?

---

### Post by gingermark on 2006-02-12
A quick google search led me to [this page](http://www.vmware.com/support/ws5/doc/ws_newguest_tools_linux.html).

I think the 2nd option would be best for Kubuntu, run Konsole to bring up a terminal emulator.

I know nothing about VMware, but hopefully that page will point you in the right direction.

---

### Post by Programmer on 2006-02-12
Thanks!

This package (vmware-tools) is very strange to me, i did the same operations inside my Gentoo Linux but it failed.
Here, it worked fine, althought I don't see much different in the performance.

Thank you for your help :-)

---

### Post by loser72555 on 2006-02-12
I as well run Ubuntu inside Windows (I also run Windows inside Kubuntu on another machine), using VM Ware.  All that was necessary for me to do was go to the VM tab on VMware and install the tools.

---

### Post by AntiGenX on 2006-02-12
vmware tools install will fail if you have a Xserver running. To get around this, I did the following:

Note: you need at least gcc and make running to get them run:
**sudo apt-get install make**
**sudo apt-get install gcc**

[LIST]
[*]Mount up the vmware.iso image included with vmware. and copy **vmware-linux-tools.tar.gz** installer to **/tmp** 
[*]logout of kde and log back in with a failsafe session.
[*]shutdown kdm **sudo /etc/init.d/kdm stop** (this will kill the Xserver and leave you at the console. At this point I had to hit **ALT-F1** to get a valid tty)
[*]**cd /tmp** and extract the vmware-linux-tools.tar.gz file **tar -xvzf vmware-linux-tools.tar.gz**
[*]**cd vmware-linux-tools/vmware-tools-distrib**
[*]run **sudo ./vmware-install.pl**
[*]Answer all of the questions. (The defaults will work fine but for the first question I always answer /usr/vmware/bin because that will install everything into /usr/vmware if you take the defaults on the rest of the questions. This keeps everything easy to find.)
[*]The installer will ask you if you want to run the configure script, say yes.
[*]restart kdm **sudo /etc/init.d/kdm start**
[/LIST]

NOTE: You will get an error message because one of the modules will fail to compile. This is due to the fact that you are using a newer version of GCC, it's not really a bid deal to me since it's the module that lets you drag and drop files between the host and guest OS and vice-versa. I prefer to just share folder in windows then in KDE you use "Run Command" and type \\HOSTNAME where HOSTNAME is the hostname of your windows machine or its IP. Otherwise you can try installing the version of GCC that it's looking for, but you're on your own there...

-Jonathan

edit: forgot to put sudo before /etc/init.d/kdm stop

---

### Post by Programmer on 2006-02-13
Well, not neccesserily!
I installed vmware tools from the konsole inside the kde, in the middle of the installation the kde got crazy, the screen turned off but after few seconds it returned to its previous state without losing any data, and the vmware tools was installed successfully.

Another thing, alt+f1 doesn't work inside the vmware. Someone knows why ?

---

### Post by A3sthetix on 2008-07-14
Thank you AntiGenX, your instructions worked for me the second try around.

The first try, I was downloading Evolution mail while trying to perform your instructions in Terminal. That was really bad judgment on my behalf. 

To anyone doing this, make sure you don't do anything but follow AntiGenX's instructions. I had to do a full reinstall of Kubuntu.

-A3

---

