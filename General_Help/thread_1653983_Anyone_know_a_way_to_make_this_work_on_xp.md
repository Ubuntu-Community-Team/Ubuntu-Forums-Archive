---
title: "Anyone know a way to make this work on xp"
date: 2010-12-27
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2010-12-27
My dad has a router/modem and his computer plugined in to it
there is then a wire running to my room into my router 
in my room i have a wii, laptop, and a desktop
I have my router forwarding the printing ports for my shared printer to the desktop
If I connect my ubuntu laptop to the the modum/router in his room i can print via my router however his xp desktop will not find the printer so there is a working connection and xp will not use it and as muck as i would love to upgrade his computer to ubuntu has has a very unhealthy addiction to AOL so does anyone know a way to make xp use the connection
smb://192.168.1.2/hp_psc_2400
192.168.1.1 = router/modem
192.168.1.2 = my router (WAN)
192.168.1.100 = dad's xp comnputer (DHCP)
10.0.0.1 = my router (LAN)
10.0.0.50 = xp with shared printer
10.0.0.75 = my ubuntu laptop
edit:
changed my desktop to use xubuntu and made  print server/scanner/server out of it

---

### Post by no2498 on 2010-12-27
im no guru in any way
but from your side/room did you allow your dad's computer
it is a two way street now

just pointing

hope it makes you think of the way

---

### Post by pqwoerituytrueiwoq on 2010-12-27
if i boot a live ubuntu cd cd/usb i can print from if all i have to do is search from a printer under 192.168.1.2
i am going to try to get him to use xubuntu
just tryed the 173 nvidia driver on the upgraded car he has yet to let me put in the box and i could not login after installing trying the 195 now

---

### Post by efflandt on 2010-12-27
Windows file/printer sharing is a broadcast protocol (netbios) that does not see Windows PC's in other networks (past a router) unless you specifically address them by their IP address, (with proper ports forwarded) or you have a Windows server or samba doing WINS (and Windows PC's pointed at the WINS server in network settings).

I think there is something you can optionally install in Windows (I think somewhere in add/remove programs related to Windows setup) that are unix tools that include an lpr/lpd type server.  If you can find that in Windows and install it on the computer with the printer, you could then configure his computer to do lpr/lpd type printing.

To do that in add printers, set up a new "local" port for TCP printing to the WAN IP address of your router (with port 515 forwarded to the PC with printer).  Although, I am not sure what you call the print queue, because I have not done the server end of that.  Then it is just a matter of selecting a printer driver that works (many printers are backwards compatible with older, similar drivers).

But I have done lpr/lpd type printing from WinNT and WinXP by configuring the local TCP port, and even Win98 with a shareware program.

---

