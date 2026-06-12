---
title: "Print server"
date: 2009-11-15
forum: General Help
---

### Post by p2ranger on 2009-11-15
After fighting with 9.10, I have done a clean install of Ubuntu Server 9.04. Currently just trying to get the printing to work.

I've looked at a couple of other thread about getting printing to work from the Ubuntu Server edition, but they are dated.

[http://ubuntuforums.org/showthread.php?t=310450](http://ubuntuforums.org/showthread.php?t=310450)

[http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282)

For example, in the first thread it says to do this:
```

adduser cupsys shadow

```

And it says
```

adduser: The user `cupsys' does not exist.

```

Overall, my problem is that I can't get the web front to pull up when I try to administer CUPS. It tells me the web page isn't available when I do the [https://nameofmyserver:631](https://nameofmyserver:631) Is there any more recent tutorials or help threads about setting up printers from the command line?

Thank you

Jason

---

### Post by Bruce H on 2009-11-15
I don't think I can help with command line issues with cups. However, you might try installing webmin. It makes it very easy to administer your server over the network, and can configure printers, samba shares, nfs exports, apache server, all kinds of things.

Grab the latest from here:

[http://prdownloads.sourceforge.net/webadmin/](http://prdownloads.sourceforge.net/webadmin/)

Currently, it is this:

[http://sourceforge.net/projects/webadmin/files/webmin/1.490/webmin_1.490_all.deb/download](http://sourceforge.net/projects/webadmin/files/webmin/1.490/webmin_1.490_all.deb/download)

Copy that file to your server, then run:

sudo dpkg -i webmin_1.490_all.deb

point your browser at [https://your-server-ip-here:10000/](https://your-server-ip-here:10000/)

enjoy.

---

### Post by Bruce H on 2009-11-15
heh. Sorry. you are running webmin it seems. I should read better.

---

### Post by p2ranger on 2009-11-15
Thanks for the tip, but using webmin, I'm not successful in adding a printer there either.

Jason

---

### Post by Queue29 on 2009-11-15
It has to do with the default config file for cupsys being completely stupidly locked down. If you open it up and just delete away all the restrictions, it works fine ;)

See:
[http://bozosort.com/content/?p=19](http://bozosort.com/content/?p=19)

---

### Post by p2ranger on 2009-11-15
Well that is interesting, thanks. I tried it, but when I try to pull it up in a web browser I get the 403 Forbidden page. The permissions for cups look like this though:

```
-rwxr-xr-x 1 root root 2526 2009-10-31 17:32 /etc/init.d/cups
```

are there some permissions I need to change somewhere so that I can get that to come up? This is farther than previously where it just told me that it wasn't there.

Thanks

Jason

---

### Post by p2ranger on 2009-11-16
Well, administering CUPS by going to [http://server:631](http://server:631) still gives me the 403 Forbidden page.

Using Webmin, it appears there, but has no print driver. Tried to print a test page and it gives it as a failure. I'm not sure how to add the print driver for it. Its an HPlaserjet 1022

This part of adding a printer was so much easer when I was trying it all out on the Desktop install.

The printer shows up from windows when I browse for the printer, but when I try to install it as a printer for windows, it says there's no printer driver installed. Of course, because there's no printer driver that the printer on the linux server is pointing towards.

I sure wish the documentation was more straight forward/easier to find.

Jason

---

### Post by Queue29 on 2009-11-16
I promise you, the problem is still in the config file.

Did you replace /etc/cups/cupsd.conf with the following:

```

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseLocalProtocols
<Location />
  # Allow remote administration...
  Order allow,deny
 # Allow @LOCAL # if you are on a LAN you could enable this
 </Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
 #  Allow @LOCAL # again, on a LAN, you could enable this
</Location>
<Location /admin/conf>
  # Allow remote access to the configuration files...
  Order allow,deny
  # Allow @LOCAL # LAN? enable if you want
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Order allow,deny
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    Order allow,deny
    **Allow 192.168.1.0/24**
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    Order allow,deny
    **Allow 192.168.1.0/24**
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Order allow,deny
    **Allow 192.168.1.0/24**
  </Limit>
  <Limit All>
    Order allow,deny
    **Allow 192.168.1.0/24**
  </Limit>
</Policy>

```

and edit the bolded lines to fit your LAN?

---

### Post by p2ranger on 2009-11-16
I did put that in as the cupsd.conf file. I'm assuming the numbers in there are right. I'm assuimg that the IP addresses it lists are for the range of all the ip's that are in the 192.167.1.X range where X is all the numbers that can be put in for that holder (forgive me, I can't remember the range of numbers that can hold that spot). My server is 192.168.1.120

It still tells me error 403 Forbidden when I try to pull up the web front to administer CUPS.

I even tried changing it to the specific IP address for my laptop that I'm using to try to get to it, and it still gives me the same problem.

Ideas?

Thanks

Jason

---

### Post by Queue29 on 2009-11-16
Is the 403 coming from Apache (or whatever webserver you're using) or is it the 403 from cupsys (with the beige background) ?

Is this a headless server? If not, try loading the page from a webbrowser on the server itself. 

Also, **are you restarting the cupsys daemon every time you update the cupsd.conf file?**

The command for that is:

```
sudo /etc/init.d/cupsys restart

```

---

### Post by p2ranger on 2009-11-17
It looks like what you get from Apache when you don't have the file permissions set correctly. One of the other posts in this thread has the file permissions. I wouldn't think I have to chmod something to 777. I'm not even real sure what it is that gets called up when you try to get that in the web browser. 

So it is a white screen. Apache is what's installed so I'm guessing that is what is serving the pages. 

Yes I have restarted the CUPS program. I've even rebooted the computer. It is headless but I have a monitor I can hook up to it. Should I try using something like links to browse to it?

Thanks

---

### Post by p2ranger on 2009-11-17
Update

Still not working. I used the published conf file shown earlier in this thread. Installed links text based web browser on my server (as it is a CLI machine) and still got the Forbidden error. I restored the original conf flie and I can browse to it with the links browser from that machine. Still not the solution I'm looking for, but at least CUPS does work, somewhere. Still trying to sort this out.

Jason

---

### Post by p2ranger on 2009-11-17
Well, I'm not quite sure what all that stuff means in the file. I have a desktop version of Unbuntu 9.10 that I was using earlier as a print server and also to test somethings out on. I copied the cupsd.conf flie from it, as I knew it was allowing me to browse to administer CUPS and used it. Well, IT WORKS! I'm still not sure how to administer some stuff on there such as canceling jobs and a duplicate printer it shows. It says I have to administer it through a https: link, which it won't allow me to do. It says its unavailable. Not sure how to change the security so I can do that part of it. But below is the one I used that atleast lets me print and get to the administration page now. 

Thanks for all the help

Jason

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
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
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
  <Limit Cancel-Job CUPS-Authenticate-Job>
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
      Order deny,allow
        </Limit>
  <Limit All>
        Order deny,allow
          </Limit>
</Policy>

```

---

### Post by Queue29 on 2009-11-17
Oh wow, I am so sorry..
In my example file 
 # Allow @LOCAL # if you are on a LAN you could enable this
should have been replaced with 
Allow All

@LOCAL just restricts access to your local network 

Now, to actually be able to configure things, you need to disable safety features like I was talking about before. For example, all those places that say "Require User" are going to give you needless troubles. Same for Authtype settings. Delete them to turn them off, and your config file will end up looking like the one I posted before.

---

### Post by p2ranger on 2009-11-17
Thanks again for your help.

So I managed to piece together this file:

```


LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS
BrowseLocalProtocols
<Location />
  # Allow remote administration...
  Order allow,deny
#  Allow @LOCAL # if you are on a LAN you could enable this
  Allow All
 </Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
#  Allow @LOCAL # again, on a LAN, you could enable this
  Allow All
</Location>
<Location /admin/conf>
  # Allow remote access to the configuration files...
  Order allow,deny
#  Allow @LOCAL # LAN? enable if you want
   Allow All
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Order allow,deny
	Allow 192.168.1.0/24
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    Order allow,deny
    Allow 192.168.1.0/24
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    Order allow,deny
    Allow 192.168.1.0/24
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Order allow,deny
    Allow 192.168.1.0/24
  </Limit>
  <Limit All>
    Order allow,deny
    Allow 192.168.1.0/24
  </Limit>
</Policy>


```

I think its working.

On a strange note, I've noticed that it goes between the beige colored admin pages to white. The beige pages are CUPS 1.3 and white are 1.4 Hmmm... Strange

Thanks

Jason

---

### Post by Queue29 on 2009-11-17
I would actually recommend changing those Allow All's back to Allow @LOCAL if it works that way, as Allow All will allow computers outside of your network to access your cupsys pages, which you may or may not consider an issue. Worst case scenario, somebody tells your printer to print a tray full of test pages.

---

### Post by p2ranger on 2009-11-17
Yes, thank you. I was wondering about that. Thanks for clearing it up. I changed it. That's all I need is some 11 year old using up all my paper and thinking it's funny.

Jason

---

