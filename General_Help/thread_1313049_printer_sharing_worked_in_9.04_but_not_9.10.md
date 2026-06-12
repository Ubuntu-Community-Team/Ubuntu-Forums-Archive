---
title: "printer sharing worked in 9.04 but not 9.10"
date: 2009-11-03
forum: General Help
---

### Post by stupid head on 2009-11-03
Printer sharing worked fantastically on 9.04 Jaunty but won't work on 9.10 Karmic. First of all, enabling printer sharing won't make it broadcast the printer service via zeroconf (Bonjour). I can get around that by manually creating an Avahi service with a config in /etc/avahi/services/. However, the real problem pops up when I try to add the shared printer to the other computers in my network. On Windows when I try to add the shared printer, it says "You do not have sufficient access to your computer to connect to the selected printer." On a Mac, it will let me install the printer, but it will not let me submit jobs to the shared printer. Ubuntu 9.10 can't even discover the shared printer.

For now, I will stick to 9.04. I hate seeing what seems to be a regression in 9.10.:(

---

### Post by sb000b on 2009-11-03
Hi, 

I have the same kind of issues.
It used to work in 9.04 server but in 9.10 server, other computers can't discover the printer (OsX Snow Leopard & Ubuntu 9.10 client).
Does anyone has an idea on how to address tis issue ?

Thanks in advance

---

### Post by jpfink on 2009-11-03
Same here. Has this been listed as a bug yet? I wonder if the problem is in the sharing of it by the server or the discovery of the client.

---

### Post by sb000b on 2009-11-04
And what about removing cups and building it from source ?

---

### Post by SteveDee on 2009-11-05
Only discovered yesterday that printing over the network via my upgraded (9.10) computer no longer works from a 9.04 or a Windows machine.

But after a lot of experimentation I've discovered a horrible hack!

Go to System > Administration > Samba and double click your printers directory (see attached).
Now select the "Access" tab and enable "Allow Access to Everyone".
Now click OK and wait a short time, then close the Samba dialog window.

 * The good news: you can now print from remote computers!

 * The bad news: when you reboot your 9.10 pc you won't be able to print.

So next time you have to set "Access" to "Only Allow Access to Specific Users", select a user, click OK, wait a short time, then set it back to "Allow Access to Everyone". ...then you can print.

Hopefully, by the time the novelty of this little ritual has wore off there will be a fix for it!


Additional: Even simpler (but not nearly so entertaining) is to stop then restart Samba. You can do this via terminal or even make yourself a dinky script.

Commands are:-
 sudo /etc/init.d/samba stop
 sudo /etc/init.d/samba start
...and you can check the status:-
 sudo /etc/init.d/samba status

---

### Post by Nausser on 2009-11-10
Same issue here. Upgraded from 9.04 to 9.10 and now none of my printing works. I had local network printing and IPP working perfectly. I even tried installing the printer and then sharing it on another computer with a fresh 9.10 install. No prevail.

This is sort of a big one guys... how can these problems slip through every time? So many things were fixed with 9.10 and then this is allowed to happen.

I sure hope this is figured out soon!

---

### Post by thawn on 2009-11-10
Same problem here. Has anyone posted a bug for this?

Could this be some kind of firewall issue?

afaik, I don't have a firewall installed...

---

### Post by Gazneth on 2009-11-10
I worked around this problem by adding a line to /etc/rc.local ```
sudo gedit /etc/rc.local
``` then insert this line before exit0 ```
/etc/init.d/samba restart
``` This restarts Samba and starts the nmbd process, that is causing the problem by initializing too early in the boot process. After doing this test by rebooting or a```
sudo /etc/init.d/samba restart
``` then check nmbd with ```
sudo /etc/init.d/samba status
```

---

### Post by GaryHT627 on 2009-11-10
Thank you!!  The code worked great and I can print again.

---

### Post by lbodrozic on 2009-11-11
Printer sharing via SAMBA with the provided init edit seems to work.

But does anybody actually know what's wrong with sharing CUPS/IPP/Bonjour?

I didn't even have SAMBA installed prior to this issue, and I'd rather not have it installed if I can help it.

Pretty bittersweet as it is.

---

### Post by SteveDee on 2009-11-11
> **Gazneth said:**
> I worked around this problem by adding a line to /etc/rc.local...

This is a nice clean solution, and I won't need to remember to remove it when they eventually fix this bug. Many Thanks!

---

### Post by schmod on 2009-11-11
You can add me to the list of people having the same problem.

---

### Post by danila4m on 2009-11-12
As for me, samba restart makes no good. The picture is the same all the time: my Samsung ML-1640 works fine at karmic; it is seen from windowsXP machines - but with "couldn't connect,no access" status. When reinstalling it on windows client EVERY TIME a driver is requested to install, and still "no access"... All Samba settings are the same as at ubuntu 9.10...

---

### Post by evplatt on 2009-11-12
I think the problem this thread was started for was not related to Samba at all.  I also lost printer sharing with the 9.10 upgrade, and haven't had Samba installed at all, before or after the upgrade.

People on our network with Macs depended on our Ubuntu server to forward jobs to our main printer, since they can't connect directly.  The copier will not accept jobs in PS format, so they have to connect through CUPS, since the server will convert their print jobs to PCL before forwarding to the copier.

I hope this gets resolved soon, since Mac users around here are out of luck until then.

---

### Post by lbodrozic on 2009-11-12
Agreed, evplatt. The original thread was not started for samba printer sharing. It was for bonjour / cups printer sharing. Although it seems that samba printer sharing is having issues as well.

For what it's worth, I installed samba and shared my printer that way (same as you, I didn't even have it installed prior). Then after applying the samba hack from this thread, I was able to reinstall the printer in os x using samba (Windows tab) instead of bonjour / cups. It's working now.

But this means you have to reinstall the printer on any machine that uses it, and the driver has to be on your local mac. Cups made all this so much easier. I'm very much yearning for a fix for that.

So it's very far from a clean fix, but if you are in a huge pinch I can confirm this workaround is working for me.

Also, how do we get action taken on this? I'm quite new to it all. Are there devs monitoring these forums? Should I file a bug somewhere? I've never had a Ubuntu issue before that the forums hadn't already solved for me.

---

### Post by negations on 2009-11-13
As above, I had a working printing system with 9.04 machines but have upgraded all of them to 9.10 and shared printing does not work.  If I enter the printer details manually using LPD or IPP the printing itself fails with a SpliX error.

---

### Post by MockY on 2009-11-14
Add me to the list as well.
How on earth can something like this be overlooked? At least they should patch it fast as heck, but yet there is no fix for it. *sigh*
But this is how it's been lately with the releases. They fix bugs in the new release but create just as many, bugs that did not exists on older releases. To me it simply does not make sense.

But I will patiently wait for a fix, just like I always do, and always will.

---

### Post by Simanek on 2009-11-14
I was frustrated with this too after upgrading to 9.10. With things like these I hesitate to resort to a commandline solution. I really want to hold Ubuntu to a standard of being approachable for laymen.

After giving up I discovered that doing the following enabled sharing of my printer once again. I have a desktop running 9.10 with a USB-connected HP printer. My other system is a laptop running 9.10. Doing the following made it easy to print from the laptop to the printer connected to my desktop.

**DESKTOP DIRECTLY CONNECTED TO PRINTER**
[LIST=1]
[*]Go to Main **Menu > System > Administration > Printing**
[*]In Printer Configuration menu go to **Server > Settings**
[*]Check "*Publish shared printers connected to this system*" and click **OK**
[*]Double-click on the printer that you wish to share, under **Policies** check *Enabled*, *Accepting jobs* and *Shared*. Then click **OK**.
[/LIST]

**LAPTOP**
[LIST=1]
[*]Go to Main **Menu > System > Administration > Printing**
[*]In Printer Configuration menu go to **Server > Settings**
[*]Check "*Show printers shared by other systems*" and click **OK**
[/LIST]

Once you do the above any available network printers should be visible via Bonjour/whatever. I think in past versions of Ubuntu sharing printers like this was all set on each individual printer. Hopefully this helps.

---

### Post by mrjerryk on 2009-11-15
> **Simanek said:**
> I was frustrated with this too after upgrading to 9.10. With things like these I hesitate to resort to a commandline solution. I really want to hold Ubuntu to a standard of being approachable for laymen.

After giving up I discovered that doing the following enabled sharing of my printer once again. I have a desktop running 9.10 with a USB-connected HP printer. My other system is a laptop running 9.10. Doing the following made it easy to print from the laptop to the printer connected to my desktop.

**DESKTOP DIRECTLY CONNECTED TO PRINTER**
[LIST=1]
[*]Go to Main **Menu > System > Administration > Printing**
[*]In Printer Configuration menu go to **Server > Settings**
[*]Check "*Publish shared printers connected to this system*" and click **OK**
[*]Double-click on the printer that you wish to share, under **Policies** check *Enabled*, *Accepting jobs* and *Shared*. Then click **OK**.
[/LIST]

**LAPTOP**
[LIST=1]
[*]Go to Main **Menu > System > Administration > Printing**
[*]In Printer Configuration menu go to **Server > Settings**
[*]Check "*Show printers shared by other systems*" and click **OK**
[/LIST]

Once you do the above any available network printers should be visible via Bonjour/whatever. I think in past versions of Ubuntu sharing printers like this was all set on each individual printer. Hopefully this helps.


If with the above steps I am still unable to print from either my laptop or my windows machine.

---

### Post by MockY on 2009-11-15
I was unable to get it working with the above method.

---

### Post by lbodrozic on 2009-11-15
I had already tried this as well with no luck. Seemed promising, but didn't do the trick. :(

---

### Post by gizmobay on 2009-11-17
Add me to the list. Samba network shares work for me but not the printer. I just get opening on my Samsung clp300 in WinXP. Just upgraded to Samba 3.4.0 and this didn't solve my issue. The printer works on the Ubuntu side.

---

### Post by alek66 on 2009-11-18
Same overhere... Bonjour/cups always worked like a charm!

Let us know when a patch is released.

---

### Post by jletze on 2009-11-22
Same here.  I can see the discovered printers but can't print to them.

---

### Post by XubuRoxMySox on 2009-11-22
This is what finally worked for me. Go to [http://localhost:631/](http://localhost:631/) in your web browser and configure your printer there. You will be asked for a username and password - it's the same as your root username and password. Go to the **Administration** tab and choose **Add Printer**. There's even a box you can check for sharing your printer on a network, or finding one on your network.

-Robin

---

### Post by flamingsole on 2009-11-23
Just wanted to add myself as another person who could print with Avahi in 9.04, and cannot do so in 9.10. My Mac, when trying to print to Ubuntu, says "Processing - "Unable to get printer status (Bad Request)!" and can't print.

I think it originally had a different error message, but there have been a few package changes that haven't fixed the bug (including one I saw today for Avahi), but may have changed something. Regardless, I'd love to hear if anyone finds a fix, or hears that an update is going through.

Thanks,
Jonathan

---

### Post by gusman21 on 2009-11-25
When browisng for the printers in windows, can you see the shared printer?

---

### Post by WhyIsThisOpen on 2009-11-27
I have a **workaround (for mac clients)** for cups issues that doesn't involve samba. I am running Karmic on the server and Snow Leopard on the client: both are on my local network.

First, what I tried that didn't work:

[LIST]
[*]Redoing the configurations in Menu > System > Administration > Printing
[*]Redoing the configurations from a browser at localhost:631. (This would be from the server, not the client, of course.)
[*]Making sure the configurations in /etc/cups/cupsd.conf were correct. (As best I can tell.)
[*]Installing every update that I got.
[/LIST]

What did work:

[LIST=1]
[*]Make sure the printer is properly configured by visiting the cups configuration page on your local machine. eg: go to [http://*serverName*]("http://%3Ci%3EserverName%3C/i%3E"):631/printers/ and select the printer from the list.
[*]You should now be at a page at [http://*serverName*]("http://%3Ci%3EserverName%3C/i%3E"):631/printers/*printerName *and it should say something like: *printerName* (Idle, Accepting Jobs, Shared, Server Default) .
[*]Go to the Add Printer window on your Mac client. (Select "Add Printer..." from the printer list in any print window.)
[*]Select the "IP" tab.
[*]For Protocol select "Internet Printing Protocol - IPP" from the drop down.
[*]For the Address enter the host name and port from above. eg: *serverName*:631 .
[*]For the Queue enter the location of the printer from above. eg: printers/*printerName* .
[*]For the Name enter whatever you want it to be called. eg: color printer .
[*]For Print Using choose "Select Printer Software..." from the drop down menu and choose whatever driver you are using for the printer on the remote machine. (You can find this listed on the cups printer page.)
[*]Add the printer.
[*]Test and enjoy.
[/LIST]

What should work but doesn't. (The issue.):

It is my understanding that the printer to be discovered by default in Mac OS X, and that it should be displayed under "Default" printer tab in the Add Printer window. I have printer sharing turned on in cups (on the server) and all the settings appear to be as they were in Jaunty, when things worked.


As a side note, although I do have samba running and my server shows up in the list I have yet to get printer sharing through samba to actually work (Windows or Mac).

---

### Post by flamingsole on 2009-11-28
The above steps worked for me on previous distros - Gutsy, Hardy, Intrepid, Jaunty, etc. but they don't work on Karmic. My Mac returns the following error when I try to add and print with the default Ubuntu printer by the above steps: "Unable to get printer status (Bad Request)!" This error shows when I try to print, to be clear - I can add the printer, and it shows up in the list - it just won't print.

I'm guessing others are having the same issue and that's why we have the thread, though it is interesting that it isn't a universal error.

---

### Post by jonathanmotes on 2009-11-28
I was able to get mine to work with a print server and laptop both running Ubuntu 9.10 by doing two things:

1. Went to [http://localhost:631](http://localhost:631) on the print server machine (I think I used a text based browser like "lynx" since the server is command line only) and chose to share all printers and entered the username and password for the administrator on the computer when prompted.

2. On the "client" (laptop, etc.), I went to System -> Administration -> Printing and chose Server -> Settings... from the print menu, then chose "Show Printers shared by other systems." I still wasn't able to search and find the network printer but it showed up in the printers list automatically.

---

### Post by flamingsole on 2009-11-28
Hello,

So these are the steps that I was just able to get to work. They are similar to the ones from WhyIsThisOpen but maybe the fields are different. Note: I'm running Snow Leopard on the Mac, and Ubuntu Karmic on the Ubuntu system. Both are on the same network.
[LIST=1]
[*]On Ubuntu, go to [http://localhost:631](http://localhost:631) in your browser. Click &#8220;Printers&#8221; and make sure you have the proper name of the printer that is connected to Ubuntu. Click on it, and in the [http://localhost:631/printers/PRINTERNAME](http://localhost:631/printers/PRINTERNAME) screen, you can click Set As Server Default. I&#8217;m not entirely sure if this is a required step, but I did it.
[*]On the Mac, go to [http://localhost:631](http://localhost:631) in your browser. Go to Administration > Add Printer. Let it finish looking. Choose the &#8220;Internet Printing Protocol (ipp)&#8221; option, and click Continue.
[*]In the Connection field, type [http://SERVERNAME:631/printers/PRINTERNAME](http://SERVERNAME:631/printers/PRINTERNAME) where SERVERNAME is the name of your Ubuntu server, and PRINTERNAME is the name by which the server knows the printer, as you saw in step 1. Click Continue.
[*]**Note:** In my previous setup, I was able to use [http://SERVERNAME.local/](http://SERVERNAME.local/), but in the current setup it doesn't work with .local. I just use [http://SERVERNAME/](http://SERVERNAME/).
[*]The Name, Description, Location, etc. fields can be whatever you like. Same for the settings on the following page.
[/LIST]

---

### Post by lbodrozic on 2009-11-30
flamingsole, that did the trick. nice find. for the server name, i had to use my IP address.

---

### Post by alek66 on 2009-12-12
So... they are never gonna fix the bonjuor+cups issue?

It used to work great!

---

### Post by KiDQUiCK on 2010-01-03
I had this problem as well. **Here's the workaround** until CUPS gets updated...

This problem is documented in [bug 482836]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/482836"). It affects Windows Vista 64 and Windows 7 64-bit clients trying to connect to a Ubuntu 9.10 CUPS-networked printer. Error messages in Windows are vague and uninformative; I received error code 0x0000000d.

The solution is to bind a network printer to LPT1 using this command from Windows. ie:
```
net use lpt1 \\UbuntuHost\MyPrinter /persistent:yes
```

You may have to run command prompt (cmd.exe) with administrator privileges. The persistent switch will allow this setting to be retained after reboot.

Then map a local printer from Windows to LPT1. Voila!

Thanks to the Ubuntu community for support over the years.

Cheers

---

### Post by banchali on 2010-01-04
> **lbodrozic said:**
> flamingsole, that did the trick. nice find. for the server name, i had to use my IP address.

It should work at servername.local if you add the line:
```
ServerAlias *
```
to your cups config (at [http://localhost:631/admin/](http://localhost:631/admin/) on the server, click 'edit configuration file').
CUPS by default will name itself 'servername' and will view requests to 'servername.local' as invalid (you should see '...using invalid Host: field "server.local" ' in the error log). Of course, normal zeroconf means that clients won't see the server at 'servername', rather 'servername.local', so neither way works in the default setup.

It really is completely ridiculous that something as basic as Bonjour printer sharing not only doesn't work, but stopped working when it worked just fine before.  I can now print via both IPP and SMB (from OSX 10.6.2 and 10.5.4) with the fixes listed here, but Bonjour really is the norm these days and 9.10 should definitely not have been released with this not working, let alone kept broken for these 3 months since release.

---

### Post by CovenStine on 2010-01-23
> **Gazneth said:**
> I worked around this problem by adding a line to /etc/rc.local

Thanks Gazneth!

---

### Post by damilaredavids on 2010-01-26
> **Nausser said:**
> Same issue here. Upgraded from 9.04 to 9.10 and now none of my printing works. I had local network printing and IPP working perfectly. I even tried installing the printer and then sharing it on another computer with a fresh 9.10 install. No prevail.

This is sort of a big one guys... how can these problems slip through every time? So many things were fixed with 9.10 and then this is allowed to happen.

I sure hope this is figured out soon!
Here’s how to do a basic shared printer setup using Samba in Ubuntu  9.10 Karmic Koala. This is the easiest way to do it, since with guest  access and no authentication, anyone who can access the computer over a  network connection will be able to print to the shared printer. However,  this involves minimal security, so I would not recommend using this  configuration on a machine with any actual file shares. Overall, I think  this setup would be best for home users, or small offices. Enterprise  users, or home users with more rigorous security needs, should use a  more secure configuration. All that said, here’s how to set it up.
 First, you will need a printer of some sort connected to your Ubuntu  machine. Either a USB printer or a networked printer (one with its own  IP address) will work, so long as it’s properly set up on your Ubuntu  computer.
 Next, open up a Terminal window, and install Samba using the  following command:
[B]
sudo apt-get install samba[/B]
 We’ll need to edit Samba’s configuration file, smb.conf, with the  following command (make certain to create a backup copy of the smb.conf  file first, in case anything goes wrong):
[B]
sudo gedit /etc/samba/smb.conf [/B]
 (Note that you can replace gedit with your editor of choice, but if  you’re in the GUI, you might as well use gedit.)
 Once inside the smb.conf file, you’ll need to change a number of  lines. Some of the lines will be commented out with a semicolon (;) or a  crosshatch (#) in front of them. Note that any lines we change here  will need to have the ; or the # removed to activate them.
 Because we’re going to enable guest access in Samba (which is  inherently less secure than user-based authentication), we’ll configure  Samba by setting it so that only the local area network can access it.  Add these lines to the **[global]** section of your  smb.conf file:
[B]
interfaces = lo eth0
bind interfaces only = true[/B]
 Edit this line in the **[global]** section to enable  guest access in Samba (if the line isn’t there, add it):
[B]
security = share
[/B]
 
 Finally, change the **[printers]** share definition so  that it looks like this:
 [B][printers]
comment = All Printers
browseable = no
path = /var/spool/samba
printable = yes
guest ok = yes
read only = yes
create mask = 0700[/B]
 Save your changes to the smb.conf file, and restart Samba with the  following command:
[B]
sudo /etc/init.d/samba restart[/B]
 You can test your Samba definitions with the use of the **testparm  **command. If your definitions come up OK, you should be ready  to connect to the printer
 To use your shared printer, access your Ubuntu box from another  machine. On a Windows PC, go to Start, Run, and type \\hostname (or the  IP address, \\192.168.0.1), and click OK. If you typed everything  correctly, you should see a window with your printer icon. Double-click  the printer icon to install it (make sure you have the correct driver  for your model of printer on hand; check your manufacturer’s website)  and you should be set to print.
 Note that Windows may claim that access is denied to the printer, but  if you typed everything correctly, you should be able to print anyway.

---

### Post by gewitty on 2010-02-03
> **jletze said:**
> Same here.  I can see the discovered printers but can't print to them.

Exactly the same problem here. My previous (9.04) set-up had a Canon USB printer connected to my desktop, which was shared by another machine on the network, also running 9.04. This worked fine. I recently upgraded the desktop to 9.10 and found that whilst the second machine could see the shared printer, it could no longer print to it. I don't have SAMBA installed and would like to see a fix for the CUPS problem fairly soon. Is anyone working on the problem? Looking at all the posts here, there seems to be no indication that this issue has been picked up by the developers.

---

### Post by eraker on 2010-02-07
I spent probably three hours today trying to get a PowerBook running Snow Leopard to print to a cups-shared printer connected via USB to my Ubuntu Desktop.

I finally figured out that I needed to open my firewall on the Ubuntu Desktop to allow requests to port 631.

Then, on the PowerBook I went into the Cups administration tab ([http://localhost:631](http://localhost:631)), found the network printer, then clicked "modify printer," and selected "Http".

After that, in another Safari tab on the PowerBook I went to [http://IP-ADDRESS-of-UBUNTU-DESKTOP:631](http://IP-ADDRESS-of-UBUNTU-DESKTOP:631) and clicked on "Manage Printers," and then I clicked on the printer name I wanted to print to, and copied the full http address for the printer from the address bar of firefox. (It looked like this: [http://IP-ADDRESS-UBUNTU:631/printers/Deskjet-D2300-series](http://IP-ADDRESS-UBUNTU:631/printers/Deskjet-D2300-series))

Then, all I had to do was paste that http address into the localhost:631 http location and click "modify printer."

It was a totally dumb solution, but it worked and I'm just happy not to mess with it anymore.

---

### Post by techieguy_100 on 2010-04-05
OK, I've tried every solution suggested in this thread, and I have no joy. I have Karmic Koala on both machines, all updates installed. I have shared and published the printer ( HPLaserjet 1018 ) on my 'server' machine, but the client is not 'seeing it'  I am amazed that there is not a global solution to this problem yet.  This should be a piece of cake!

---

### Post by dkoes on 2010-04-30
Anyone tried 10.04 yet?  And incidentally, did anyone actually file a bug about this, or did we all just assume someone else would?

---

### Post by flamingsole on 2010-04-30
> **dkoes said:**
> Anyone tried 10.04 yet?  And incidentally, did anyone actually file a bug about this, or did we all just assume someone else would?

I have not tried 10.04 yet, though I'll be apprehensively trying it this evening.

I didn't file a bug. I assumed it was an intentional change somewhere, I guess.

---

### Post by dkoes on 2010-05-03
Still broken in 10.04.  :(

---

### Post by flamingsole on 2010-05-03
> **dkoes said:**
> Still broken in 10.04.  :(

I tried it in 10.04. The fix I posted at [http://ubuntuforums.org/showpost.php?p=8403263&postcount=31]("http://ubuntuforums.org/showpost.php?p=8403263&postcount=31") still works perfectly for me. My environment consists of a desktop running 10.04 and two laptops running Snow Leopard.

---

### Post by dkoes on 2010-05-10
I filed a bug (surprisingly, no one reported it):
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/577931](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/577931)

If this issue affects you, please start tracking the bug.  It shouldn't be necessary to go through ipp printing or samba.

---

### Post by alek66 on 2010-05-11
so....bottom line... this still doesnt work nor there is a workaround.

---

### Post by lbodrozic on 2010-05-11
This is logged and well understood here:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/465916](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/465916)

---

### Post by josefismael on 2010-05-20
ran into the same issue as everyone else, but here's what worked for me:

Go through the CUPS printer setup process by browsing to http://<serverip>:631. Hit Add Printer and add the printer (pretty straightforward).

On your windows machine, just go to Add Printers and add the printer in Windows as a Network printer with the following address syntax:

https://<serverip>:631/printers/<printername>

good luck!
jm

---

### Post by Kittykathy on 2010-06-20
Browsing to [http://localhost:631/printers](http://localhost:631/printers) and installing networked printers using the services provided absolutely works.  Perhaps this was the intended solution when transitioning from 9.04 to 9.10.
 I've spent hours and hours over a period of months trying to solve this problem and this worked.

---

### Post by Kittykathy on 2010-06-20
Printing from Vista to a Linux networked printer.

My system:  An Ubuntu desktop running 8.10 with a Konica Minolta Magiccolor 2400W USB printer, a laptop with 9.10 and Vista laptop with a Brother wireless 2040 Printer connected locally.

I already had Samba installed and working. I could share files between the Linux laptop, desktop and Vista machine but network printing eluded me.  I had tried a million different combinations of installations using System/Administration/Printing on the Linux laptop, printing was always shared, everyone could print, etc.

I had two printing problems. I could not access the Magiccolor printer from the Linux laptop and from the Vista laptop.

I could access the Brother printer from the Linux laptop and the Vista laptop.

The solution to the network printing issue was to first install the Magiccolor printer  as a Linux networked printer as described in the previous post.  This installed provided network printing success on the Linux laptop. This installation also  provides an 8 character name which I've seen described in other posts as necessary to having printing success with 9.10 and Windows. The other names created using System/Adminstration/Printing were much longer than 8 characters.

Once the printer is installed on the Linux laptop as a Networked printer, on the Vista machine I navigated to 
Control Panel/Printers/Add a Printer.

Select Network printer and allow Vista to browse the list of networked printers.  I found my newly named 8 character printer in the list, selected it, installed the driver(which I had installed hundreds of times before in many other attempts) and voila, Vista connected , no weird messages, etc about not being able to connect, lack of permission, hundreds of other useless messages.  I was able to print the test page.

Problems solved....this makes me so happy!  I hope this info can help others.

---

### Post by Mexico Man on 2010-07-07
Same network printing issue here.
I am trying to print from a Windows Vista Laptop to a Canon IP2600 on a Linux Mint 9 desktop via IPP.
The print job launches on the Vista laptop then after a minute the status changes to "Error - Printing".  This is really annoying because I had network printing working fine on a prior version of Ubuntu.
Unless an answer can be found I will reluctantly give Samba a go next. Although in truth I really shouldn’t have to because IPP should just work out of the box.

---

### Post by dwpbike on 2011-09-16
i do ubuntu 10.4 on two desktops with a usb printer connected to one.  i read this thread in preparation for sharing the printer with the other desktop.  i deleted the current config and added a new network printer.  all went smoothly, except i couldn't print.  so i started over.  when i went to the other computer, then i noticed that it "saw" the printer.  this is my second discovery that, in many cases, ubuntu has already taken care of things.

---

