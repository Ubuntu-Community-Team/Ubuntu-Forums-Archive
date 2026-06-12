---
title: "Printer Trouble"
date: 2006-02-19
forum: General Help
---

### Post by pianoboy3333 on 2006-02-19
My computer won't connect to another's printer that is running XP. Here is my /etc/cups/printers.conf file:

# Printer configuration file for CUPS v1.1.23
# Written by cupsd on Sun Feb 19 21:44:24 2006
<DefaultPrinter LaserJet-1000>
Info LaserJet-1000
DeviceURI smb://john@KENDELL/hpLaser
State Idle
Accepting Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
</Printer>

Is there anything I'm missing? john is the username of my computer, KENDELL is the name of the computer that is hooked up to the printer, hpLaser is the sharename of the printer. Does the network name need to go somewhere? Am I missing something?

---

### Post by cilynx on 2006-02-20
I've never had much luck getting to SMB shared printers effectively from Linux.  However, I've had much success accessing CUPS IPP printers from Windows.  I know for fact (I own one) that the LaserJet-1000 works with Ubuntu / CUPS and that you can print with it from anything on the network as well.  The only hangup for installing this printer on Linux is that the printer is retarded and needs the firmware uploaded to it every time the printer and/or computer reboots.  Let me know if you need a copy of the firmware.

Good Luck

---

### Post by pianoboy3333 on 2006-02-20
I don't think it is so much that, the printer setup GUI won't detect any computers on the Windows network setup, and the computer that the printer is connected to is KENDELL, and 'ping KENDELL' in the terminal won't work. So something isn't setup right. Is there anything I need to do on the XP machine (that has the printer connected to it) to allow me to get the printer? The printer is checked for sharing, the share name is hpLaser.

---

### Post by soonindallas on 2006-02-20
utilities like ping do not use smb so you cannot refer to hosts by name, you need to use IP addresses.

try to follow this howto, except for the samba installation that I guess you have successfully done, and post back your results.

[http://www.ubuntuforums.org/showthread.php?t=32190](http://www.ubuntuforums.org/showthread.php?t=32190)

---

### Post by pianoboy3333 on 2006-02-20
It said that the XP computer with ipconfig was 192.168.1.101, but I could not ping it in ubuntu, the ubuntu Applications->System Tools->Network Tools said there was a 192.168.1.100 for wlan0 so when I pinged that it worked and the bellow was with the .100 IP.

There are three different foo2zjs drivers, someone told me to install another one 'cause the one that came with ubuntu was not completed or something.

The first original driver that came with ubuntu gave:

Unable to connect to SAMBA host, will retry in 60 seconds...DEBUG: 1 %%Trailer

After the 60 secs: Unable to connect to SAMBA host, will retry in 60 seconds...ERROR:  Connection failed with error NT_STATUS_UNSUCCESSFUL

Second foo2zjs driver I have: Printing: Unable to connect to SAMBA host, will retry in 60 seconds...foomatic-rip version $Revision: 3.43.2.11 $ running...

After 60: Printing: Unable to connect to SAMBA host, will retry in 60 seconds...DEBUG: 1 %%Trailer

Third foo2zjs driver: Printing: Unable to connect to SAMBA host, will retry in 60 seconds...foomatic-rip version $Revision: 3.43.2.11 $ running...

After 60 sec with the third: Printing: Unable to connect to SAMBA host, will retry in 60 seconds...ERROR:  Connection failed with error NT_STATUS_UNSUCCESSFUL

With the pmtozjs driver: Printing: Unable to connect to SAMBA host, will retry in 60 seconds...foomatic-rip version $Revision: 3.43.2.11 $ running...

After 60: Printing: Unable to connect to SAMBA host, will retry in 60 seconds...ERROR:  Connection failed with error NT_STATUS_UNSUCCESSFUL

Ok, now the three with 192.168.1.101 the IP address that the XP machine said it had:

1st: Printing: Connection failed with error NT_STATUS_UNSUCCESSFUL
2nd: Printing: Connection failed with error NT_STATUS_UNSUCCESSFUL
3rd: Printing: Connection failed with error NT_STATUS_UNSUCCESSFUL

with the pbmtozjs driver: Printing: Connection failed with error NT_STATUS_UNSUCCESSFUL

---

### Post by cilynx on 2006-02-20
Just a thought:  did you disable the default paranoid firewall on your XP box?  By default, some versions of XP don't allow any connections in at all.  This includes ping and SMB.  Beware that disabling the firewall is opening yourself up to other problems.

---

### Post by learning curve on 2006-02-20
Follow These instructions:

How to set up a Network Printer from Ubuntu to a Windows Machine

Make sure you have Samba installed.  You can get it using the Synaptics Package Manager.
Enable “Print Services for Unix” on Windows XP machine and share printer.  Right click on the printer and click on sharing and then click in the radio button that says share this printer. (I’m not actually sure that this is necessary, it might be a red herring…) read the 2nd from the bottom sentence.
When you add the printer in Ubuntu, 
1.Choose “Network Printer” and “Windows Printer (SMB)” 
2.put your Workgroup in the Host field usally it is MSHOME by default
3.Put “guest@<IPadress>/<printer>” in the Printer field (replacing <host> and <printer> with your host & printer names) 
So, for example,  your printer was called “LaserPrinter”, you would put guest@ipaddress/LaserPrinter.
You should not need a name and password for the Windows machine for this to work. 
You also have to go to Control Panel/add/remove programs and add a windows component to accept print services for UNIX.  Check the box Other Network and File Print Services click next  and it will install.  Reboot

to find the IP address on your windows machine go to RUN and type in cmd/hit enter/when the dos window opens type in ipconfig and hit enter.  you should now see your IP address as xxx.xxx.xxx.xxx

Hope this is easy to follow and works for you.  It works great for me.:cool:

---

### Post by soonindallas on 2006-02-21
[QUOTE=cilynx]Just a thought:  did you disable the default paranoid firewall on your XP box?  By default, some versions of XP don't allow any connections in at all.  This includes ping and SMB.  Beware that disabling the firewall is opening yourself up to other problems.[/QUOTE]

it's not necessary to open the firewall completely.  in XP, go to control panel>windows firewall; if the firewall is enabled (recommended), check "file and printer sharing" on the exceptions tab.

it does sound like this is a networking problem affecting connection to your printer rather than a printer problem.

you might want to check out this thread: [http://www.ubuntuforums.org/showthread.php?t=59552](http://www.ubuntuforums.org/showthread.php?t=59552)
I had a similar problem some time ago and got it fixed thanks to the community.

if you make change changes to smb.conf you need to restart samba services so that the new configuration gets loaded:

```
/etc/init.d/samba restart
```

---

### Post by hobbes_opus on 2006-02-23
I was going to post this as a new thread, but thought you all seemed to be on a good track here.  I'm certainly a newbie too, but can add something maybe useful - at home, Hoary Hedgehog seemed to print easily onto a window's workstation's shared printer.  Can't get a peep out of the Breezy Badger version.  Does that make sense to anyone, or give any hints to the moderators & experts out there to help the rest of us (Breezy Badger is great but can't use it w/o sharing printers on windows machines).

Thanks,
Bob

---

