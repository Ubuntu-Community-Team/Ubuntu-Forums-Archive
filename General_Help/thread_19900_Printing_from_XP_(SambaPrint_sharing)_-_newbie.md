---
title: "Printing from XP (Samba/Print sharing) - newbie"
date: 2005-03-14
forum: General Help
---

### Post by alpen on 2005-03-14
Hello, I'm a complete ubuntu/unix/linux newbie.

I installed ubuntu on a laptop (which I wanna use as a printserver in a home windows network [all other PCs in the workgroup are running XP]). Configured the printer (Epson C62) & it prints fine when used locally.

Then I installed samba & smbfs. I made a few changes (which I didn't completely understand) to smb.conf (as instructed in ubuntuguide). The linux box can 'see' the XP boxes in the workgroup & they can 'see' the linux box. I could also see the printer from an XP box and configure it as a network printer & even managed to print to it. However, when I came back later to print, the XP app(s) from which I were trying to print continually hung.

So I decided to do a bit more research & totally reconfigure samba from scratch. I found a base smb.conf file for basic printing at samba.org & thought I'd use that as a start & then tweak it as I understood more. So this is what my smb.conf file looks like now (I've restarted samba using it):

[global]
workgroup = hpmwork
security = share
printcap name = cups
disable spoolss = Yes
show add printer wizard = No
printing = cups
[printers]
comment = All Printers
path = /var/spool/samba
guest ok = Yes
printable = Yes
use client driver = Yes
browseable = No

Now my situation is as follows: XP pc can see the printer on the linux box and I can configure the printer on the XP pc using the windows wizard. I can check the status of the printer from the XP pc and it all looks to be working fast and correctly. However, when I come to print, the iondows app indicates everything ok but the print job just disappears. I can print locally on the linux box without problems.

Any suggestions? Anything obviously wrong with my smb.conf file?
(I do realise this is potentially a windows problem & not a linux problem)

rgds
al

Edit:
-------------
ok, I found the problem. The directory /var/spool/samba did not exist. So I created it and then (as instructed by samba.org) gave it to the root user as follows:

chown root.root /var/spool/samba
chmod a+rw TX /var/spool/samba

The second command didn't work but printing now does!.

As an aside: would errors resulting from my mistakes above me logged anywhere? I looked thru the system log but couldn't find anything. Is there a good linux/gnome intro book someone could recommend as I've not really understood most of what I've done so far (though it eventually works).

al

---

### Post by kamstrup on 2005-03-14
I have never tried using samba or networked printers, but have always been curious about because I know that one day I'd have to figure it out :)

The TX in the chmod command looks out of place... Basically "chmod a+rw /var/spool/samba" would add read and write permissions for all to /var/spool/samba. Do a "man chmod" to read more about this.
"chown root.root /var/spool/samba" makes root the owner of /var/spool/samba, and also sets the group which it belongs to, to root. Look at "man chown" for details.

---

### Post by alpen on 2005-03-14
thanks for your response, Kamstrup.

Yes, it was the 'TX' that was objected to (however, that was a direct copy of a command from samba.org). I get the feeling that given the way ubuntu sets users up it was probably unnecessary to do the chown & chmod stuff anyway.

Either way, network printing is now working so I'm happy!

---

### Post by Happy on 2005-03-23
I followed the exact steps as alpen (thanks for the guide btw alpen)
but I can't tell if it worked because the windows machine is having trouble finding it's own network, let alone another =(
yet it connects to the router flawlessly

stupid windows.
no printing for my roommate it seems

---

### Post by Happy on 2005-03-24
hmm...
well my problem appears to stem from an incompatibility in windows XP SP2, it has the windows firewall enabled (roommate isn't computer savvy enough to be trusted with another brand of firewall), the initial problem was "file and print sharing" was blocked by the firewall (for local file/printer sharing as well  #-o )

After doing that I managed to install a windows driver for the computer and succesfully printed out a test page.
But when I tried printing out a pdf file from the windows machine it froze up on me.
the print dialog opened up and started freezing up the rest of the computer. stupid windows   :( 
anyway.
I'll post my smb.conf here and if anyone notices any glaring problems please let me know

> [global]
workgroup = workgroup
netbios name = box
security = share
printcap name = cups
disable spools= Yes
show add printer wizard = Yes
printing = cups

[printers]
comment = All Printers
path = /var/spool/samba
guest ok = Yes
printable = Yes
use client driver = Yes
browseable = Yes


Oh yes, There is another workgroup set up using SME server, the windows computer can not see that workgroup at all!
and it can only see this machine if it belongs in the same workgroup...

I read somewhere about setting the os level to 64 or something like that...
I have set up a 'pcguest' account and matched the usernames/passwords with linux and samba as described at [http://ubuntuguide.org/](http://ubuntuguide.org/)

Thanks

Edit: Windows sp2 suddenly started connecting to my ubuntu box no hassles, as well as the SME-server box I have.
Unfortunately it is still struggling to print.
I read that it may be due to it waiting from a response from an outgoing port 445 call and the only way to speed things up is to install a proper firewall (read non windows) to block outgoing ports...
this is a hassle

quote from [http://www.sixfiles.com/forum/download-windows-xp-network-printing-problems-5670.html](http://www.sixfiles.com/forum/download-windows-xp-network-printing-problems-5670.html)
> Hi,
since Win2000 and also in WinXP, when windows networking is bound to
TCPIP, the system tries a network connection to remote IP port 445, and
only if this fails, uses ports 137 to 139. As Win98 and WinME don't have
a port 445 open (and would not know how to handle those incoming network
packets to port 445), WinXP keeps trying for some time or number of
attempts. (I'd like to know where this is defined, because after update
with SP2, this takes forever.)
During these attempts, the printing process seems to be frozen.

So your problem may very well go away if you unbind file and printer
sharing from TCPIP on the WinXP machine. I would like to know whether
this helps.

I can't do this because NETBEUI is not supported on our LAN, but
astonishingly the freezing of the printing process also goes away if I
deny outgoing connections to remote port 445 in the firewall.
Now that's a dirty fix, because the system SHOULD use 445 when
connecting to other Win2K or WinXP machines, and I will allow 445
connections as soon as all other machines are upgraded to Win2K or
WinXP, but until then ... if only someone could tell me where to set the
connection timeout so that the freezing stops after that time 

yep, just followed the same procedure on a windows XP SP1 machine and it works FLAWLESSLY!
this is definately a windows XP SP2 issue.
bugger it, I'm going to hack my roomates computer to death until I get it working!
first step! Kerio Personal Firewall =P


Edit again:
well that didn't work...
KPF did nothing to help and apparently samba 3.07 (the version I have) listens to socket 445 anyway.
so I once again have no idea how to enable printing =(
any other bright ideas?

---

### Post by Happy on 2005-03-25
THANK YOU MICRO$OFT!
Never thought I would say that but I finally managed to find their network troubleshooting guide and it handles my situation perfectly!

[http://support.microsoft.com/?kbid=314073&#13](http://support.microsoft.com/?kbid=314073&#13)

> SMB-connected print server
SMB print servers allow workstations on the network to send print jobs directly to a print server without going through an intermediate computer or print server. This type of configuration does not support Point and Print.

To work around this issue, follow these steps to install the print driver locally and create a connection to the SMB print share:
1.	Click Start, click Run, type control.exe in the Open box, and then click Printers and Faxes.
2.	Double-click Add a printer, and then click Next.
3.	Click Local printer attached to this computer, and then click Next.
4.	Click Create a new port.
5.	In the Type box, click Local Port, and then click Next.
6.	Type the SMB share name. For example:
\\PrintServer\ShareName
7.	Continue the wizard and install the appropriate driver for the device.

---

