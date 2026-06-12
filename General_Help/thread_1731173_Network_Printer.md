---
title: "Network Printer"
date: 2011-04-16
forum: General Help
---

### Post by searchfgold6789 on 2011-04-16
Hi,
I remember it being really easy to add a printer attached to  another computer using Ubuntu, but I don't remember exactly what made it  so easy.. All I know is that now that I have switched to Kubuntu the  process has become much harder because now I have to find out some  special locations, numbers etc. for it to connect to the printer. It's  connected to a Windows XP machine on the other side of the house.
It  says alot about 'contacting the network administrator' if I am unsure  about what to put in. But I am more or less the network administrator!
Can  anyone recommend a good guide that says how to find out what numbers to  put in so that my Linux machine can connect and print to the Windows  machine? Or maybe someone knows a few commands to share?
My exact  trouble is, I go to Applications > Settings > System settings,  Printer configuration, New Printer, New Network printer, and then there  are a few options but I don't know which one to choose. Windows Printer  via Samba, I guess? Then in the box that says smb://[enter stuff here] I  need to put in info but I don't know how to find that info.
Thanks in advance,
 - search

---

### Post by jerome1232 on 2011-04-16
smb://ip address of machine with printer/printer name

---

### Post by searchfgold6789 on 2011-04-16
Ok, thanks for the quick reply... How do I find out what should go in 'printer name'?

---

### Post by jerome1232 on 2011-04-16
On my Windows 7 box you go to Control Panel -> Printers and Devices -> right click the printer, printer properties, click the sharing tab, and it's listed under printer name.

See screen shot. I'm sure it's somewhat similar under xp.

---

### Post by SeijiSensei on 2011-04-16
If you have the smbclient package installed, try this:

```
smbclient -L servername
```

If the printer is publicly visible, you'll see an entry like this:

```

Sharename       Type      Comment
8250            Printer   HP Photosmart 8200 series

```

If it's not publicly visible, but available to an account on the Windows machine for which you have the password, then use 

```
smbclient -U username -L servername
```

You'll be prompted for the password for "username".

I often talk directly to CUPS by browsing to [http://localhost:631/](http://localhost:631/) on the client machine and using that interface to add the printer.  You'll be prompted for your username and password if you choose a task that requires root privileges.

---

### Post by searchfgold6789 on 2011-04-17
Thank you both! This was exactly what I was looking for.
 - search

---

