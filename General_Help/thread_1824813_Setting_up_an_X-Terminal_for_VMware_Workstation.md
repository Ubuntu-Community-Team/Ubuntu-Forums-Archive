---
title: "Setting up an X-Terminal for VMware Workstation"
date: 2011-08-14
forum: General Help
---

### Post by Kissell on 2011-08-14
I need VMware workstation to auto-start everytime I turn on an Ubuntu machine.  

I was able to solve this problem by using /etc/rc.local to set the permissions of the network adapter into promiscuous mode again after a reboot.  NOTE: This must be done in rc.local because it requires sudo privledges, otherwise you'll have to enter a password every time you reboot.
> 
chmod a+rw /dev/vmnet0
exit 0


Then running a bash script in startup applications like this:
> 
#!/bin/bash
vmware --power-on "/vmware/ESX/image.vmx" &


Now, that's great...  I can have the hypervisor running as a virtual machine upon unattended reboot of this linux box.  

The only remaining tiny problem is that when VMware Workstation does run and power-on this virtual machine, it opens full screen in gnome.  Then I click the X button to close the window (and VMware is setup to continue running powered-on virtual machines even when you close the window).

I would like to somehow automate this window closure, after VMware opens I want to close the window...  or at least minimize the window...  but I haven't see any way to do that.  But, there is a command line switch to start the program in a different X-Terminal.  Unfortunately, when I do that, it runs then shuts down, presumably because no X-terminal of that number really exists. 

I don't know much about X-terminals..  but ideally I could create a 2nd user interface behind the one I see on the screen, and open VMware in it, so that I never have to see it, yet it is always opened everytime I reboot.

---

### Post by Kissell on 2011-08-14
Well, I found a solution that works for me in this other thread.
[http://ubuntuforums.org/showthread.php?t=1619743]("http://ubuntuforums.org/showthread.php?t=1619743")

They use an app from the repository called "wmctrl" to minimize all windows.  This works really well with Unity, because minimized windows don't take up any additional space on the application bar, they just have an arrow next to them to indicate that app is open.  This way my desktop boots clean without these startup application programs open.  Very nice.  

I hated Unity Desktop when I first started using it, but its really growing on me.

---

### Post by nits143 on 2011-08-14
hello sir I'm new user of ubuntu...
can you help me to use c language in ubuntu..???

please reply..

---

### Post by Kissell on 2011-08-14
We try to keep each thread on a single topic.

Post your specific question in the General Help forum and I'm sure someone will be glad to help you.

---

