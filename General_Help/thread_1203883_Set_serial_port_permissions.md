---
title: "Set serial port permissions?"
date: 2009-07-03
forum: General Help
---

### Post by devin0 on 2009-07-03
I have started using linux to create programs for my basic stamp microcontroller. I belive I need to set permissions for my serial port but am unsure how. In the installation instructions I was told to run
ln -s ttyS0 bstamp but every time I restart the machine I need to re run that command to get things to work. What can I do to fix this? The install instructions I followed are here : [http://bstamp.sourceforge.net/install/](http://bstamp.sourceforge.net/install/)

---

### Post by kilowattradio on 2009-07-03
> **devin0 said:**
> I have started using linux to create programs for my basic stamp microcontroller. I belive I need to set permissions for my serial port but am unsure how. In the installation instructions I was told to run
ln -s ttyS0 bstamp but every time I restart the machine I need to re run that command to get things to work. What can I do to fix this? The install instructions I followed are here : [http://bstamp.sourceforge.net/install/](http://bstamp.sourceforge.net/install/)

```

ls -l /dev/ttyS0

```
See what group is associated with the device file and as long as the group has read write permissions just add your user id to that group in the Users and Groups utility in Ubuntu;s Adminstration menu. 
If you still can't get it to work you can add:
```

chmod 555 /dev/ttyS0 

```
in one of your start up scripts in /etc . 
As long as you don't have net access associated with that product there is a very small security issue.

---

### Post by devin0 on 2009-07-04
Where exactly in my startup scripts should I put that code? Im still having the problem of bstamp disappearing from /dev every time I restart.

---

### Post by kilowattradio on 2009-07-04
> **devin0 said:**
> Where exactly in my startup scripts should I put that code? Im still having the problem of bstamp disappearing from /dev every time I restart.

```

/etc/init.d/rc.local

```
Will do the job.

---

### Post by devin0 on 2009-07-04
OK thanks I think that that sorted out the permissions problem with the serial port. What can I do about my bstamp file disappearing every time I restart? Should I do something similar to what I just did and add a command to create the file to my startup scripts?

---

### Post by kilowattradio on 2009-07-04
> **devin0 said:**
> OK thanks I think that that sorted out the permissions problem with the serial port. What can I do about my bstamp file disappearing every time I restart? Should I do something similar to what I just did and add a command to create the file to my startup scripts?

If the bstamp device is created after you attach the device to the computer whatever script or file creates that file in /dev could be modified to make the link from ttys0 to bstamp. Otherwise you can write a script and run that after attaching the device. 
You could make a launcher in the desktop to run that script with a double click or add it to a menu.

```
xterm -e /path/to/script 


```
If the script needs root permissions use

```
gksu xterm -e /path/to/script 


```

Your best bet is to find whatever module that mounts the device to /dev/bstamp and see if it can or does run a script when mounting and put all your script commands in that file. A google search should help you find out.

---

### Post by txcrackers on 2009-07-04
Instead of attempting to over-ride HAL permissions on the device, just add the appropriate users to the "dialout" group via user management. Log out and log back in and you're done.

As for attaching the bstamp device to the ttyS* port, the above **may** solve that problem for you. If not, you might want to look into HAL/UDEV rules to appropriately set things up. While I personally have used scripts to hack around certain things, I've found that adhering to the manner in which devices are managed ends up working a whole lot better and less frustratingly.

---

### Post by devin0 on 2009-07-08
I have been looking around Trying to find a way to add bstamp to udev rules but haven't had any success. What should I change in the udev rules to make bstamp be there automatically?

---

