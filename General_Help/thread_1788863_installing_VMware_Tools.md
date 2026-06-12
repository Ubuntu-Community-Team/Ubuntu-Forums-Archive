---
title: "installing VMware Tools"
date: 2011-06-23
forum: General Help
---

### Post by tomearp on 2011-06-23
Sorry, not sure if this is the right place to post, couldn't see anything obviously to do with running Ubuntu inside a VM....
 
I'm running VMWare Workstation 6.5.5 build-328052 in Windows 7 Professional 64-bit Service Pack 1.
 
I have installed Ubuntu 11.04 and am having trouble getting VMWare tools to install/run. I installed it through the software center (open-vm-tools).
 
If I try to run either VMWare Toolbox from Applications > Accessories, or VMWare User Agent from Applications > Other, then nothing happens.
 
If i open a terminal and try to run vmware-toolbox I get the following:
 
telescope@telescope-VM:~$ vmware toolbox
** Message: HOSTINFO: CPUID hypervisor bit is set, but no hypervisor vendor signature is present
 
** (process:2125): DEBUG: VmCheck_IsVirtualWorld: detected non-VMware hypervisor ().
 
 
** (process:2125): WARNING **: The VMware Toolbox must be run inside a virtual machine.
 
It definitely is running inside a virtual machine... anyone have any thoughts?

---

### Post by tomearp on 2011-06-23
Managed to answer my own question....sort of
 
I decided to have a go at manually building VMWare tools from the "Install VMWare tools" option in Workstation.... (how hard could it possibly be? :lol:)
 
before you start...
 
*sudo apt-get install build-essentials*
*sudo apt-get install linux-headers-`uname -r`*
 
(these should already be installed anyway)
 
the kernel source probably won't be, but we'll need it later so...
 
*sudo apt-get install linux-source-2.6.38* (install the appropriate version if yours is different. N.B. this may be a rather large download)
 
 
first you need to mod the version.h file or the install script will throw a wobbly
 
*cd /usr/src/linux-headers-`uname -r`/include/linux*
*sudo gedit version.h* (or use whatever editor you're comfortable with)
 
add the line 
 
#define UTS_RELEASE "2.6.38-8-generic" 
(if your uname -r is different...change accordingly)
 
save and close
 
now copy the autoconf.h file or the install script will throw a wobbly
 
*sudo cp ../generated/autoconf.h autoconf.h* (assuming you haven't cd'd)
 
now create a symlink so that the install script can easily find the headers
 
*cd /usr/src*
*sudo ln -s linux-headers-`uname -r` linux*
 
verify with *ls -al* if you can be bothered....
 
 
now we're just about ready to run the installer...so find the Install VMWare Tools option in Workstation and it'll mount the "cd"
 
mine appeared in /media/VMware Tools
 
*cp /media/VMware\ Tools/*.gz /tmp/*
*cd /tmp*
*tar zxvf VMwareTools-7.8.8-328052.tar.gz* (your filename may differ)
 
now we can run the install script
 
*cd /tmp/vmware-tools-distrib*
*sudo ./vmware-install.pl*
 
accept the defaults...it will eventually offer to run the first-time configuration script...say yes
 
now if the modules are deemed inappropriate for your system it will build them, keep selecting the defaults when it asks something.
 
my build of the vmhgfs, vmxnet, vmci modules failed... the others worked tho
 
i chose not to enable the experimental vmsync driver as i didn't feel the need for that feature
 
Restart the system....
 
It works....ish, obviously not all the features will be there as some of the modules failed to build, for me anyway. But the feature I wanted the most, auto resizing of guest resolution, seems to work nicely.
 
 
If anyone has suggestions on how to make the other modules build, I'd be more than happy to hear them!

---

### Post by tomearp on 2011-06-25
forgot to add....
 
Make sure to add the following to your Startup Applications
 
*/usr/bin/vmware-user*

---

