---
title: "Remote desktop"
date: 2006-05-01
forum: General Help
---

### Post by g77s80 on 2006-05-01
how can I configure Ubuntu/Kubuntu to remote desktop winXP/Win2k workstations?

---

### Post by nanotube on 2006-05-01
use vnc
look at the tightvnc program (tightvnc.com) to get windows, and you can get one for ubuntu from the repos.

---

### Post by aysiu on 2006-05-01
You want to be able to control the Windows desktop from Ubuntu...?
Or control Ubuntu desktop from Windows...?

---

### Post by g77s80 on 2006-05-01
I'd like to control a windows desktop from Ubuntu

---

### Post by Beergrenade on 2006-05-01
I'd like to be able to do the opposite (control a Linux box from a Windows box) as well as control a Linux box from another Linux box.  I've got VNC installed already, but have run into trouble getting the two computers to talk to each other.

---

### Post by Beergrenade on 2006-05-01
Ok...I was able to connect from Linux box to Linux box by going to the console and typing "vncviewer 192.168.XXX.XXX:0".  Now I need to get it so it will work with the hostname instead of IP address.  Ideas?

---

### Post by nanotube on 2006-05-01
if your ip addresses are static, you can put entries in your /etc/hosts file for those ip addresses.

---

### Post by zad on 2006-05-01
or see if there is a version of dns2go or such like which will give you a name ie zad.dns2go.net or somat like that so if the ip changes it will still mirror it. :)

zad

---

### Post by cwaldbieser on 2006-05-02
[QUOTE=g77s80]I'd like to control a windows desktop from Ubuntu[/QUOTE]
Use the rdesktop program.  It is very similar to the remote desktop client you find in XP/2K3.

---

### Post by Al3xanR0 on 2006-05-03
[QUOTE=g77s80]how can I configure Ubuntu/Kubuntu to remote desktop winXP/Win2k workstations?[/QUOTE]

here is how I do it ```
rdesktop -a 24bpp -g 1010x645 -x l -r sound:remote <hostname or ip>:3389
```

here is an explaination of the above line -a =color depth -g=geometry -x=experience l=lan -r=device redirection (sound:remote obviously plays sound on the xp box) 3389= terminal services port number.

Need more info? Then do ```
man rdesktop
```

If you use remote desktop as often as I do you may want to go to your desktop (or where ever you have all of your application launchers) right click-> click creat new-> Link to application-> place that line in the :command field on the application tab.

---

### Post by Al3xanR0 on 2006-05-03
Opps I almost forgot you need to have terminal services running on either of your Windows boxes and obviously Rdesktop must be installed on your Ubuntu machine. Hope that helps.

---

