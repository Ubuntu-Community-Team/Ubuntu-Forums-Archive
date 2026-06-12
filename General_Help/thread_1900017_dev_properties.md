---
title: "/dev properties"
date: 2011-12-25
forum: General Help
---

### Post by Cool Javelin on 2011-12-25
I have a data acquisition board located at port 0x300. It is called a DAC08. It has digital and analog inputs. I can access it via the port function in Pascal.

I don't believe it is showing up in /dev.

My fitst question, I need to run the program as root in order to access the port. Can I somenow tell Ubuntu to allow access to this address area to non root users?

My second question. This device does not show up when I run hardinfo. Is there some way I can make an entry in the /dev directory to make a manual connection between it and Ubuntu?

Thanks, Mark.

---

### Post by matt_symes on 2011-12-25
Hi

> **Cool Javelin said:**
> I have a data acquisition board located at port 0x300. It is called a DAC08. It has digital and analog inputs. I can access it via the port function in Pascal.

I don't believe it is showing up in /dev.

My fitst question, I need to run the program as root in order to access the port. Can I somenow tell Ubuntu to allow access to this address area to non root users?


I have no experience with that board but i would be looking at checking udev. It seems it not creating a device node for it. You can also change the permission of the node from udev using the MODE="666" rule.

> 
My second question. This device does not show up when I run hardinfo. Is there some way I can make an entry in the /dev directory to make a manual connection between it and Ubuntu?

Thanks, Mark.I don't think hardinfo is reading it because it can't find the device node. That is just supposition though as i am not in the least bit sure. 

The device is a PCI card ?

What's the output of

```
lspci
```If that does not show it use

```
sudo lshw
```Post back the results

Kind regards

---

### Post by Cool Javelin on 2011-12-25
Thanks matt_symes:

The board is not PCI, but ISA.

Neither lspci, nor lshw show anything about that board or address space.

There is a block of addresses starting at 300 hex. Each address is a controller of come kind, 2 for reading an a-d converter, one for an analog mux, 3 for digital IO, etc.

I will look into udev and post more info later.

Thanks, Mark.

---

### Post by matt_symes on 2011-12-25
Hi

An isa board ? It's an old device ?

The device is registered under sysfs (this is worth checking) ? If it is then get the sysfs path and use that to try to get info from udevadm.

I have to say, i am rather concerned that lshw is not recognizing it. If your just poking a memory location to operate it then i think you may have trouble creating a node for it. You wrote the driver yourself ?

Kind regards

---

### Post by Cool Javelin on 2011-12-26
Matt

Yes, it is an old ISA board and while I did not write a driver that Ubuntu knows about, it does know what registers do what on the board and accesses the board directly.

I don't know how Linux figures out what hardware is attached to a computer, I assume it looks troough a series of hardware ports during boot, then if it finds something it checks to see if it can match it to some kind of list.

I don't know enough about this process to understand how it works or what it dose if it can't figure out what the hardware is.

As far as sysfs, running that command at the prompt yields a command not found error.

I did a little research on Google and I am beginning to tread into territory I don't understand.

Mark.

---

### Post by matt_symes on 2011-12-26
Hi

To see if the device is listed under sysfs do something like

```
ls -l /sys/bus/isa
```

and check under devices.

Kind regards

---

### Post by Cool Javelin on 2011-12-27
Here it is, obviously, Ubuntu either doesn't find anything, or doesn't know what to do with what it does find.


```
mark@aserver:/sys/bus/isa$ ll -R
.:
total 0
drwxr-xr-x  4 root root    0 2011-12-26 21:23 ./
drwxr-xr-x 22 root root    0 2011-12-26 21:23 ../
drwxr-xr-x  2 root root    0 2011-12-26 21:23 devices/
drwxr-xr-x  2 root root    0 2011-12-26 21:23 drivers/
-rw-r--r--  1 root root 4096 2011-12-26 21:23 drivers_autoprobe
--w-------  1 root root 4096 2011-12-26 21:23 drivers_probe
--w-------  1 root root 4096 2011-12-26 21:23 uevent

./devices:
total 0
drwxr-xr-x 2 root root 0 2011-12-26 21:23 ./
drwxr-xr-x 4 root root 0 2011-12-26 21:23 ../

./drivers:
total 0
drwxr-xr-x 2 root root 0 2011-12-26 21:23 ./
drwxr-xr-x 4 root root 0 2011-12-26 21:23 ../
mark@aserver:/sys/bus/isa$
```

Thanks for all your help.

Mark.

---

