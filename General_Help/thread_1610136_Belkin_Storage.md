---
title: "Belkin Storage"
date: 2010-10-31
forum: General Help
---

### Post by paulridley on 2010-10-31
Hope you can help.

Running Kubuntu on a laptop and desktop, wirelessly and wired respectivly.

Connect to a Belkin Router [COLOR=#000000][FONT=Times New Roman][FONT=Verdana]F5D8635-4v1.  

This device has a USB port to allow a External drive to be used throughout the network for storage / sharing.
Conncection is via //192.168.2.1/san in a MS environment.

How do i connect to this device to RRX files on this device in ubuntu.  

Thanks

Paul
[/FONT][/FONT][/COLOR]

---

### Post by btindie on 2010-10-31
Take a look at page 28 of the [manual]("http://www.belkin.com/uk/support/article/?lid=enu&pid=f5d8635uk4a&aid=14356&scid=0"). The USB device is accessible via SAMBA, you connect to it as you would any windows computer. Launch nautilus then click on Network, select "Windows Network" and the name of your device should appear in the list. Or, if that's the correct IP address of your device enter the following in the address bar
```
smb://192.168.2.1/
```
The share name depends on the devicename assigned to the storage device, but it should be listed when you connect to the host.

It looks like this device is using an embedded Linux so you can always add NFS support if it doesn't already have it.

---

### Post by paulridley on 2010-11-01
thanks for your help.

Unfortunately that has not resolved the problem.  I installed Nautilus, but the application does not come up under applications or places.  A quick check on the net, and it seems other people may also be having problems with Nautilus and Xubuntu?

Is there a way to connect via a terminal screen? or have you any other suggestions.  

Belkin of course don't support Linux despite the fact thats what they build on!

---

### Post by btindie on 2010-11-02
Nautilus is more of a gnome program and it needs additional packages to be able to browse samba shares. From what I've read under Xubuntu, Thunar the file manager doesn't support samba shares so you have to do it from the terminal.
 
Take a look at the following pages and you should be able to mount your remote hard disk
 
[http://musante.i.ph/blogs/musante/2010/01/13/mounting-a-permanent-samba-share/](http://musante.i.ph/blogs/musante/2010/01/13/mounting-a-permanent-samba-share/)
[http://www.sirnet.co.uk/archives/114](http://www.sirnet.co.uk/archives/114)
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
[http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-remote-windows-partition-windows-share-under-linux.html)

---

