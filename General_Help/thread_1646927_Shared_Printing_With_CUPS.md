---
title: "Shared Printing With CUPS"
date: 2010-12-16
forum: General Help
---

### Post by TheFuzz4 on 2010-12-16
So last night I picked up a HP LaserJet Printer, took it home and plugged it into my Ubuntu computer in my living room, of course Ubuntu recognized it right away and took care of the dirty work of installing drivers and everything else for me.  I went through the CUPS community page here on Ubuntu for sharing the printer, got that all setup and was able to add it to my laptop.  The problem I'm now having is that whenever I go to print to the printer it keeps asking me for a username and password.  I've checked everything that I can think of and can't find anything that I need to change as everything is shared correctly. I will post a copy of my cups.confd file at the end of this just in case I'm missing something.  Also no matter what username and password I give the prompt it never lets me print.  Thank you for your help in advance.

```


LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI>
  AuthType Default
  Order deny,allow
</Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
AuthType Default
Require user @OWNER @SYSTEM
Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
  AuthType Default
  Require user @SYSTEM
  Order deny,allow
    </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
      </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
      AuthType Default
      Require user @OWNER @SYSTEM
      Order allow,deny
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>

```

---

### Post by Morbius1 on 2010-12-16
Can you give us a link to whatever this CUPS community page is you referenced. It sounds like you're using samba to connect to the printer share.

---

### Post by TheFuzz4 on 2010-12-16
Sure not a problem here is the link that I used to setup sharing of the CUPS
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by Morbius1 on 2010-12-17
Couldn't follow that HowTo at all.

I might be saying the same thing as the HowTo but make sure you did the following on the machine with the printer ( Server ):

* Step 1: Enable Sharing for that Printer.*
System > Administration > Printing > Right Click the attached printer > Properties > Policies
Check Enabled, Accepting Jobs, and Shared

* Step 2: Enable Publishing of the Shared Printer*
System > Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

On the machine that wants to access the printer ( Client ) you have many choices.

On the off chance that you're using samba to access the printer then you need to modify the samba configuration file:

Open the file as root:
```
gksu gedit /etc/samba/smb.conf
```Look for the section that looks like this and change guest access to yes:
> [printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   [COLOR=Blue]**guest ok = yes**[/COLOR]
   read only = yes
   create mask = 0700
I don't think you need to restart cups but just in case:
```
sudo service cups restart
```Then restart samba:
```
sudo service smbd restart
```If you're not using samba then connect to the printer directly:
System > Administration > Printing > New

Select "Other" > In the "Enter URI" box enter it's location in one of the following formats:
```
ipp://WORKGROUP_NAME/MACHINE_NAME:631/printers/Linux-Printer-Name
ipp://MACHINE_NAME:631/printers/Linux-Printer-Name
ipp://192.168.0.100:631/printers/Linux-Printer-Name

```Changing WORKGROUP_NAME, MACHINE_NAME, Linux-Printer-Name, or 192.168.0.100 to their appropriate values.

---

### Post by TheFuzz4 on 2010-12-17
Thank you yes it turns out I was trying to connect to it through SAMBA so I am now connected to the printer through SAMBA but I would still like to connect to it through CUPS.  Now when I go to connect to it through CUPS I get 
Share Printers is not available.
Everything is setup in CUPS to share I don't know if perhaps I'm missing something somewhere.  Thanks for your continued help with this.

---

### Post by Morbius1 on 2010-12-17
> Thank you yes it turns out I was trying to connect to it through SAMBA  so I am now connected to the printer through SAMBA but I would still  like to connect to it through CUPS.When you go through Samba you're still getting to CUPS it's just that you have to play with Samba to get it to work.
> Now when I go to connect to it through CUPS I get 
Share Printers is not available.I don't know what that means. Where are you getting that error?

---

### Post by TheFuzz4 on 2010-12-17
> **Morbius1 said:**
> 
I don't know what that means. Where are you getting that error?

I get that when I try and add the printer on my laptop and going to the address ipp://192.168.1.175:631/Printers/HP-ColorLaser-Jet-4550- I give that as the address and then I click on Verify and then that pop up comes up.

---

### Post by Morbius1 on 2010-12-17
> ipp://192.168.1.175:631/Printers/HP-ColorLaser-Jet-4550
Don't now if that's a typo but the "P" in printers needs to be lower case:
```
ipp://192.168.1.175:631/[COLOR=Blue]printers[/COLOR]/HP-ColorLaser-Jet-4550
```

---

### Post by TheFuzz4 on 2010-12-17
Here is a screenshot of what I have going on

---

### Post by TheFuzz4 on 2010-12-17
FYI I realized I forgot to put 631 in the Host address, so I did that but still get the same error

---

### Post by TheFuzz4 on 2010-12-17
Ok I think I figured this out
After reading from here
[http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html](http://www.debianadmin.com/setup-cups-common-unix-printing-system-server-and-client-in-debian.html)
I found out I had to create a client.conf in /etc/cups/
so 
```

sudo vi /etc/cups/client.conf

```
Then inside of that I had to add the following two lines
```


#Servername
ServerName 192.168.1.175

#Encryption
Encryption IfRequested

```
I don't know exactly why it is that I had to do this and specify in here exactly where the print server was located at but hey it works.  
Thank you for your help with this and I hope that this helps others out as well.

Also found out that you can specify a wild card in here so I just changed my ServerName line to read 
```

ServerName 192.168.1.*

```

---

### Post by Morbius1 on 2010-12-17
I remember client.conf from years ago. This sure does sound like a bug to me. Since it's not in the default Ubuntu ( or any ubuntu based distros that I've used ) nobody would be able to access a shared printer by default.

I'll have to search launchpad to see if this is a common thing.

Thanks for the info. You never know when it might happen to me. ;)

---

