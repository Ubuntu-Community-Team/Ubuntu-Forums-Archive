---
title: "Connect to Winxp Printer"
date: 2012-08-20
forum: General Help
---

### Post by ksanger on 2012-08-20
I'm running Ubuntu 12.04.  I have two printers on my WinXP box that are shared.  I would like to map to it from Ubuntu.  

If I select the gear in the upper right hand corner, then printers, then Add, Windows Printer via Samba, Browse, I get WORKGROUP and my Winxp Computer listed.  However it does not show either of the two shared printers on the Winxp computer.

If I click the right facing triangle it goes out and hangs.  

If on the window labelled New Printer I set authentication details now and enter my Winxp login and password then Browse still hangs.

If instead I select Find Network Printer and type in the name of my WinXP Host and hit Browse I get Searching ...  with no error message.  

If I type in Workgroup/ComputerName and enter the verification details then hit verify I get an error Print Share Inaccessible.

---

### Post by davidvandoren on 2012-08-20
you have to open port 631

```
sudo ufw allow 631
```

---

### Post by wetland on 2012-08-20
Setting up printing to windows can be a bit of a pain... done it many times.

Check this [link]("http://askubuntu.com/questions/153517/ubuntu-12-04-network-printing-through-windows-samba-server") out / all the way at the bottom.

---

### Post by Jerry N on 2012-08-20
> **davidvandoren said:**
> you have to open port 631

```
sudo ufw allow 631
```

I have installed a Windows connected printer many many times over the last 5 years in various versions of Ubuntu and its derivatives and I have never had to explicitly open port 631.  Maybe I am missing something. 

Jerry

---

