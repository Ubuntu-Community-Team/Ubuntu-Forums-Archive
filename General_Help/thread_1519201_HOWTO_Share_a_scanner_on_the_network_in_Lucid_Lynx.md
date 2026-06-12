---
title: "HOWTO: Share a scanner on the network in Lucid Lynx"
date: 2010-06-27
forum: General Help
---

### Post by Leppie on 2010-06-27
[SIZE=3][COLOR=Sienna]Assumptions:[/COLOR][/SIZE]


[LIST]
[*]Your scanner is installed properly and fully function. If you need to install your scanner first, have a look at the [ScanningHowTo]("https://help.ubuntu.com/community/ScanningHowTo"). To check if your scanner is connected and installed properly you can use the command "scanimage -L".
[*]The machine we're configuring to use as the scanner server has the ip address [COLOR=Green]192.168.1.1[/COLOR] and subnet-mask 255.255.255.0. This means that this machine is on the [COLOR=Blue]192.168.1.0/24[/COLOR] (CIDR notation) network/subnet.
[/LIST]


[SIZE=3][COLOR=Sienna]Preparation:[/COLOR][/SIZE]

Install the package sane-utils:
```
sudo apt-get install sane-utils
```
[SIZE=3][COLOR=Sienna]Server-side setup:
[/COLOR][/SIZE]
Open /etc/default/saned with a text editor:
```
gksudo gedit /etc/default/saned
```Set RUN to yes and save and exit the file.
The file should look like this:
```
# Defaults for the saned initscript, from sane-utils

# Set to yes to start saned
RUN=yes

# Set to the user saned should run as
RUN_AS_USER=saned
```open /etc/sane.d/saned.conf with a text editor:
```
gksudo gedit /etc/sane.d/saned.conf
```Find the following section and modify it using the ip and netmask settings of your scanner server. Also amend if you only want certain hosts to be able to use the scanner:
```
## Access list
# A list of host names, IP addresses or IP subnets (CIDR notation) that
# are permitted to use local SANE devices. IPv6 addresses must be enclosed
# in brackets, and should always be specified in their compressed form.
#
# The hostname matching is not case-sensitive.

#scan-client.somedomain.firm
#192.168.0.1
[COLOR=Blue]192.168.1.0/24[/COLOR]
#[2001:7a8:185e::42:12]
#[2001:7a8:185e::42:12]/64
```(Re)start the saned daemon:
```
sudo service saned restart
```Add the saned user to the lp group so it can access the scanner:
```
sudo adduser saned lp
```
[SIZE=3][COLOR=Sienna]Client-side setup:[/COLOR][/SIZE]

On each client computer you want to give access to the scanner, open the /etc/sane.d/net.conf with a text editor:
```
gksudo gedit /etc/sane.d/net.conf
```and add the ip-address or hostname to the end of the file.
it should look something like this:
```
## saned hosts
# Each line names a host to attach to.
# If you list "localhost" then your backends can be accessed either
# directly or through the net backend.  Going through the net backend
# may be necessary to access devices that need special privileges.
# localhost
[COLOR=DarkGreen]192.168.1.1[/COLOR]
```You should now be able to access the scanner using Simple Scan, XSane, etc.


[SIZE=3][COLOR=Sienna]Web interface:[/COLOR][/SIZE]

In order to provide a web interface for your scanner (which could be useful for guests), install the packages netpbm tesseract-ocr-eng apache2:
```
sudo apt-get install netpbm tesseract-ocr-eng apache2
```
[SIZE=3][COLOR=Sienna]Configure the web server:[/COLOR][/SIZE]

Setup Apache2 to allow CGI scripts to run:
```
echo 'AddHandler cgi-script .cgi' | sudo tee -a /etc/apache2/apache2.conf
```Allow CGI scripts to be executed in /var/www/:
```
sudo sed -i.bak 's/FollowSymLinks MultiViews/FollowSymLinks MultiViews ExecCGI/g' /etc/apache2/sites-available/default
```Restart the apache2 web server:
```
sudo service apache2 restart
```
[SIZE=3][COLOR=Sienna]Installing scanner server:[/COLOR][/SIZE]

Change to the /var/www/ folder:
```
cd /var/www
```Download the scan server archive:
```
sudo wget http://www.openubuntu.com/downloads/ftp/PHP-Server-Scanner-1.2-3.tar.bz2
```Unzip the archive:
```
sudo tar xvf scan*.tar
```Delete the archive:
```
sudo rm scan*.tar
```
[SIZE=3][COLOR=Sienna]Connecting to scanner server:[/COLOR][/SIZE]

You can access the server using its ip address following by /scan. In our case:
```
http://[COLOR=Green]192.168.1.1[/COLOR]/scan
```
[SIZE=3][COLOR=Sienna]Links:[/COLOR][/SIZE]

[LIST]
[*][ScanningHowTo]("https://help.ubuntu.com/community/ScanningHowTo")
[*][SANE protect]("http://www.sane-project.org/")
[*][SANE's  scanner howto]("http://tldp.org/HOWTO/Scanner-HOWTO/index.html")
[*][Scanner Server]("http://scannerserver.online02.com/")
[/LIST]

---

### Post by jmickela on 2010-07-03
Thanks for the info, I followed it and it worked great.

Only one change I would suggest. In the client setup section it should be noted that you have to add the server as a 'client' of itself in order to get the web access working.

I wasn't setting up any clients and skipped that section.

---

### Post by Leppie on 2010-07-03
I'm not sure I understand what you're saying, but I believe you are suggesting that in order to be able to use the web interface on the scanner server itself the scanner server's ip address needs to be added to net.conf?
The scanner server scripts use another engine as Xsane and therefore the scanner server's own ip address does not have to be added to its own net.conf. Accessing using localhost/scan should work fine without the extra line in the net.conf file (I have set up a scanner server box like this, which is working fine).

Note that not all scanners are compatible with the scripts (even though your scanner may be in the sane compatibility list). I have an hp which works fine with both Xsane and scanner server, but my Brother MFC does not like the scanner server (works perfectly fine with Xsane though).

---

### Post by Leppie on 2010-07-09
Updated the guide as the sane daemon can be used without running as root by simply adding the saned user to the lp group (which is naturally better for security).

---

### Post by bdp on 2010-09-20
Not sure why, but this did not work for me until I set

RUN_AS_USER=root

in /etc/defaults/saned.  Any idea why, or how this might otherwise be remedied?

FWIW, I'm running Ubuntu 10.04 (Lucid) AMD64, with all packages up to date.  The scanner is an Epson Pervection V300 with the appropriate packages installed from [www.avasys.jp](www.avasys.jp).  The scanner works fine when run locally.

Before changing RUN_AS_USER to root, the scanning software (e.g., simple scan) on the client would complain that it could not communicate with the scanner (although it did detect it).

Also, with RUN_AS_USER=saned on the server, running "scanimage -L" on the client returned the following two lines:

device `net:sx2840:epkowa:interpreter:001:006' is a Epson (unknown model) flatbed scanner
device `net:sx2840.local:epkowa:interpreter:001:006' is a Epson (unknown model) flatbed scanner

and after setting RUN_AS_USER=root it returned

device `net:sx2840:epkowa:interpreter:001:006' is a Epson Perfection V300 flatbed scanner
device `net:sx2840.local:epkowa:interpreter:001:006' is a Epson Perfection V300 flatbed scanner

---

### Post by perspectoff on 2010-09-20
Awesome thread! Did you put this somewhere in the Ubuntu community wiki?

[https://help.ubuntu.com/community/Scanners](https://help.ubuntu.com/community/Scanners)

Ooops, yep, I see you referenced it in your very first line and in the links at the bottom.

---

### Post by Paresh on 2010-09-26
Hi

I have just followed this guide and am unable to get my scanner to work via the web interface.

```
scanimage -L
``` returns

```
device `plustek:libusb:002:004' is a Canon CanoScan N1240U/LiDE30 flatbed scanner

```

I can scan on the server machine using xsane.  When I connect via the web interface ```
http://localhost/scan
```, and try to search for scanners, I get ```
No Scanners Found
```.

Any clues as to what's wrong?

---

### Post by Paresh on 2010-09-28
Ahem

bump anyone?

---

### Post by jhansonxi on 2010-10-03
I just released a [patch for LSS 1.2 Beta 1]("http://jhansonxi.blogspot.com/2010/10/patch-for-linux-scanner-server-v12.html").  This fixes several bugs in the index.cgi script.

The "no scanners found" error is a permissions problem.  I'm releasing a tool soon that provides a workaround for it.

---

### Post by karthick87 on 2010-10-03
Nice info..Similarly how to a share printer in Lucid..?

---

### Post by jhansonxi on 2010-10-03
> **getyourkarthick said:**
> Nice info..Similarly how to a share printer in Lucid..?
Try:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)
[https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers](https://help.ubuntu.com/community/SettingUpSamba#Sharing%20CUPS%20Printers)

---

### Post by jhansonxi on 2010-10-03
I just **[released scanner-access-enabler]("http://jhansonxi.blogspot.com/2010/10/scanner-access-enabler.html")**, a GUI tool for setting scanner device permissions so that www-data (and thus LSS) can use any scanner.

---

### Post by Paresh on 2010-10-04
Thanks Mate

Applied the patch and ran the permissions script.

That all works fine now.

---

### Post by MaruAdventurer on 2010-10-07
This is an outstanding how-to by all accounts. But its focus is how to take a locally attached scanner (USB, SCSI, Par) and share it on the network. No problem with that. But how would one utilize XSane with a network based scanner with its own IP address?

Use case:

* Device is a Lexmark X422 with an ip address of 192.168.1.249.
* I can scan to pdf with the device via FTP.
* Device comes with a support disk, sadly most of the code being for windows.

Any suggestions??

---

### Post by jhansonxi on 2010-10-07
> **MaruAdventurer said:**
> This is an outstanding how-to by all accounts. But its focus is how to take a locally attached scanner (USB, SCSI, Par) and share it on the network. No problem with that. But how would one utilize XSane with a network based scanner with its own IP address?

Use case:

* Device is a Lexmark X422 with an ip address of 192.168.1.249.
* I can scan to pdf with the device via FTP.
* Device comes with a support disk, sadly most of the code being for windows.

Any suggestions??

Similar question with a bit of news of a driver being developed by Lexmark:
[http://www.linuxquestions.org/questions/debian-26/how-to-make-lexmark-s305-scanner-wifi-work-with-xsane-796857/](http://www.linuxquestions.org/questions/debian-26/how-to-make-lexmark-s305-scanner-wifi-work-with-xsane-796857/)

Some network-connected scanners have built-in web interfaces that can be used to scan (like HP).  Try connecting to its address with a web browser.

---

### Post by crotale on 2010-10-31
Great information in this thread. I just enabled my headless 10.04 as a network scanner server.

However, I also had som permission issues which I did not got solved until I added www-data to the lp group.
To be more specific, the web interface said it couldn't find any printer even though sudo scanimage -L could find it and I could scan locally.

```
sudo adduser www-data lp
```Solved my problem.

---

### Post by unebaguettesvp on 2010-11-08
Hi-

I'm trying to get my network scanner to function. I've been following the guides here and:

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

And I think I am just misunderstanding something. I'm not trying to set up a web interface. I just want the scanner to work over my network.

1. The scanner is properly functioning on the server side.

2. Both, the client and the server, have the package sane-utils installed.

3. I changed /etc/default/saned on the server to RUN=yes (that was easy!)

4. Editing /etc/sane.d/saned.conf is what I think I'm getting confused on. The internal IP address of the server is 192.168.1.102 and the subnet mask is 255.255.255.0. The internal IP address of the client is 192.168.1.103. So, what do I put here? Is 192.168.1.0/24 correct? That didn't work!

5. Also, editing /etc/sane.d/net.conf on the client is confusing me too! What IP address should go there? Can I put the server name? What is the correct syntax?

6. I added saned to the correct group, lp. I made sure that the scanner was owned by the correct group by doing these commands:
sane-find-scanner
AND
ls -al /dev/bus/usb/XXX/XXX
The group was lp.

7. Yes, the server was restarted! A hard restart!

Any help would VERY much appreciated! Both computers are using 10.10.

---

### Post by jhansonxi on 2010-11-08
> **crotale said:**
> ```
sudo adduser www-data lp
```Solved my problem.
On Ubuntu 10.04 (Lucid Lynx) that doesn't work for me with SCSI, USB, and parallel-port scanners.  Are you using a multifunction/AiO device?  That may be the reason.

---

### Post by jhansonxi on 2010-11-08
> **unebaguettesvp said:**
> 3. I changed /etc/default/saned on the server to RUN=yes (that was easy!)I don't have it running all the time (RUN=no).  I use inetd to start it as needed.  To configure it that way change the default control file back and then issue "sudo update-inetd --enable sane-port" which will change the correct line in the /etc/inetd.conf file.

> **unebaguettesvp said:**
> 4. Editing /etc/sane.d/saned.conf is what I think I'm getting confused on. The internal IP address of the server is 192.168.1.102 and the subnet mask is 255.255.255.0. The internal IP address of the client is 192.168.1.103. So, what do I put here? Is 192.168.1.0/24 correct? That didn't work!Looks correct.  My *[saned autoconfig script]("http://jhansonxi.blogspot.com/2010/10/script-for-auto-configuring-saned.html")* does the same thing.

> **unebaguettesvp said:**
> 5. Also, editing /etc/sane.d/net.conf on the client is confusing me too! What IP address should go there? Can I put the server name? What is the correct syntax?Either the IP address or just the hostname.

> **unebaguettesvp said:**
> 6. I added saned to the correct group, lp. I made sure that the scanner was owned by the correct group by doing these commands:
sane-find-scanner
AND
ls -al /dev/bus/usb/XXX/XXX
The group was lp.I think that only works for multifunction/AiO devices which are handled as printers.  To get SCSI or USB scanners to work with saned I have to use my *[Scanner Access Enabler]("http://jhansonxi.blogspot.com/2010/10/scanner-access-enabler.html")*.

---

### Post by unebaguettesvp on 2010-11-09
wow! thanks jhansonxi! so, i edited /etc/sane.d/saned.conf on the server back to 192.168.1.0/24 and i changed /etc/sane.d/net.conf to the ip address of the server. and.... that didn't work!

then i saw your blog post:
[http://jhansonxi.blogspot.com/2010/10/script-for-auto-configuring-saned.html](http://jhansonxi.blogspot.com/2010/10/script-for-auto-configuring-saned.html)

i was about to install your script until i noticed a command on your page:
sudo dpkg-reconfigure sane-utils

i answered one question, whether or not i wanted it to be a standalone server. i clicked yes and that was it! it started working! i have no idea why! but thanks!!!

---

### Post by crotale on 2010-11-09
> **jhansonxi said:**
> On Ubuntu 10.04 (Lucid Lynx) that doesn't work for me with SCSI, USB, and parallel-port scanners.  Are you using a multifunction/AiO device?  That may be the reason.

Yes, it's a multi function unit (HP OfficeJet 7130) and while I don't know what AIO is I can recall seeing it during the hp-setup.

Perhaps what fixed it for me is a special case, but hopefully it can help someone else.

---

### Post by jhansonxi on 2010-11-09
> **crotale said:**
> Yes, it's a multi function unit (HP OfficeJet 7130) and while I don't know what AIO is I can recall seeing it during the hp-setup.[All-in-One]("http://en.wikipedia.org/wiki/All-in-one_printer") (industry slang).  There was some problems printing with these and the old "scanner" group configuration.  The group was removed because [libsane doesn't need it anymore]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/195782/comments/14").

---

### Post by Captain Spectacular on 2010-12-13
Yeah, so I decided today that I wanted to use my scanner in a way that it'd be available to all.  Found this page and a number of other links and gave it a go.

What I have is a permissions problem, I'm sure.  I can't scan as a normal user using Simple Scan, but I can if I run [FONT="Courier New"]gksu simple-scan[/FONT].  Right there I suspect permissions, obviously.  If I run [FONT="Courier New"]sudo scanimage[/FONT], it scans.  Permissions error if I don't use sudo.

The scanner is detected by all the software (ie. Simple Scan after I get the error asking if I want to choose a different scanner, Scanner Server web UI), but I get errors about not being able to scan.

Scanner Access Enabler doesn't detect my scanner.

I am using a Canon PIXMA MP780 multifunction device on Ubuntu Server 10.04 x86 which I expect I may need to restart from time to time as per the sane compatibility chart, but these issues seem unrelated.

Users saned and www-data are added to the lp group.  I added other standard users to the group for poops and giggles too, but that made no difference when running Simple Scan, for example.

RUN_AS_USER=sane or =root doesn't make a difference that I can see.

Here's a couple screenshots that are hopefully helpful (but probably not).

---

### Post by jhansonxi on 2010-12-14
SAE uses scanimage -L and sane-find-scanner through sudo so it should find them.  Unfortunately I don't have a Canon to test.

---

### Post by Captain Spectacular on 2010-12-14
Yeah, I figured running it as root would mean that finding the thing would be a non-issue, but I guess not.

I'm not afraid of manually editing permissions wherever need be, I'm just sort of stumped as everything that everyone else has done has been tried by me (I think so, anyway, ha), and the scanner does work when I run Simple Scan as root, thus negating any hardware or software incompatibilities at that level, anyway.

EDIT:  I just did a chmod 666 on /dev/bus/usb/001/006 and everything works.  So definitely permissions.  I guess this is satisfactory, but I'd rather know what specific permissions to fix.

---

### Post by pqwoerituytrueiwoq on 2010-12-28
i can't seem to the the web based scanner to work i have tryed ever permissions thing in the thread
i can use the scanner on my laptop via easyscan
"No scanner devices were found" is given by the GUI app and  the web app
i even changed it to the beta and still do not have it working
```
scanimage -L
device `hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T' is a Hewlett-Packard psc_2400_series all-in-one
```
i have a HP PCS 2410xi
running xubuntu 10.04 fresh install nothing has been updated

---

### Post by jhansonxi on 2010-12-28
> **pqwoerituytrueiwoq said:**
> i can't seem to the the web based scanner to work i have tryed ever permissions thing in the thread
i can use the scanner on my laptop via easyscan
"No scanner devices were found" is given by the GUI app and  the web app
i even changed it to the beta and still do not have it working
```
scanimage -L
device `hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T' is a Hewlett-Packard psc_2400_series all-in-one
```
i have a HP PCS 2410xi
running xubuntu 10.04 fresh install nothing has been updated

The web server, Linux Scanner Server, uses scanimage with the www-data account.  My [Scanner Access Enabler](http://jhansonxi.blogspot.com/2010/10/scanner-access-enabler.html) is only needed for that account for non-multifunction/AiO (all-in-one) scanners.  For AiO scanners try adding www-data to the lp group by editing the lp entry in "/etc/group" or with the users-admin tool (should be listed as "Users and Groups" in the XFCE menu somewhere).

---

### Post by pqwoerituytrueiwoq on 2010-12-28
```
sudo adduser www-data lp
The user `www-data' is already a member of `lp'.
```my printer/scanner craped out on me ](*,)
now i am using this
```
scanimage -L
device `plustek:libusb:002:003' is a UMAX 3450 flatbed scanner
```and i cant access it via easy scan over the network like it could the other scanner
still not working on the web version

---

### Post by jhansonxi on 2010-12-28
> **pqwoerituytrueiwoq said:**
> 
```
scanimage -L
device `plustek:libusb:002:003' is a UMAX 3450 flatbed scanner
```and i cant access it via easy scan over the network like it could the other scanner
still not working on the web versionFor that scanner you will need to use my enabler.  Note - the enabler has to be used after every reboot as the change is not permanent.

---

### Post by pqwoerituytrueiwoq on 2010-12-29
I managed to fix the printer :)
Port forwarding 6566 (sane-port) and using easy scan/xsane is not a good idea, at least for my hp psc 2410xi 
It will not scan but will screw something up on the scanner and it will not find the end of the scanner bay 
I had to open up the scanner bay (T10 screw driver needed) and move bar back until it saw the edge
I managed to get the web app working I don't know how maybe cause I installed the [FONT=Courier New]libsane-extras[/FONT] package
I am using the beta server scripts
I went through the source and saw this in [FONT=Courier New]inc/header.inc[/FONT]
```
<div id="tab">
<a href="index.cgi?page=config">Configure</a>
</div>

<div id="tab">
<a href="index.cgi?page=scans">Recent Scans</a>
</div>

<div id="tab">
<a href="index.cgi?page=scan">Scan Image</a>
</div>

<div id="tab">
<a href="http://$$SERVER_NAME">$$SERVER_NAME</a>
</div>
```ids are supposed to me unique use a class attribute instead of a id attribute
also update [FONT=Courier New]inc/style.css[/FONT] and [FONT=Courier New]config/style.css[/FONT] to use a class and not a id (use a . not a #) 
also in my opinion adding a border radius to the tabs look better
css:
```
    -moz-border-radius: 5px;
    border-radius: 5px;
    -webkit-border-radius: 5px;
    -o-border-radius: 5px;
```

---

### Post by jhansonxi on 2010-12-29
> **pqwoerituytrueiwoq said:**
> I managed to fix the printer :)
Port forwarding 6566 (sane-port) and using easy scan/xsane is not a good idea, at least for my hp psc 2410xi 
It will not scan but will screw something up on the scanner and it will not find the end of the scanner bay 
I had to open up the scanner bay (T10 screw driver needed) and move bar back until it saw the edge
I managed to get the web app working I don't know how maybe cause I installed the [FONT=Courier New]libsane-extras[/FONT] package
I am using the beta server scriptsThat sounds like a sane driver error.  You should report it to them.
> **pqwoerituytrueiwoq said:**
> I went through the source and saw this in [FONT=Courier New]inc/header.inc[/FONT]
```
<div id="tab">
<a href="index.cgi?page=config">Configure</a>
</div>

<div id="tab">
<a href="index.cgi?page=scans">Recent Scans</a>
</div>

<div id="tab">
<a href="index.cgi?page=scan">Scan Image</a>
</div>

<div id="tab">
<a href="http://$$SERVER_NAME">$$SERVER_NAME</a>
</div>
```ids are supposed to me unique use a class attribute instead of a id attribute
also update [FONT=Courier New]inc/style.css[/FONT] and [FONT=Courier New]config/style.css[/FONT] to use a class and not a id (use a . not a #) 
also in my opinion adding a border radius to the tabs look better
css:
```
    -moz-border-radius: 5px;
    border-radius: 5px;
    -webkit-border-radius: 5px;
    -o-border-radius: 5px;
```My expertise is shell scripts.  I know very little about css/html/Javascript.  I noticed there were some cosmetic problems but didn't know how to fix them.  For instance, there is supposed to be a progress bar displayed during scans but it doesn't show.

Feel free to fix any problems you find since the original developer doesn't have a scanner to work with.  I suggest starting with the beta tarball, add my patch, then make diffs of your changes with:
diff -uN <original file> <modified file> >update.patch

Post the patch or link to it here so the rest of us can try it out.  It might be a while before I get to it myself as I'm really busy with multiple projects.

---

### Post by pqwoerituytrueiwoq on 2010-12-29
i will be happy to send you a mod of the archive i also added a title attribute to the download print and delete buttons
any idea how to configure php to run on the server 
i was going to make a script to delete old scans that are over an hour old
i installed php5 
i know php, js, html, and css
i do not know cgi from looking at the code it looks like a mix of php and c++ (i do not know c++)

---

### Post by jhansonxi on 2010-12-29
> **pqwoerituytrueiwoq said:**
> i will be happy to send you a mod of the archive i also added a title attribute to the download print and delete buttons
any idea how to configure php to run on the serverThe php5 metapackage should have installed everything.  You probably just need to enable the php module in Apache:
```
ln -s /etc/apache2/mods-available/php5.conf /etc/apache2/mods-enabled/php5.conf
ln -s /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/php5.load 
```
 
> **pqwoerituytrueiwoq said:**
> i was going to make a script to delete old scans that are over an hour old
Don't put that in LSS.  Make that a shell script that runs out of cron.
> **pqwoerituytrueiwoq said:**
> i installed php5 
i know php, js, html, and css
i do not know cgi from looking at the code it looks like a mix of php and c++ (i do not know c++)The **[shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)")** tells you it is being run by the shell (sh), Dash in the case of Ubuntu (ls -l /bin/sh).  It is just a shell script.  The page is generated by stdout from the script.  Almost any "echo" that isn't redirected to a file ends up in the generated web page.

---

### Post by pqwoerituytrueiwoq on 2010-12-29
php is working now :)
was going to cron the php script
I attached my modification to the scripts
I wanted to add a 3ed color to the theme system so I could use the 3ed as the page background color but I do not know cpi :(
I fixed non-fatal html bugs and tried to fix the loading picture's display it did not want to load the picture maybe if I were to base64 the image it would work but there goes IE 7 and below support oh-well IE sucks so who cares 
I added Title attributes to the image buttons (print,download, etc.) (tooltips)

---

### Post by jhansonxi on 2010-12-29
> **pqwoerituytrueiwoq said:**
> php is working now :)
was going to cron the php script
I attached my modification to the scripts
I wanted to add a 3ed color to the theme system so I could use the 3ed as the page background color but I do not know cpi :(
I fixed non-fatal html bugs and tried to fix the loading picture's display it did not want to load the picture maybe if I were to base64 the image it would work but there goes IE 7 and below support oh-well IE sucks so who cares 
I added Title attributes to the image buttons (print,download, etc.) (tooltips)Nice improvements.  The rounded corners do look better.  I noticed the localhost button disappeared.  It's useful for navigating back to the main page of a local server.

---

### Post by pqwoerituytrueiwoq on 2010-12-29
sorry about that i commented it out for myself since it is the only thing i have running on it
*goes to uncomment*
edit:
updated attachment

---

### Post by pqwoerituytrueiwoq on 2010-12-29
I just fixed the loading image bug and polished the UI a bit more
and added the ability to delete saved scan settings (all at once)
the favicon file is from [http://www.iconfinder.com/icondetails/46210/16/scanner_icon](http://www.iconfinder.com/icondetails/46210/16/scanner_icon)

To prevent the server from being filled up with scans I made cleaner.php
this will delete scans over 1 hour old it will check for old scans every 5 minutes and delete any old ones
if you want more storage time there is a 3600 in cleaner.php 3600 is 1 hour in seconds
run this command ```
crontab -e
```i used nano
and add this line of code
```
*/5 * * * * php -f /path/to/cleaner.php
```to save in nano press [ctrl]+[O] <--the letter O not the number 0
the press enter
press [ctrl]+[O] to exit nano
you will need php5 and php installed
```
sudo apt-get install php5 php5-cli
```

---

### Post by jhansonxi on 2011-01-05
Updated file attached.  Sorry but I've been busy this week.

I merged in pqwoerituytrueiwoq's changes to date with some code clean-ups to index.cgi (mostly to prevent me from wasting another two hours looking for a bug that was actually an error in manual_scanners.conf).

After some usability concerns I changed the button names in header.inc to make more sense.  I also replaced the "edit config/settings.conf" manually note with something more practical.  Since the settings are encoded in the links it is easier to just bookmark them.

I am encountering some cgi timeouts with long scans but that is an Apache configuration issue.  The default limit is 10 minutes for a cgi to complete.

I think the settings cleanup php function is useful but it adds a dependency on php that didn't exist before.  Not a problem for me but maybe I can make a shell script equivalent later.

---

### Post by edorfaus on 2011-01-05
> **pqwoerituytrueiwoq said:**
> Port forwarding 6566 (sane-port) and using easy scan/xsane is not a good idea
I found this out the hard way too, trying to use ssh port forwarding to gain access via localhost, though not as bad as your experience (my scanner only needed a reboot to clear up).

Eventually I remembered reading something that explains it, in the saned man page:
> **data_portrange** = min_port - max_port[INDENT]Specify the port range to use for the data connection[/INDENT]Basically, the protocol used by saned works similarly to FTP, in that it opens separate TCP/IP connections for each scan, that don't use the sane-port (6566). Thus, the scanning program (easy scan, xsane, scanimage) connects to the scanner control port just fine (since that was forwarded), and sends the command to start a scan, but fails to connect to the scan data port (since that wasn't forwarded), leaving saned waiting for a connection to send the data on, and the scanner in limbo waiting for a scan-completed command or similar...

It might be possible to get it to work using port forwarding if you set the data_portrange to something limited (just a few ports) and then forward all of those ports as well as the sane-port, but I haven't tried this, finding it much easier to just enable access directly to saned from the relevant hosts.

---

### Post by jhansonxi on 2011-01-05
> **edorfaus said:**
> It might be possible to get it to work using port forwarding if you set the data_portrange to something limited (just a few ports) and then forward all of those ports as well as the sane-port, but I haven't tried this, finding it much easier to just enable access directly to saned from the relevant hosts.With firewalls, specifying the data port range is unnecessary and not recommended as per the sane.conf file.  It recommends to use the nf_conntrack_sane kernel module instead.  With UFW (System > Administration > Firewall Manager), the module is added to the IPT_MODULES="..." line in /etc/default/ufw and then only port 6566 needs to be opened.  The other ports are opened by the module as the client and server negotiate them (like port-triggering but smarter).  Probably not going to be useful with SSH.  You could use UFW to lock down the server and still allow saned through a VPN or something and limit the allowed client IPs with UFW.

---

### Post by pqwoerituytrueiwoq on 2011-01-19
> **jhansonxi said:**
> Updated file attached.  Sorry but I've been busy this week.

I merged in pqwoerituytrueiwoq's changes to date with some code clean-ups to index.cgi (mostly to prevent me from wasting another two hours looking for a bug that was actually an error in manual_scanners.conf).

After some usability concerns I changed the button names in header.inc to make more sense.  I also replaced the "edit config/settings.conf" manually note with something more practical.  Since the settings are encoded in the links it is easier to just bookmark them.

I am encountering some cgi timeouts with long scans but that is an Apache configuration issue.  The default limit is 10 minutes for a cgi to complete.

I think the settings cleanup php function is useful but it adds a dependency on php that didn't exist before.  Not a problem for me but maybe I can make a shell script equivalent later.
Just updated my script with the new ones the blank scanner.conf file made it so i could not setup the scanner 
it was found i would go to the scan page it would say none were setup i removed the blank file and it worked
hope you like the css upgrades i made
use of cleaner.php is optional
i would convert the cgi to php if i knew shell scripting

---

### Post by jhansonxi on 2011-01-21
pqwoerituytrueiwoq, I haven't tried your latest changes yet.  Are you using my patches or the original LSS?  I would be surprised if you had problems with the conf file using my patches.

I'm going to merge your changes into my patch in a few days after I test it.

Future:
The resolutions on the scan page are fixed and do not reflect what the selected scanner is capable of.  I can obtain the resolutions from scanimage but I need an example of html where the scanner pull-down changes the resolution (quality) pull-down entries.  I don't know what html the index.cgi needs to output.

I also found [this graphic gadget](http://odyniec.net/projects/imgareaselect/).  Maybe we could use it?  The "preview" pane isn't really useful since it just shows a reduced version of the previous scan.  A "preview" function that generates a low-resolution image (very fast scan) with a selectable scan area would be much more convenient and match the behavior in other scan tools.

Far future:
Probably should consider multi-lingual support.  I know that shell scripts can use gettext but I've never tried it.

Different programing language:
Go for it but I can't help beyond much beyond shell scripts.  The index.cgi is using scanimage and a bunch of grep/sed/regex hacks.  For PHP you'll need a library like libsane or an extension of some sort but I don't know what is available.

Also, Phrank's site just disappeared.  I attached my copy of the original 1.2 Beta 1 tar.

---

### Post by jhansonxi on 2011-01-22
I just discovered [phpSANE](http://sourceforge.net/projects/phpsane/) so a php conversion might be unnecessary.  I'll check it out later.

---

### Post by jhansonxi on 2011-01-25
I did some testing with phpSANE 0.5.1 on Apache2.

Good:
Resolution selection matches scanner capabilities.

Has rudimentary scan area selection.


Bad:
Only supports 1 scanner.

Confusing error messages ("!!!!!!!! ERROR !!!!!!!!" and faulty setting in red).  Errors are rather common.  I had a lot of problems getting a scan out of it.

It doesn't have any image management function.  Just a pop-up window with a temp file link and an instruction to right-click it and save.

Doesn't support scanners on parallel ports.


Security issue:
[http://esikker.dk/vul_40796.php](http://esikker.dk/vul_40796.php)
Not sure if this is fixed or not.

---

### Post by pqwoerituytrueiwoq on 2011-02-04
It was your copy, I think it was a permission issue on the field since they were yours
Added some JavaScript to generate drop down menu content
Quality, brightness, rotate, and scale
probably went overboard on some of them
updated version number to beta 3

@
"I also found [this graphic gadget]("http://odyniec.net/projects/imgareaselect/").   Maybe we could use it?  The "preview" pane isn't really useful since  it just shows a reduced version of the previous scan.  A "preview"  function that generates a low-resolution image (very fast scan) with a  selectable scan area would be much more convenient and match the  behavior in other scan tools."
take a look at [Server_Scanner_Dev.tar.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=182711&stc=1&d=1296858525") 
if you can shell script the math to convert a scale selection to a true selection and have the scanner scan a region this thing will be really nice
it will pass a selection with theses variable names (by default all variables are -1 so ignore then if they are -1)

[LIST]
[*]loc_width
[*]loc_height
[*]loc_x1
[*]loc_y1
[*]loc_x2
[*]loc_y2
[/LIST]
the get variables function in index.cgi will be useful
Edit:
i noticed the new options i added for the rotate did not work here is the new rotate command 
```
convert -rotate "$ROTATE" "/tmp/scan_file$SCANNER.ppm" "/tmp/_scan_file$SCANNER.ppm"
```

---

### Post by jhansonxi on 2011-02-05
> **pqwoerituytrueiwoq said:**
> 
Added some JavaScript to generate drop down menu content
Quality, brightness, rotate, and scale
probably went overboard on some of them
updated version number to beta 3

You definitely went overboard.  It makes the GUI a little too complex.  Most users won't be making changes in 1 degree increments when scanning.  It's easier to do that with a graphics editor like Gimp.
I was about to release my updated patch as beta 3.  I changed mine to beta 4 without the change because of my usability concerns and other reasons (see below).
> **pqwoerituytrueiwoq said:**
> 
take a look at [Server_Scanner_Dev.tar.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=182711&stc=1&d=1296858525") 
if you can shell script the math to convert a scale selection to a true selection and have the scanner scan a region this thing will be really nice
it will pass a selection with theses variable names (by default all variables are -1 so ignore then if they are -1)

[LIST]
[*]loc_width
[*]loc_height
[*]loc_x1
[*]loc_y1
[*]loc_x2
[*]loc_y2
[/LIST]
the get variables function in index.cgi will be useful

Thanks.  Shell scripts can do math with "Arithmetic Expansion" using the "$((expression))" syntax.

The page generated by your modified sample page provides the example code that the shell script needs to generate.  Unfortunately I'm not going to be using it (see below).
> **pqwoerituytrueiwoq said:**
> 
Edit:
i noticed the new options i added for the rotate did not work here is the new rotate command 
```
convert -rotate "$ROTATE" "/tmp/scan_file$SCANNER.ppm" "/tmp/_scan_file$SCANNER.ppm"
```
That's a problem I previously noticed when experimenting.  LSS uses netpbm tools (pnm*) which have a lot of limits.  The imagemagick tools (convert) are better but it would cause a lot of changes to the shell script.  Unfortunately I'm not going to make them (see below).  This is the other reason I didn't want to use your pull-down changes as it drags in another dependency.


Now for the big problem.  Attached is the "scanimage --help -d <device>" output from every scanner I own.  Extract these to a directory and do some greps:
```
grep '\--rotation' scanimage-help-d*
grep '\--mode' scanimage-help-d*
grep '\--speed' scanimage-help-d*

```
That mess is what needs to be parsed to come up with the data.  Parsing text with shell scripts is tedious.  The output from scanimage is so non-uniform it makes it very time-consuming.  Every case has to be handled differently.  Without a database of scanner IDs to pre-select the parsing algorithms, every possible one has to be used with each scanner, then the values from each has to be compared to see which one actually worked.

The "speed" parameter is something I didn't expect and I'm not sure what the effect on scan quality is.

When you grep for "mode" in the scanner help files, notice the Brother MFC-440CN.  It doesn't have a mode for "Color".  Since the mode is hard-coded in scan.inc, scanning fails because it doesn't match what the device supports.  This is another parameter that needs to be generated in the pull-downs dynamically.

As you already realized, having a huge list of resolutions in the pull-down is not helpful, especially since there are more than you added (up to 1600dpi with some of mine).  Some only have a few fixed settings.  If one is specified that the scanner doesn't support, scanimage just picks the next lower one but the user has no way of knowing.  Using the scanner while watching the Apache error log (tail -f /var/log/apache2/error.log) is quite informative.  What's worse is that the scanners report their maximum dpi which is [usually interpolated]("http://en.wikipedia.org/wiki/Image_scanner#Quality") way beyond what the sensor can actually achieve.  Ideally LSS would only show the maximum optical resolution as scaling with a graphics editor is much better than the hardware interpolation.  Then there is the problem of determining how many resolutions to list and what their values will be (especially with scanners supporting 1dpi increments).

Another problem with LSS is security.  It's rather easy to run the system out of space unless /scan/scans is on a separate partition or quota is active.  It seems to me that a better solution would be to have a client-side process in the browser receiving the data in real-time from the server during the scan.  It would be more secure than having the scans from all users on the server where anyone can access or delete them.  I think that is why phpSANE just provides a temp file link for the user instead of a server-side shared directory.


I'm at the point where I can't continue on this project.  I simply don't have the time with my current workload and that is not going to change for several months.  We fixed a lot of bugs over 1.2 Beta 1 and Beta 4 works well enough for my needs.  It would be nice to have some official response from upstream.  I'm not sure what has happened to Phrankdachicken, maybe he was hit by a truck while crossing a road somewhere.

If you want to go further I suggest joining the phpSANE project.  I don't know enough about php to have an opinion about their coding quality but php has to be more efficient to work with than sed/regex in a shell script.

My patch for beta 4 is attached.  It was created by performing a recursive diff on the modified "/var/www/scan" as compared to LSS 1.2 Beta 1 in "/var/www/scan_1.2_Beta1":
```
diff -crBN scan_1.2_Beta1 scan >scan_1.2_Beta4.patch
```

To apply the patch, extract scan_1.2_Beta1.tar to "/var/www/scan".  Put the patch in "/var/www".  Then apply it with:
```
patch -p1 --directory /var/www/scan --input=/var/www/scan_1.2_Beta4.patch
```
This doesn't include the favicon.png which needs to be put in "/var/www/scan/inc/images".

---

### Post by pqwoerituytrueiwoq on 2011-02-05
Sad to hear you do not have the time
imagemagick appears to be pre-installed in ubuntu/xubuntu
so i see little issue with adding it as a dependency
Here is Beta 4 (probably good enough to be a RC)

You can not crop the image unless you just scanned it
You can not crop the image if you just rotated it
should i consider bc and awk dependencies?
i used those commands for from math work

sh math does not support decimals
$((30/60*120) = 0
echo "scale=1; 30/60*120" | bs = 60.0 
echo "scale=0; 30/60*120" | bs = 0 
echo "scale=10; 30/60*120" | bs = 60.0 | awk '{print int($1)}' = 60
edit:
@[jhansonxi]("http://ubuntuforums.org/member.php?u=162029")
noticed you added some color options in your change log that i did not have they are in in this archive
edit2:
forgot to unremove the server name link
Locate this in inc/header.inc
```
<!--
<div class="tab">
<a href="http://$$SERVER_NAME">$$SERVER_NAME</a>
</div>
-->
```
and remove the 1st and last line i posted

---

### Post by jhansonxi on 2011-02-05
> **pqwoerituytrueiwoq said:**
> Sad to hear you do not have the time
imagemagick appears to be pre-installed in ubuntu/xubuntu
so i see little issue with adding it as a dependency
It may be installed by default with ubuntu-desktop but LSS is a server app so ubuntu-server may not include it.  LSS is also not Ubuntu-specific.
> **pqwoerituytrueiwoq said:**
> 
Here is Beta 4 (probably good enough to be a RC)
Is this LSS 1.2 Beta 1 with my Beta 4 patch only?  If you've added more than my patch then you should make it a beta 5 or something.
> **pqwoerituytrueiwoq said:**
> 
You can not crop the image unless you just scanned it
You can not crop the image if you just rotated it
That's part of the problem of not having a true "preview", only a big thumbnail of the previous scan.
> **pqwoerituytrueiwoq said:**
> 
should i consider bc and awk dependencies?
i used those commands for from math work

Yes.  If someone creates a deb package for it then they will want to know.
> **pqwoerituytrueiwoq said:**
> 
sh math does not support decimals
$((30/60*120) = 0
echo "scale=1; 30/60*120" | bs = 60.0 
echo "scale=0; 30/60*120" | bs = 0 
echo "scale=10; 30/60*120" | bs = 60.0 | awk '{print int($1)}' = 60
I guess I didn't think of that.  Another reason to not use shell scripts.  Have you checked out phpSANE?

---

### Post by pqwoerituytrueiwoq on 2011-02-05
I have not yet 
i am not sure how to read the patch file you made 
it has nothing you did in that sadly
would you care to merge the patch into the beta i uploaded
I have not yet
i downloaded it to my laptop and was doing to ftp it to the desktop but i do not have ftp working yet

---

### Post by jhansonxi on 2011-02-05
> **pqwoerituytrueiwoq said:**
> I have not yet 
i am not sure how to read the patch file you made 
it has nothing you did in that sadly
would you care to merge the patch into the beta i uploaded
I have not yet
i downloaded it to my laptop and was doing to ftp it to the desktop but i do not have ftp working yet

To apply the patch just use the patch command (apt-get install patch) and a clean install of LSS 1.2 Beta 1:
patch -p1 --directory /var/www/scan --input=/var/www/scan_1.2_Beta4.patch

---

### Post by pqwoerituytrueiwoq on 2011-02-09
I am working on a php version
and can you geive the the output of this command i need to know how it returns if there are multiple scanners
```
scanimage -f "{\"ID\":%i,\"INUSE\":0,\"DEVICE\":\"%d\",\"NAME\":\"%v %m %t%n\"},"
```
main thing i need to know is if there are line breaks

---

### Post by jhansonxi on 2011-02-09
Attached.

---

### Post by pqwoerituytrueiwoq on 2011-02-09
thanks just noticed what %n did 
people will be able to have different color schemes at the same time in the php one i ma making
just to make sure all this pile of sh does is save the config file and make some readable text to go in the header function right?
```
        grep -q '%i' config/manual_scanners.conf
        if [ $? -eq 0 ]; then
            # Add the manual entries to the list excluding comments and anything without a ID=%i in it
            OP="$OP""$(echo "";grep -E '^[[:space:]]*[^#]' config/manual_scanners.conf | grep -E 'ID=%i')"
# echo "OP w/manual: $OP <br>"
            notsetIDs=$(echo "$OP" | grep -E '^ID=%i')
            while [ "$notsetIDs" != "" ]
            do # Look for %i and replace it with the next highest ID
            # The last line from scanimage has the highest ID so
            # get all the numeric IDs (not %i) and use the last+1
            nextID=$(($(echo "$OP" | sed -n 's/^ID=\([0-9]*\) .*/\1/p' | sed -n '$s/\([0-9]*\)/\1/p')+1))
            OP=$(echo "$OP" | sed "0,/%i/s/^\(ID=\)\(%i\)\(.*\)$/\1"$nextID"\3/")
            notsetIDs=$(echo "$OP" | grep -E '^ID=%i')
            done
        fi
# echo "OP w/indexed manual: $OP <br>" # debug
        # Get rid of extra spaces in names (UMAX Vista-S8 for example)
        OP=$(echo "$OP" | \
        sed ':repeat;s/\(.* \) /\1/;t repeat')

        # Escape forward slashes in the names and write the config file
        # then replace newlines with HTML breaks and save back to OP
        OP=$(echo "$OP" | \
        sed ':repeat;s/\(NAME=.*[^\]\)\//\1\\\//;t repeat' | \
        tee config/scanners.conf | \
        sed 's/^[^=]*=[^=]*=[^=]*=[^=]*=\(.*\)/\1<br>/' | \
        tr -d '\n')

```

---

### Post by jhansonxi on 2011-02-09
> **pqwoerituytrueiwoq said:**
> thanks just noticed what %n did 
people will be able to have different color schemes at the same time in the php one i ma making
just to make sure all this pile of sh does is save the config file and make some readable text to go in the header function right?

Correct.  The first line checks if there are any entries in the manual_scannners.conf (for parallel-port scanners which scanimage doesn't detect).  It figures out the highest ID# from the current list in $OP and merges in the entries from manual_sanners.conf, changing %i to the next highest number.

The next part gets rid of extra spaces in the name.  I think that was just for neatness in the pull-down list.

The last part escapes forward slashes in the names.  The "tee" command forks it to both the scanners.conf file and to the next sed expression which changes newlines to html breaks.  The html-friendly output from sed ends up back in $OP.

---

### Post by pqwoerituytrueiwoq on 2011-02-09
How do I get the data for non-usb printers?
atm what i have only uses scanimage so i guess it lacks parallel support
space striping should not matter as html ignores multiple spaces (unless you use non-breaking spaces)
also what does the -n mean in 'if [ -n "$SET_SAVE" ]; then'

---

### Post by jhansonxi on 2011-02-09
> **pqwoerituytrueiwoq said:**
> How do I get the data for non-usb printers?
Printers?  The file I sent you contains both USB and SCSI scanner devices.
> **pqwoerituytrueiwoq said:**
> 
atm what i have only uses scanimage so i guess it lacks parallel support
That is why manual_scannners.conf exists.  It is manually created based on the settings in SANE.  In LSS, the only difference between it and the output from scanimage for USB and SCSI scanners is the device ID=%i.  It gets replaced with a number when it is merged with the list from scanimage to create the final device list which stored in the scanners.conf file.> **pqwoerituytrueiwoq said:**
> space striping should not matter as html ignores multiple spaces (unless you use non-breaking spaces)I don't remember what the problem with the UMAX was but I had to do that to get it functional.> **pqwoerituytrueiwoq said:**
> 
also what does the -n mean in 'if [ -n "$SET_SAVE" ]; then'
The "[" is a program, also called "test".  Open a terminal and type "man [" or "man test" for the manual page.  The rest of the expression are parameters for the "[" program.  The final "]" is optional as it is ignored.  The "-n" returns true (0) if the length of $SET_SAVE is non-zero.  If there is anything in $SET_SAVE the "then" portion of the statement is processed.

---

### Post by pqwoerituytrueiwoq on 2011-02-09
meant scanner not printer (i have a all in one and typically call it a printer)
i would like some more detail on the parallel settings
is this file generated by a program am i able to extract the parallel scanners from a system file?
sample files would help 
i will try not replacing the excess spaces you can be a genie pig for that if you don't mind may have been a sh issue 
so -n is basically if string length of $myVar is 0 do this

---

### Post by jhansonxi on 2011-02-10
> **pqwoerituytrueiwoq said:**
> i would like some more detail on the parallel settings
is this file generated by a program am i able to extract the parallel scanners from a system file?
sample files would helpA copy is part of my LSS patch.  I'll attach it separately for you (it will have a .txt extension because the forum doesn't allow .conf).  It has to be manually created and needs to match the settings in the corresponding sane conf file for the scanner driver (/etc/sane.d/mustek_pp.conf for example).
> **pqwoerituytrueiwoq said:**
> 
i will try not replacing the excess spaces you can be a genie pig for that if you don't mind may have been a sh issue 
so -n is basically if string length of $myVar is 0 do this
It may have been a problem with the original html code that it generated.

Note:  The correct term is [Guinea pig]("http://en.wikipedia.org/wiki/Guinea_pig").

---

### Post by pqwoerituytrueiwoq on 2011-02-10
ID=%i INUSE=0 DEVICE=mustek_pp:Mustek-600-IIIEP NAME=Mustek 600 IIIEP flatbed scanner
i will be formating the scanners like this
{"ID":4,"INUSE":0,"DEVICE":"mustek_pp:Mustek-600-IIIEP","NAME":"Mustek 600 IIIEP flatbed scanner"}
the format is called JSON (JavaScript Object Notation)
[http://www.jsonlint.com/](http://www.jsonlint.com/) can make them readable for humans
is that your scanner or just an example (or both)
if i can get the divice info without the need for this file i will 
how would one know this info to fill this file out manually?
if you write a script (comment on every line explaining what it does)
that gets the parallel scanners i can probably use that to build a php version
i am probably around 70% conversion 
how ever there are many upgrades i plan to make after i convert it
for example mine will filter redundant scanners[FONT=monospace] on the scanner page not the search page
[/FONT]```
ID=0 INUSE=0 DEVICE=net:linux-desktop.local:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=1 INUSE=0 DEVICE=net:linux-desktop.local:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=2 INUSE=0 DEVICE=net:localhost:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=3 INUSE=0 DEVICE=net:127.0.0.1:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=4 INUSE=0 DEVICE=net:10.0.0.50:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=5 INUSE=0 DEVICE=hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
```

---

### Post by jhansonxi on 2011-02-10
> **pqwoerituytrueiwoq said:**
> ID=%i INUSE=0 DEVICE=mustek_pp:Mustek-600-IIIEP NAME=Mustek 600 IIIEP flatbed scanner
i will be formating the scanners like this
{"ID":4,"INUSE":0,"DEVICE":"mustek_pp:Mustek-600-IIIEP","NAME":"Mustek 600 IIIEP flatbed scanner"}
the format is called JSON (JavaScript Object Notation)
[http://www.jsonlint.com/](http://www.jsonlint.com/) can make them readable for humans
is that your scanner or just an example (or both)
if i can get the divice info without the need for this file i will 
how would one know this info to fill this file out manually?You can't.  The name in particular has to be manually entered.  I think this is because the protocol parallel-port scanners use doesn't supply the information.> **pqwoerituytrueiwoq said:**
> 
if you write a script (comment on every line explaining what it does)
that gets the parallel scanners i can probably use that to build a php versionYou should just use the manual_scanners.conf file format and convert it to JSON when importing it.> **pqwoerituytrueiwoq said:**
> 
i am probably around 70% conversion 
how ever there are many upgrades i plan to make after i convert it
for example mine will filter redundant scanners[FONT=monospace] on the scanner page not the search page
[/FONT]```
ID=0 INUSE=0 DEVICE=net:linux-desktop.local:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=1 INUSE=0 DEVICE=net:linux-desktop.local:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=2 INUSE=0 DEVICE=net:localhost:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=3 INUSE=0 DEVICE=net:127.0.0.1:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=4 INUSE=0 DEVICE=net:10.0.0.50:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
ID=5 INUSE=0 DEVICE=hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T NAME=Hewlett-Packard psc_2400_series all-in-one 
```
You could have a setting that selects between direct connections and network.  On a server it would normally be one or the other, not both.

---

### Post by pqwoerituytrueiwoq on 2011-02-10
so it has to be done manually is there a way i can get part of it?
i will make a form to fill out for this

---

### Post by jhansonxi on 2011-02-10
> **pqwoerituytrueiwoq said:**
> so it has to be done manually is there a way i can get part of it?
i will make a form to fill out for this

My [Scanner Access Enabler]("http://jhansonxi.blogspot.com/2010/10/scanner-access-enabler.html") uses "sane-find-scanner -p" to identify parallel port scanners but it only works for Mustek models.  The correct sane conf files have to be manually edited as well so having a form won't help much.

Parallel port scanners are a rather old technology and rarely seen today.  Even some new PCs don't have parallel ports as USB is used for most everything.  Don't spend a lot of time trying to support them.

---

### Post by pqwoerituytrueiwoq on 2011-02-10
It is a manual edit i am just making a GUI for it
i will add something for musket with that command
can i get some sample output of the command
nrv it needs root access

---

### Post by pqwoerituytrueiwoq on 2011-02-10
How does this look for a GUI for that
[[IMG]http://i55.tinypic.com/33lgvba_th.png[/IMG]]("http://i55.tinypic.com/33lgvba.png")
does not support *"* in the names
URI=Device
should i use device

---

### Post by jhansonxi on 2011-02-11
> **pqwoerituytrueiwoq said:**
> How does this look for a GUI for that
[[IMG]http://i55.tinypic.com/33lgvba_th.png[/IMG]]("http://i55.tinypic.com/33lgvba.png")
does not support *"* in the names
URI=Device
should i use device

Looks good but since you are creating a complete rewrite you shouldn't call it a beta of LSS.  Give it a new name like phpSANER (as compared to phpSANE) or phpLSS.

I'm not sure what you mean by "device".  If you mean the sane device name then ?  If you have two of the same scanner it would be helpful to tell them apart.  Sane device names provide that but an index number would work also.

An information page with the output of "sane --help --device" for each scanner may be useful for troubleshooting or just identifying what the scanner capabilities are.

---

### Post by pqwoerituytrueiwoq on 2011-02-11
ID=0 INUSE=0 **DEVICE**=hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T **NAME**=Hewlett-Packard psc_2400_series all-in-one
```
No command 'sane' found, did you mean:
 Command 'xsane' from package 'xsane' (universe)
 Command 'saned' from package 'sane-utils' (main)
 Command 'save' from package 'atfs' (universe)
sane: command not found

```

---

### Post by jhansonxi on 2011-02-11
> **pqwoerituytrueiwoq said:**
> ID=0 INUSE=0 **DEVICE**=hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T **NAME**=Hewlett-Packard psc_2400_series all-in-one
```
No command 'sane' found, did you mean:
 Command 'xsane' from package 'xsane' (universe)
 Command 'saned' from package 'sane-utils' (main)
 Command 'save' from package 'atfs' (universe)
sane: command not found

```

Sorry.  That should have been "scanimage --help --device <sane device>"

---

### Post by pqwoerituytrueiwoq on 2011-02-11
Here is a pre release; can you check you scanner with the excess spaces in the name.
as far as i know the only thing that does not work is the edit page (new feature)
The stuff you will be able to read is in call to the shell_exec function (search for shell_exec)
while php has some image editing abilities built it i would rather use imagemagick as i will not have to worry with chmoding stuff
it will need version 6.5.9 (or higher) and lucid has a lesser version :(
[https://launchpad.net/ubuntu/+source/imagemagick](https://launchpad.net/ubuntu/+source/imagemagick)
i have a newer version i just need to remove netpbm as a dependency
the script (www-data) must have write access to the config folder and it's sub folder
i now have a untested version that does not use netpbm

---

### Post by pqwoerituytrueiwoq on 2011-02-16
Here is a Release Candidate
it has many new features
here is everyone i can think of (i may have missed some)

[LIST]
[*]image editing
[*]low disk space warning
[*]more scanning options
[*]inline readme file support
[*]downloadable from any page
[*]better color them picker
[*]gui for parallel scanner management
[*]saved settings management
[*]scanners in use have a yellow background in the drop down menu
[*]has a list of installed scanners and details on each one
[*]can alter image contrast
[*]can make images larger
[/LIST]
TODO list:

[LIST]
[*]README touch up
[*]Spell check everything
[*]get someone check IE support (not that anyone cares ;))
[*]Make a screen recording of it (or get someone to)
[/LIST]
Fixes in RC2:

[LIST]
[*]bug resulting from security patch (device list -> scanner details)
[*]patched print.php
[*]tougher security (may still have holes)
[*]minor bug here and there i happened to find
[*]Download server link now now puts a version number in the file name
[/LIST]

---

### Post by jhansonxi on 2011-02-18
I tested PSS on Lucid with the UMAX, Mustek (configured with the parallel form), and SJ 4470c.  They all functioned.

Bugs:
If preview button clicked in "Use Scanner" but file was deleted (through another window or by another user) then Apache error log shows:
File does not exist: /var/www/scan/scans/Scan_0_Feb_18_2011~17-50-10.png

If Scans page is loaded but there are no files, Apache error log shows:
ls: cannot access Preview*: No such file or directory
Since it's just a warning in this case it probably should be suppressed by redirecting stderr to /dev/null or something.  I did that in a few places in LSS.

4470c has some problems with 600dpi (probably a Sane bug).  When it fails:
scanimage: sane_read: Error during device I/O

After unplugging it and replugging in again, attempting to scan results in:
scanimage: open of device rts8891:libusb:002:002 failed: Invalid argument

This is because it was assigned to a different device (002:003) so scanner detection had to be performed again.  I had to run Scanner Access Enabler again also.

You should probably check for these errors and tell the user something more informative than the default "plug in the scanner/check permissions" error message.

It seems to function with IE7 on XP but the loading.gif didn't animate during the scan.

The cropping function works but it's still an annoying behavior with the "preview" scan being the same as a real scan.  Normally a "preview" scan doesn't save the image.  Maybe use a static preview image file name for each scanner but don't show them in the "scanned files" page.

When changing the page (Save Settings, another scan, etc.) the "preview" is lost.  Xsane has separate windows for scans and previews which prevents those problems.  I'm not sure how that should be handled.  Implement tabs with a "preview" and a "last scan" (or multiple previous scans) tabs?

When I use a scanner with multiple items of the same size (8.5x11in. "letter" paper size for example), I usually do one preview, set the scan region, then scan each page without preview or changing the region.  When I scan many smaller items I fit as many as possible on the scanner, do one preview, and only change the scan area for each scan.  With the current behavior it's difficult to do either without performing a preview before each scan.

In the future you might want to add region presets for common paper sizes.  The **[paperconf tool]("http://www.linuxquestions.org/questions/linux-general-1/default-paper-size-for-new-printers-763970/")** may help.  One problem is that the origins of the scan region as defined by scanimage don't necessarily match that of the markings/labels on the scanner.  With the UMAX it refers to top-left x and y but the measurement ruler on the scanner has "0" in the middle of the rear edge.

---

### Post by pqwoerituytrueiwoq on 2011-02-18
So far i fixed these:

[LIST]
[*]If preview button clicked in "Use Scanner" but file was deleted (through  another window or by another user) then Apache error log shows:
File does not exist: /var/www/scan/scans/Scan_0_Feb_18_2011~17-50-10.png
[*]If Scans page is loaded but there are no files, Apache error log shows:
ls: cannot access Preview*: No such file or directory
Since it's just a warning in this case it probably should be suppressed by redirecting stderr to /dev/null or something. I did that in a few places in LSS.
[*]You should probably check for these errors and tell the user something  more informative than the default "plug in the scanner/check  permissions" error message.
[*]Color settings would not work in 2016 (settings will hold for 10 years unless you delete your cookies before then)
[*]Cache is now used for color themes
[/LIST]
Cant fix
[LIST]
[*]It seems to function with IE7 on XP but the loading.gif didn't animate during the scan.
[/LIST]
Will add paper sizes if you can give the the values i need and the corresponding name
Current options:
full : Full Scan
101.6-152.4 : Picture: 4x6
215.9-279.4 : Paper: 8.5x11

You will need to do a hard refresh (ctrl+f5) or clear your cache for the previous scan to work (if you used the previous version)

EDIT:
Security Patch
replace line 39 of index.php with this line:
```
return str_replace("`","",$_REQUEST[$name]);// backticks (`) are striped to prevent the use of malicious code
```

---

### Post by jhansonxi on 2011-02-18
> **pqwoerituytrueiwoq said:**
> [*]If preview button clicked in "Use Scanner" but file was deleted (through  another window or by another user) then Apache error log shows:
File does not exist: /var/www/scan/scans/Scan_0_Feb_18_2011~17-50-10.png
Seems to be fixed.
> **pqwoerituytrueiwoq said:**
> [*]If Scans page is loaded but there are no files, Apache error log shows:
ls: cannot access Preview*: No such file or directorySeems to be fixed.
> **pqwoerituytrueiwoq said:**
> [*]You should probably check for these errors and tell the user something  more informative than the default "plug in the scanner/check  permissions" error message.
The "scanimage: sane_read: Error during device I/O" error results in an incomplete PSS error message:
"Make sure the scanner is turned on and plugged into the scanner server computer.
Or www-data does not have permission to write files to the /var/www/scan/scans folder.
Please read the "

> **pqwoerituytrueiwoq said:**
> [*]Color settings would not work in 2016 (settings will hold for 10 years unless you delete your cookies before then)
[*]Cache is now used for color themesNice! I like this much better than the LSS hack.
> **pqwoerituytrueiwoq said:**
> Will add paper sizes if you can give the the values i need and the corresponding nameThey will vary by country and anything bigger than the scanner's range will have to be filtered out.  Use the "paperconf" tool mentioned in the link I posted to get the sizes.

> **pqwoerituytrueiwoq said:**
> Next version will not have a restore last scan option if you delete the scan in another window/tab
to do this now locate this line near the end of scan.php
if(isset($_COOKIE["scan"])){
change it to 
if(isset($_COOKIE["scan"])&&file_exists("scans/".$_COOKIE["scan"])){I'll take your word for it.  I'm still really busy with other tasks so it will probably be a while before I can test it.

The only usability problem I saw (besides the preview window) is that the in-use highlight in the scanner pull-down is not useful with a single scanner because the selection shading masks the highlight when it is in use.  The lack of real-time busy/free status is another problem (the page has to be refreshed to show current status) but I don't have any idea how you would be able to query the server for that.  AJAX?

There was also a broken symlink in the RC3 file that I don't think was supposed to be there.

---

### Post by pqwoerituytrueiwoq on 2011-02-19
opps not supposed to be there
i edited my above post
the symlink goes to /home/$USER/Public
i put it there for quick file sharing
i suppose i could AJAX it easily enough
every 8 seconds should do 
I will not be supporting IE for this feature
i refuse to bend over backwards to make MS happy
Edit:
you think the color trick (the css themes) i nice you should try it on firefox 4/chrome/opera

---

### Post by pqwoerituytrueiwoq on 2011-02-19
NOW uses AJAX on the scanner page to update the scanners every 8 seconds (assuming you do not lag your computer and make it take longer)
It is optimized for modern browsers ex firefox 3.5+
now over 100kb at max compression
the error messages are fixed

---

### Post by pqwoerituytrueiwoq on 2011-02-19
I still not not understand the paperconf thing i do not know how i can use the string "letter" to get sizes automatically
much less if there scanner can use that size to do any kind of filtering
the next rc will have a new feature in the device list (set default scanner)
it will also have a new information page

[[IMG]http://i55.tinypic.com/fd6hdx_th.png[/IMG]]("http://i55.tinypic.com/fd6hdx.png")

/usr/local/share/applications
has been moved to:
/usr/share/applications
the second part is copy/paste from the blog with the only edit being formating and linking to the local copy of the access enabler

---

### Post by jhansonxi on 2011-02-19
> **pqwoerituytrueiwoq said:**
> I still not not understand the paperconf thing i do not know how i can use the string "letter" to get sizes automatically
much less if there scanner can use that size to do any kind of filtering
The man page for paperconf ("man paperconf") is a little confusing but "paperconf -a" gives you the list.
> **pqwoerituytrueiwoq said:**
> the next rc will have a new feature in the device list (set default scanner)
it will also have a new information page

[[IMG]http://i55.tinypic.com/fd6hdx_th.png[/IMG]]("http://i55.tinypic.com/fd6hdx.png")Looks interesting.

> **pqwoerituytrueiwoq said:**
> /usr/local/share/applications
has been moved to:
/usr/share/applications
the second part is copy/paste from the blog with the only edit being formating and linking to the local copy of the access enabler
The /usr/local subdirectory is used for programs and data that are not handled by the package manager (apt, dpkg, Synaptic).  Don't put anything in the /usr hierarchy manually.  That directory tree (excluding /usr/local) should only be modified by the package manger through deb files.  Normally all programs use /usr/local by default and the distribution packagers change it to /usr when they make a package.

---

### Post by pqwoerituytrueiwoq on 2011-02-19
i tried to put it in that location but it did not exist
but i found desktop files there so i assumed
so what do i do with list (edit nrv paperconf -s letter)

[LIST]
[*]a4
[*]letter
[*]note
[*]legal
[*]etc
[/LIST]
now how do i get the size of the scanner bed?
Wouldn't happen to know a way i can get a ancient parallel scanner working do you?
scoripo pro-e
not that it matters as i have no where to plug it up and i do not think it is supported

---

### Post by jhansonxi on 2011-02-20
> **pqwoerituytrueiwoq said:**
> i tried to put it in that location but it did not exist
but i found desktop files there so i assumedJust create the /usr/local/share/applications directory with the usual root ownership and rwxr-xr-x permissions.
> **pqwoerituytrueiwoq said:**
> so what do i do with list (edit nrv paperconf -s letter)

[LIST]
[*]a4
[*]letter
[*]note
[*]legal
[*]etc
[/LIST]"paperconf -a -N -h -w" gives you most everything.
> **pqwoerituytrueiwoq said:**
> now how do i get the size of the scanner bed?That is in the output from "scanimage --help --device <device>".  The scanimage output files I posted earlier will have lots of examples.  I'm not sure how you would figure out the origin on the scanner as compared to the origin in scanimage.
> **pqwoerituytrueiwoq said:**
> Wouldn't happen to know a way i can get a ancient parallel scanner working do you?
scoripo pro-e
not that it matters as i have no where to plug it up and i do not think it is supported
_[Here is the manufacturer](http://www.tecoimage.com.tw/down.html)_.  There is a manual.pdf in the driver installers (you have to extract it from the exe then uncompress it with msexpand) but it doesn't have much info about the hardware.  I couldn't find anything about sane support for it.

---

### Post by pqwoerituytrueiwoq on 2011-02-20
I need readable to computers not humans for the tray size
happen to have a formula to convert the paper size to the size the scanner uses?
ever think of making a silent scanner enabler and putting a desktop file in this location?
/usr/share/gdm/autostart/LoginWindow
next version will support multiple messages in one page
like when deleting the last scan 
the file xxx was deleted 
there are no images to display
edit:
next RC5 will have:
resolution auto-detect
improved error messages
a bug with my umax will be fixed (full scan only scans a small corner of the bay)
    ```
Geometry:
    -l 0..215mm [0]
       Top-left x position of scan area.
    -t 0..297mm [0]
       Top-left y position of scan area.
    -x 0..215mm [103]
       Width of scan-area.
    -y 0..297mm [76.21]
       Height of scan-area.

```

---

### Post by Juggler00 on 2011-02-20
This is a wonderful "plugin" for Apache--thank you!

First, for anyone looking for simple instructions, I did the following:
Ubuntu 10.04
HP LaserJet 3055 connected via Ethernet DHCP
```

$ sudo aptitude install hplip hplip-cups imagemagick sane-utils tesseract-ocr tessract-ocr-eng 
$ sudo hp-setup -i
/var/www/PHPscanner$ sudo chown root:root PHP-Server-Scanner-1.0RC4.tar.bz2 
/var/www/PHPscanner$ sudo tar -xvvf PHP-Server-Scanner-1.0RC4.tar.bz2 
/var/www$ sudo adduser www-data lp

```

The reason I came across this is I was looking for a way to web-enable my scanner for 2 reasons: 
1. HP's software is terrible for the Mac
2. I wanted to be able to scan from my iPhone

With this in mind, I have a couple of comments/requests:
a) Enable scanning from the document feeder as well as the glass.
b) Building on this, allow for scanning of multiple pages.
c) Add .pdf to "save as" types
d) Since the iPhone is somewhat restrictive in saving images (jpg only), add a "mail-to" link that sends the document as an attachment.

Great work all round... thank you!

---

### Post by pqwoerituytrueiwoq on 2011-02-20
> **Juggler00 said:**
> This is a wonderful "plugin" for Apache--thank you!

First, for anyone looking for simple instructions, I did the following:
Ubuntu 10.04
HP LaserJet 3055 connected via Ethernet DHCP
```

$ sudo aptitude install hplip hplip-cups imagemagick sane-utils tesseract-ocr tessract-ocr-eng 
$ sudo hp-setup -i
/var/www/PHPscanner$ sudo chown root:root PHP-Server-Scanner-1.0RC4.tar.bz2 
/var/www/PHPscanner$ sudo tar -xvvf PHP-Server-Scanner-1.0RC4.tar.bz2 
/var/www$ sudo adduser www-data lp

```The reason I came across this is I was looking for a way to web-enable my scanner for 2 reasons: 
1. HP's software is terrible for the Mac
2. I wanted to be able to scan from my iPhone

With this in mind, I have a couple of comments/requests:
a) Enable scanning from the document feeder as well as the glass.
b) Building on this, allow for scanning of multiple pages.
c) Add .pdf to "save as" types
d) Since the iPhone is somewhat restrictive in saving images (jpg only), add a "mail-to" link that sends the document as an attachment.

Great work all round... thank you!
i advise you to update imagemagick like the readme says unless you don't brightness/contrast to work
@a i would have no way to test this as far as i can see my hardware would not support this the scanner help says it does unless it can scan the printer paper i am trying to keep it generic and not all scanners support a batch option
@c may add a pdf builder page you select the images to put in one (and order)

your welcome glad to see someone using it

@HP LaserJet 3055 connected via Ethernet DHCP
Why would you DHCP a scanner/printer?

I do not think i will add a multi page scan/doc feeder option as i have no idea how i could integrate that into this and i don't have hardware to test this
the pdf is doable

mailto does not support attachments only way you are going to pull that off would be sending a email form php and then you need a mail server

New in RC5

[LIST]
[*]last scan now remembers the scanner you used
[*]last scan now remembers your last non-cropped/rotated scan
[*]crop has been renamed select region as it tell the scanner where to scan (scan page only)
[*]dpi options are all in the range of your scanner (ex no 1600 dpi if scanner does not support it)
[*]scanners that have stupid default scan sizes can not run a full scan (Like my UMAX)
[*]better error message on scan page
[*]multiple message display
[*]set default scanner via device list
[/LIST]

---

### Post by pqwoerituytrueiwoq on 2011-02-21
I made a debug console
should i put a extra space after the readout before the next commend?
it has a Keyboard shortcut to access it as well as a option on the config page

---

### Post by Juggler00 on 2011-02-21
> **pqwoerituytrueiwoq said:**
> i advise you to update imagemagick like the readme says unless you don't brightness/contrast to work
@a i would have no way to test this as far as i can see my hardware would not support this the scanner help says it does unless it can scan the printer paper i am trying to keep it generic and not all scanners support a batch option
@c may add a pdf builder page you select the images to put in one (and order)

your welcome glad to see someone using it

@HP LaserJet 3055 connected via Ethernet DHCP
Why would you DHCP a scanner/printer?

I do not think i will add a multi page scan/doc feeder option as i have no idea how i could integrate that into this and i don't have hardware to test this
the pdf is doable

mailto does not support attachments only way you are going to pull that off would be sending a email form php and then you need a mail server

New in RC5

[LIST]
[*]last scan now remembers the scanner you used
[*]last scan now remembers your last non-cropped/rotated scan
[*]crop has been renamed select region as it tell the scanner where to scan (scan page only)
[*]dpi options are all in the range of your scanner (ex no 1600 dpi if scanner does not support it)
[*]scanners that have stupid default scan sizes can not run a full scan (Like my UMAX)
[*]better error message on scan page
[*]multiple message display
[*]set default scanner via device list
[/LIST]

Fair point on ImageMagick... this was deployed on VirtualBox on my test environment before I role it out to my "production" server. I will make sure I upgrade at that point. 

re:@a -- Understood that your scanner doesn't support this... can I ask you to point me to where in the code you are reading the capabilities of the scanners? I'd like to work on this to allow for batch jobs.

re:DHCP -- The HP printer is Bonjour enabled, so all computers reference it via xxx.local. rather than its IP. Have to say that Bonjour should be standard on all devices; it just works!

thanks again,
   J.

---

### Post by pqwoerituytrueiwoq on 2011-02-21
I would store its ability to use this in the scanners.json file 
this file is made by index.php
look for 
```
# ****************
# Config Page
# ****************
```it will be around line 180
then look for this line (RC5 and up)
```
$res=substr($help,strpos($help,'--resolution ')+13);
```this is the location you will want to mess with
i would test if " --batch-scan" exist in the $help variable and set "batch":1 in the json file for that scanner
BTW RC4 relies entirely on sane's auto-detect and the scanners default settings and does not store anything on the scanner other than it's location and name of which is gathered by 
```
scanimage -f "{\"ID\":%i,\"INUSE\":0,"DEVICE\":\"%d\",\"NAME\":\"%v %m %t\"},"
```here is RC6pre the debug console may come in handy for you

---

### Post by pqwoerituytrueiwoq on 2011-02-21
I got RC6 done
now has paperconfig support as well as custom paper sizes and the ability to delete paper sizes
the paper list updates along with the resolution when the scanner is changes

Anyone care if i messup the scans page for older browsers and IE so i can do what i did with the paper list (columns)
they would not lined up perfectly

---

### Post by jhansonxi on 2011-02-21
> **pqwoerituytrueiwoq said:**
> I need readable to computers not humans for the tray size
happen to have a formula to convert the paper size to the size the scanner uses?
"paperconf -a -N -w -h -m" outputs in mm, the same as "scanimage --help --device <device>".  I don't think that scanimage has any simplified output for parsing by other programs (at least nothing that compares to "-f").
> **pqwoerituytrueiwoq said:**
> ever think of making a silent scanner enabler and putting a desktop file in this location?
/usr/share/gdm/autostart/LoginWindow
Someday when I have more time.
> **pqwoerituytrueiwoq said:**
> next version will support multiple messages in one page
like when deleting the last scan 
the file xxx was deleted 
there are no images to display
edit:
next RC5 will have:
resolution auto-detect
improved error messages
a bug with my umax will be fixed (full scan only scans a small corner of the bay)
    ```
Geometry:
    -l 0..215mm [0]
       Top-left x position of scan area.
    -t 0..297mm [0]
       Top-left y position of scan area.
    -x 0..215mm [103]
       Width of scan-area.
    -y 0..297mm [76.21]
       Height of scan-area.

```

---

### Post by pqwoerituytrueiwoq on 2011-02-21
> **jhansonxi said:**
> Someday when I have more time.
the best way would be too add a -silent option
I managed to figure out the unit without the -m option of paperconf
i managed to convert it to mm so the above rc6 has the paper support
EDIT:
1.0

[LIST]
[*]More accurate paperconf (no more 0.0000000x off)
[*]Better paper size editor (css changes)
[*]Orientation is disabled if the paper will not fit horizontally
[*]paperconf sizes are sorted by name (sorted before conversion to objects)
[*]Recent scan informs the menus that they changed so they run validation code
[*]The script detects the name www-data instead of assuming that is the name (good for trouble shooting)
[*]The link to server main page now works if Apache is not running on port 80
[*]The link to server main page now shows the servers local ip address instead of its name (long names cause display issue)
[*]The link to the server's home page has the name in the tool-tip
[*]Adjusted the css on the config page so the boxes to not jump around
[*]There is a fancy debug log crtl+shift+D (should work on IE)
[*]Fixed up save settings reload (now uses my config function)
[/LIST]

---

### Post by Juggler00 on 2011-02-22
> **pqwoerituytrueiwoq said:**
> I would store its ability to use this in the scanners.json file 
this file is made by index.php
look for 
```
# ****************
# Config Page
# ****************
```it will be around line 180
then look for this line (RC5 and up)
```
$res=substr($help,strpos($help,'--resolution ')+13);
```this is the location you will want to mess with
i would test if " --batch-scan" exist in the $help variable and set "batch":1 in the json file for that scanner
BTW RC4 relies entirely on sane's auto-detect and the scanners default settings and does not store anything on the scanner other than it's location and name of which is gathered by 
```
scanimage -f "{\"ID\":%i,\"INUSE\":0,"DEVICE\":\"%d\",\"NAME\":\"%v %m %t\"},"
```here is RC6pre the debug console may come in handy for you

So I took  a quick look in scanimage and got the following output based on my device (AIO HP LaserJet 3055):
```
:~$ sudo scanimage --help -d hpaio:/net/HP_LaserJet_3055?zc=LJ3055
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information


Options specific to device `hpaio:/net/HP_LaserJet_3055?zc=LJ3055':
  Scan mode:
    --mode Lineart|Gray|Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 75|100|150|200|300|600|1200dpi [75]
        Sets the resolution of the scanned image.
  Advanced:
    --contrast 0..100 [inactive]
        Controls the contrast of the acquired image.
    --compression None|JPEG [JPEG]
        Selects the scanner compression method for faster scans, possibly at
        the expense of image quality.
    --jpeg-quality 0..100 [10]
        Sets the scanner JPEG compression factor. Larger numbers mean better
        compression, and smaller numbers mean better image quality.
    --batch-scan[=(yes|no)] [no]
        Enables continuous scanning with automatic document feeder (ADF).
    --source Auto|ADF [Auto]
        Selects the scan source (such as a document-feeder).
  Geometry:
    --length-measurement Unknown|Unlimited|Approximate|Padded [Padded]
        Selects how the scanned image length is measured and reported, which
        is impossible to know in advance for scrollfed scans.
    -l 0..228.6mm [0]
        Top-left x position of scan area.
    -t 0..381mm [0]
        Top-left y position of scan area.
    -x 0..228.6mm [228.6]
        Width of scan-area.
    -y 0..381mm [381]
        Height of scan-area.

```

It looks like there are several variables associated with batch scanning. If I understand correctly, scanners.json is created the first time a scanner is discovered. This file includes the capabilities of the scanner including resolution, paper size--this is where I would be adding batch capabilities?

---

### Post by pqwoerituytrueiwoq on 2011-02-22
yes that is the location to store it 
that is the easy part
making a gui and processing the files then giving the user the files will be the hard part
it gets harder the farther you go like a video game :lolflag:
edit seems i need to edit my resoluton detection
--resolution 75|100|150|200|300|600|1200dpi [75]

---

### Post by Juggler00 on 2011-02-22
> **pqwoerituytrueiwoq said:**
> yes that is the location to store it 
that is the easy part
making a gui and processing the files then giving the user the files will be the hard part
it gets harder the farther you go like a video game :lolflag:
edit seems i need to edit my resoluton detection
--resolution 75|100|150|200|300|600|1200dpi [75]

Understood... nothing like feature creep ;)

Do you have any documentation in how the functions are split across the different files? Also any insight into the logic you applied? I think this is something I want to tackle, but before I commit it would be nice to know that I don't have to reverse-engineer your existing work!

cheers,
   J.

---

### Post by pqwoerituytrueiwoq on 2011-02-22
i always try to make my code generic
made a few fixes
i added some code to check if the scanner is ADF capable line 285 it is commented out

my script only handled stuff like 75..1200 not 75|100|150|200|300|600|1200
i fixed that

the file are brought in using php's include command/function any code in an included file is run as if it were in the directory that called the file
keeps one file from having 2k+ lines you shoud not need to reverse engineer anything i suck at doing documentation
ex
index.php:
<?php include "path/file.php"; ?>
if file.php look for a file it look starting in the location index.php is not in the path folder

the css file needs ordering and index.php could use that also would make it more readable it does not hurt anything though
BTW i think i solved your phones image saving limitation

new dependency zip
anyone know how to do this with tar?
zip -r out.zip in.png
------------------------------------------------------------
There are 12 screen shots 6 per archive
------------------------------------------------------------
solved bugs/issues:
[LIST]
[*]bug in AJAX if the number of scanners changes
[*]can't tell if a scanner is in use if the mouse is over it (also changed check delay form 8 seconds to 5 seconds)
[*]cant tell if scanner is in use if the mouse if over it
[*]paper size bugs (i think)
[*]resolution detection works on scanners that have a list of resolutions
[*]created workaround for iphones downloading images other than jpg (zip download)
[*]removed excess white space on recent scans page resulting from multiple scan sizes for firefox/chrome/safari the fix does not support non-mozilla and webkit based browsers
[/LIST]

known issues:

[LIST]
[*]debug hot key does not work in chrome (key sequence belongs to bookmark current page)
[*]Some scanners like my umax tell the script there width is 215 mm even though it is more
this makes it so letter is not an option under paper size
[LIST]
[*]Reported:
[LIST]
[*]Width: 215 mm
[*]Height: 297 mm
[/LIST]
 
[*]Actual:
[LIST]
[*]Width: 217.4875 mm
[*]Height: 298.45 mm
[/LIST]
 
[*]Letter Size:
[LIST]
[*]Width: 215.9 mm
[*]Height: 279.4 mm
[/LIST]
 
[/LIST]
 
[/LIST]
[RIGHT][IMG]http://i53.tinypic.com/mh6b02.png[/IMG][/RIGHT]

---

### Post by jhansonxi on 2011-02-23
_[Scanner Access Enabler v1.2]("http://www.mediafire.com/?p1plimo2yf31kl3")_ adds a non-interactive/silent mode via a "-s" parameter.

---

### Post by pqwoerituytrueiwoq on 2011-02-23
Wohoo *goes to ssh install*
hope you enjoy teh paper config thing in the scanner
edit:
this is odd
```
cat /usr/share/gdm/autostart/LoginWindow/scanner-access-enabler.desktop
[Desktop Entry]
Name=Scanner Access Enabler
Comment=Enables non-root access to scanner ports
Exec=gksudo /usr/local/bin/scanner-access-enabler -s
TryExec=/usr/local/bin/scanner-access-enabler -s
Icon=scanner
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;GTK;System;Settings;
```it is not adding the scanner but it is adding the net path for my hp
net:scanner.local:hpaio:/usb/psc_2400_series?serial=MY3ADG51Q56T
it worked without the -s on the previous version
since i know you will ask
```
cat /etc/sane.d/net.conf
# This is the net backend config file.

## net backend options
# Timeout for the initial connection to saned. This will prevent the backend
# from blocking for several minutes trying to connect to an unresponsive
# saned host (network outage, host down, ...). Value in seconds.
# connect_timeout = 60

## saned hosts
# Each line names a host to attach to.
# If you list "localhost" then your backends can be accessed either
# directly or through the net backend.  Going through the net backend
# may be necessary to access devices that need special privileges.
# localhost
#10.0.0.50
#127.0.0.1
#localhost
#linux-desktop.local
```

---

### Post by jhansonxi on 2011-02-23
> **pqwoerituytrueiwoq said:**
> 
this is odd
```
cat /usr/share/gdm/autostart/LoginWindow/scanner-access-enabler.desktop
[Desktop Entry]
Name=Scanner Access Enabler
Comment=Enables non-root access to scanner ports
Exec=gksudo /usr/local/bin/scanner-access-enabler -s
TryExec=/usr/local/bin/scanner-access-enabler -s
Icon=scanner
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;GTK;System;Settings;
```It's not meant to be started by a desktop file but rather from /etc/rc.local:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/local/bin/scanner-access-enabler -s
exit 0
```Its scanner detection shouldn't be affected either way.  It simply uses "scanimage -f "%d%n%v%n%m%n" to get the scanner list (and "sane-find-scanner -q -p"  for parallel devices) and then does a "chmod o+rw" against every device found that doesn't start with "net:".

---

### Post by pqwoerituytrueiwoq on 2011-02-23
thanks,
i have no idea how the net line got in there but it did it seems the script did not run with the desktop file
i hope you like having that paperconf support [server update](http://ubuntuforums.org/attachment.php?attachmentid=184293&d=1298491639)

---

### Post by jhansonxi on 2011-02-24
> **pqwoerituytrueiwoq said:**
> i hope you like having that paperconf support [server update](http://ubuntuforums.org/attachment.php?attachmentid=184293&d=1298491639)Looks really good but I was confused by the paper manager.  The boxes look like check boxes and I thought I was supposed to check which sizes I wanted but clicking one deletes it instead.  A little confusing.

Some of the sizes are English/standard sizes and others are metric.  The A0 through A10 series is metric and is normally shown in mm.  Letter, Legal, and Tabloid are standard are specified in inches.  The ones that round off to increments of 0.25in are probably all inch-based.  An option to switch everything between English/standard rule sizes and metric is probably the easiest way to handle it.  Maybe a cookie?

The debug console is quite nifty.

---

### Post by pqwoerituytrueiwoq on 2011-02-24
how about a tooltip of the mm, it is the same delete icon as everywhere else
i fully tested all version of ie and none work ie6 to ie9 not a single one
ie 6/7 seem to be unable to parse the javascript 
8/9 fail do this bug [http://support.microsoft.com/kb/276228](http://support.microsoft.com/kb/276228) not n issue if you have only 1 scanner
there are a few changes nothing manger has IE error messages changed the logo image to the css file put a title attribute on the paper manager

---

### Post by pqwoerituytrueiwoq on 2011-02-28
fix:

[LIST]
[*]download zip was missing after scan
[*]IE9 now works
[/LIST]
changes:

[LIST]
[*]moved more stuff to css so i could crop some images (loading.gif,preview.png)
[*]now shows server name instead of server address in the header
[*]IE error message touchups
[/LIST]
Edit:
@[jhansonxi]("http://ubuntuforums.org/member.php?u=162029")
i figured out what you meant by check boxes
the image url was /inc/images/delete.png
it should have been inc/images/delete.png
line 42 of paper.php
i attached a patched paper.php file

Edit2:
Just to specify if you use the scanner's paper config page you will be missing the delete icon and have a white square instead unless you are running it from the root directory of the server ex /var/www will be fine while /var/www/scan will be missing the image replace paper.php in the inc folder with the separate attached copy of paper.php

Edit3:
For Google Chrome as well as other browsers the debug console does not work for via hot key you can bookmark this (you must be on the one of the scanner page for it to work)
```
javascript:void(toggleDebug(true));
```

---

### Post by pqwoerituytrueiwoq on 2011-03-01
Now has fancy CSS tooltips
[IMG]http://i52.tinypic.com/118prw2.png[/IMG] was going for something like Ubuntu's 10.04 system tooltips
based on this
[http://codefisher.org/web_applications/css-tooltip](http://codefisher.org/web_applications/css-tooltip)
bet mine works like garbage on IE8, oh well garbage browser displays pages as garbage not like IE8 worked anyway :lolflag:

it also now makes sure tesseract worked and if it fails it will make a blank text file since the app expects a file to exist

---

### Post by jhansonxi on 2011-03-01
> **pqwoerituytrueiwoq said:**
> Now has fancy CSS tooltips
[IMG]http://i52.tinypic.com/118prw2.png[/IMG] was going for something like Ubuntu's 10.04 system tooltips
based on this
[http://codefisher.org/web_applications/css-tooltip](http://codefisher.org/web_applications/css-tooltip)
bet mine works like garbage on IE8, oh well garbage browser displays pages as garbage not like IE8 worked anyway :lolflag:

it also now makes sure tesseract worked and if it fails it will make a blank text file since the app expects a file to exist

I haven't had time to test it.  Some of my scanners have gone to customers so I have less to test with.

When are you going to set up a real web site for PHP Scanner Server instead of just using this forum thread?

---

### Post by linuxbazoka on 2011-03-02
I have just installed the latest version (1.3)on my lucid server.
It works but had problems with the permission.

I miss the possibility to scan to pdf.
I had modded old version I used and added scan to pdf, but this version dos not look the same. 
I don't know what to change to add pdf.
Any tips?

---

### Post by pqwoerituytrueiwoq on 2011-03-02
How did you create the pdf in the old version i will add it if i figure out how to make a pdf
Edit:
Added a PDF download requires php-fpdf to be installed
[IMG]http://i51.tinypic.com/fxseb7.png[/IMG]
it may have issues with really tall scans
like a 50 px wide by 2000 px tall
pdf generation is done in download.php if you make any improvements please post them

New stuff/changes:

[LIST]
[*]moved buttons to css (saved over 1kb of disk space and improves cache)
[*]fancy css tool-tips that appear instantly
[*]download pdf
[*]new dependency php-fpdf
[*]has a new color theme
[*]fixed issue for scanners not be noticed as inactive is you run 2 scanners at the same time
[*]disabled columns in the paper manager for chrome as it is a complete failure
[/LIST]

---

### Post by pqwoerituytrueiwoq on 2011-03-14
Fixes/Upgrades in this version

[LIST]
[*]PDF downloads do not have distorted images and they will always fit on the page
[*]Fixed a few print links (did not open in popups/new tabs)
[*]Convert to text now supports multiple languages
[LIST]
[*]English
[*]German
[*]German fraktu
[*]French
[*]Italian
[*]Dutch
[*]Portuguese
[*]Spanish
[*]Vietnamese
[/LIST]
 
[*]README updates
[*]Reset button on scan page would enable unsupported settings for the scanner (multiple scanners)
[*]IE6/IE7/IE8 support via Google Chrome Frame
[*]Updated IE error messages
[*]Debug Console will now include error messages like a real tty
[*]View Image page now links the image to the raw file
[*]Added tool-tip on the link that goes to this page in the footer
[*]Fixed issue in Firefox 3.0
[*]IE8 fails a little less (without chrome frame)
[/LIST]
Remember to clear your browsers cache after updating

**If anyone wants to try it out send me a pm I will link you to a virtual box setup so you can try it out**

---

### Post by pqwoerituytrueiwoq on 2011-03-18
> **jhansonxi said:**
> I haven't had time to test it.  Some of my scanners have gone to customers so I have less to test with.

When are you going to set up a real web site for PHP Scanner Server instead of just using this forum thread?
technically i did (my desktop is running it)
:lolflag:
i would be too tempted to make demo pages of some kind

---

### Post by pqwoerituytrueiwoq on 2011-03-23
Fix:
[LIST]
[*]Some scanners (or just my UMAX Astra 3400U) sometimes do not turn the scanner light on every time (sometimes it comes on 1/2 way through the scan)
this version will force it on and turn it off after scanning
[/LIST]
**you will need to rescan for scanners with this update**

---

### Post by linuxbazoka on 2011-03-30
Hello.
I have tried the latest 1.2-2 version. Very Nice :D
But It took me a while before I could get it to work, it does not work for me with the default scanning size: Full Scan.
My scanner/printer is a Canon Pixma MP500 (multifunctional)
 
Debug:
```
www-data@192.168.0.1:/mnt/systemdisk/www_mappen/scan$ scanimage -d "pixma:04A9170C_5312A2" -l 0 -t 0 -x 216.069 -y 297.011 --resolution auto --mode color --format=ppm > "/tmp/scan_file0.ppm"
 
www-data@192.168.0.1:/mnt/systemdisk/www_mappen/scan$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Mar_30_2011~15-04-21.jpg"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Preview_0_Mar_30_2011~15-04-21.jpg' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.0.1:/mnt/systemdisk/www_mappen/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Mar_30_2011~15-04-21.png"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Scan_0_Mar_30_2011~15-04-21.png' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.0.1:/mnt/systemdisk/www_mappen/scan$ 
```
 
If I set the size to A4 or something else it works just fine:
 
Debug:
```
www-data@192.168.0.1:/mnt/systemdisk/www_mappen/scan$ scanimage -d "pixma:04A9170C_5312A2" -l 0 -t 0 -x 210 -y 297 --resolution auto --mode color --format=ppm > "/tmp/scan_file0.ppm"

www-data@192.168.0.1:/mnt/systemdisk/www_mappen/scan$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Mar_30_2011~15-32-10.jpg"

www-data@192.168.0.1:/mnt/systemdisk/www_mappen/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Mar_30_2011~15-32-10.png"

www-data@192.168.0.1:/mnt/systemdisk/www_mappen/scan$ 
```

---

### Post by pqwoerituytrueiwoq on 2011-04-05
i had an issue like that myself
the issue is it cant scan that large of a area 
scanner says it can scan more than it really does
can you paste the content of your scanners.json file?
[http://192.168.0.1/scan/config/scanners.json](http://192.168.0.1/scan/config/scanners.json)
i will make a edit for it
edit:
i just remembered why i specifying to scan the size on full scan some scanners do not scan the entire bay by default
you can manually edit the scanners.json with a smaller bay size the numbers are next to WIDTH and HEIGHT
can you post this also?
[http://192.168.0.1/scan/index.php?page=Device%20Notes&action=pixma:04A9170C_5312A2]("http://192.168.0.1/scan/index.php?page=Device%20Notes&action=pixma:04A9170C_5312A2")

Fixes in below version  (**If you are updating from a version below 1.2-2 you will need to rescan for scanners**):

[LIST]
[*]I fixed saving settings with the scan resolution of auto for you and fixed a possible security hole
[/LIST]

[LIST]
[*]the issue you mentioned should also be fixed (i put messages in the debug log) i used a cheap workaround for it there will be issues for scanners that do not report there size correctly and do not run a full scan be default
[/LIST]

---

### Post by Fraoch on 2011-04-06
OK - this is going to sound stupid, but before I configure all this...

This thread assumes the client is a Ubuntu Linux/other Linux machine using sane, correct?

The web access is for additional control of the scanner only, i.e. it doesn't pass the scanned image via HTTP, correct?

The reason I ask is, well, the client computer runs Windows XP.:)  It would be great if I could access the scanner connected to the Ubuntu computer from the client computer but obviously I can't use sane on the client.

Thanks very much for this neat tutorial and what looks to be an extensive script.

---

### Post by pqwoerituytrueiwoq on 2011-04-06
the server needs to be linux the client can be windows 98 as long as you can get a decent web browser on it (try [kmeleon]("http://kmeleon.sourceforge.net/"))
the web ui is used to control xsane on the server
[xsane]("http://www.xsane.org/xsane-win32.html") is available for windows by the way

---

### Post by maerlin on 2011-04-18
Hi, thank you for your hard work. This PHP Scanner Server is amazing. Anyway i have two weird problems:

- I have a Brother MFC-235C (multifunction printer), when i try scanning in mode "Color", the scanner just sits there doing nothing, then spits out:

```
www-data@192.168.1.200:/var/www/scan$ scanimage -d "brother2:bus3;dev1" -l 0 -t 0 -x 215.9 -y 355.6 --resolution 100 --mode color --format=ppm > "/tmp/scan_file0.ppm"

www-data@192.168.1.200:/var/www/scan$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Apr_18_2011~12-50-40.jpg"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Preview_0_Apr_18_2011~12-50-40.jpg' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.1.200:/var/www/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Apr_18_2011~12-50-40.png"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Scan_0_Apr_18_2011~12-50-40.png' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.1.200:/var/www/scan$ 
```

Wich i partially figured out. With Brother scanners the **--mode color** must be specified as **--mode 24bit**. In fact, if i try to scan from a command line with:

```
scanimage -d "brother2:bus3;dev1" -l 0 -t 0 -x 215.9 -y 355.6 --resolution 100 --mode 24bit --format=ppm > "/tmp/scan_file0.ppm"
```

Everything goes fine.


Second problem:

When i try to scan with a mode that should work (greyscale) I get this output:

```
www-data@192.168.1.200:/var/www/scan$ scanimage -d "brother2:bus3;dev1" -l 0 -t 0 -x 215.9 -y 355.6 --resolution 100 --mode gray --format=ppm > "/tmp/scan_file0.ppm"

www-data@192.168.1.200:/var/www/scan$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Apr_18_2011~12-55-20.jpg"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Preview_0_Apr_18_2011~12-55-20.jpg' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.1.200:/var/www/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Apr_18_2011~12-55-20.png"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Scan_0_Apr_18_2011~12-55-20.png' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.1.200:/var/www/scan$ 
```

Again, from command line:

```
> scanimage -d "brother2:bus3;dev1" -l 0 -t 0 -x 215.9 -y 355.6 --resolution 100 --mode gray --format=ppm > "/tmp/scan_file0.ppm"
scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567
> convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Apr_18_2011~12-55-20.jpg"
convert: unable to open image `scans/Preview_0_Apr_18_2011~12-55-20.jpg':  @ error/blob.c/OpenBlob/2498.
```

But, if i try to use a different folder:

```

> convert "/tmp/scan_file0.ppm" -scale 450x471 "/tmp/Preview_0_Apr_18_2011~12-55-20.jpg"
```

The image gets converted. I'm lost, lol.

---

### Post by linuxbazoka on 2011-05-01
> **pqwoerituytrueiwoq said:**
> i had an issue like that myself
the issue is it cant scan that large of a area 
scanner says it can scan more than it really does
can you paste the content of your scanners.json file?
[http://192.168.0.1/scan/config/scanners.json](http://192.168.0.1/scan/config/scanners.json)
i will make a edit for it


Here it is:[PHP][{"ID":0,"INUSE":0,"DEVICE":"pixma:04A9170C_5312A2","NAME":"CANON Canon PIXMA MP500 multi-function peripheral","DPI":"auto||75|150|300|600|1200","WIDTH":216.069,"HEIGHT":297.011,"LAMP":false}]
[/PHP]
> **pqwoerituytrueiwoq said:**
> 
edit:
i just remembered why i specifying to scan the size on full scan some scanners do not scan the entire bay by default
you can manually edit the scanners.json with a smaller bay size the numbers are next to WIDTH and HEIGHT
can you post this also?
[http://192.168.0.1/scan/index.php?page=Device%20Notes&action=pixma:04A9170C_5312A2]("http://192.168.0.1/scan/index.php?page=Device%20Notes&action=pixma:04A9170C_5312A2")


Here: [PHP]Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information

Options specific to device `pixma:04A9170C_5312A2':
  Scan mode:
    --resolution auto||75|150|300|600|1200dpi [75]
        Sets the resolution of the scanned image.
    --mode auto|Color|Gray [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --source Flatbed [Flatbed]
        Selects the scan source (such as a document-feeder).
    --button-controlled[=(yes|no)] [no]
        When enabled, scan process will not start immediately. To proceed,
        press "SCAN" button (for MP150) or "COLOR" button (for other models).
        To cancel, press "GRAY" button.
  Gamma:
    --custom-gamma[=(auto|yes|no)] [yes]
        Determines whether a builtin or a custom gamma-table should be used.
    --gamma-table auto|0..255,...
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
  Geometry:
    -l auto|0..216.069mm [0]
        Top-left x position of scan area.
    -t auto|0..297.011mm [0]
        Top-left y position of scan area.
    -x auto|0..216.069mm [216.069]
        Width of scan-area.
    -y auto|0..297.011mm [297.011]
        Height of scan-area.
  Buttons:
    --button-update
        Update button state
    --button-1  [0]
        Button 1
    --button-2  [0]
        Button 2

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    pixma:04A9170C
[/PHP]
> **pqwoerituytrueiwoq said:**
> 

Fixes in below version  (**If you are updating from a version below 1.2-2 you will need to rescan for scanners**):

[LIST]
[*]I fixed saving settings with the scan resolution of auto for you and fixed a possible security hole
[/LIST]

[LIST]
[*]the issue you mentioned should also be fixed (i put messages in the debug log) i used a cheap workaround for it there will be issues for scanners that do not report there size correctly and do not run a full scan be default
[/LIST]

---

### Post by WeFY-KVQqr on 2011-05-07
Well, somehow this isn't working for me.

[FONT=monospace]sudo tar xvf scan*.tar says:

tar: scan*.tar: Cannot open: No such file or directory

Midnight Commander says something about ignoring trailing spaces.

That archive seems to be wrong.
[/FONT]

---

### Post by pqwoerituytrueiwoq on 2011-05-08
> **WeFY-KVQqr said:**
> Well, somehow this isn't working for me.

[FONT=monospace]sudo tar xvf scan*.tar says:

tar: scan*.tar: Cannot open: No such file or directory

Midnight Commander says something about ignoring trailing spaces.

That archive seems to be wrong.
[/FONT]
be sure you used the cd command to get to the correct folder

---

### Post by pqwoerituytrueiwoq on 2011-05-08
> **linuxbazoka said:**
> Here it is:[PHP][{"ID":0,"INUSE":0,"DEVICE":"pixma:04A9170C_5312A2","NAME":"CANON Canon PIXMA MP500 multi-function peripheral","DPI":"auto||75|150|300|600|1200","WIDTH":216.069,"HEIGHT":297.011,"LAMP":false}]
[/PHP]

only issue i see is a blank scan resolution option
if full scan fails than this command should also fail
```
scanimage -d "pixma:04A9170C_5312A2" --resolution 75 --mode color --format=ppm > "/home/$USER/Desktop/scan_file1.ppm"
```
you should file a xsane bug report

---

### Post by pqwoerituytrueiwoq on 2011-05-08
> **maerlin said:**
> Hi, thank you for your hard work. This PHP Scanner Server is amazing. Anyway i have two weird problems:

- I have a Brother MFC-235C (multifunction printer), when i try scanning in mode "Color", the scanner just sits there doing nothing, then spits out:

```
www-data@192.168.1.200:/var/www/scan$ scanimage -d "brother2:bus3;dev1" -l 0 -t 0 -x 215.9 -y 355.6 --resolution 100 --mode color --format=ppm > "/tmp/scan_file0.ppm"

www-data@192.168.1.200:/var/www/scan$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Apr_18_2011~12-50-40.jpg"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Preview_0_Apr_18_2011~12-50-40.jpg' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.1.200:/var/www/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Apr_18_2011~12-50-40.png"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Scan_0_Apr_18_2011~12-50-40.png' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.1.200:/var/www/scan$ 
```Wich i partially figured out. With Brother scanners the **--mode color** must be specified as **--mode 24bit**. In fact, if i try to scan from a command line with:

```
scanimage -d "brother2:bus3;dev1" -l 0 -t 0 -x 215.9 -y 355.6 --resolution 100 --mode 24bit --format=ppm > "/tmp/scan_file0.ppm"
```Everything goes fine.


Second problem:

When i try to scan with a mode that should work (greyscale) I get this output:

```
www-data@192.168.1.200:/var/www/scan$ scanimage -d "brother2:bus3;dev1" -l 0 -t 0 -x 215.9 -y 355.6 --resolution 100 --mode gray --format=ppm > "/tmp/scan_file0.ppm"

www-data@192.168.1.200:/var/www/scan$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Apr_18_2011~12-55-20.jpg"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Preview_0_Apr_18_2011~12-55-20.jpg' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.1.200:/var/www/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Apr_18_2011~12-55-20.png"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/295.
convert: missing an image filename `scans/Scan_0_Apr_18_2011~12-55-20.png' @ error/convert.c/ConvertImageCommand/2970.
www-data@192.168.1.200:/var/www/scan$ 
```Again, from command line:

```
> scanimage -d "brother2:bus3;dev1" -l 0 -t 0 -x 215.9 -y 355.6 --resolution 100 --mode gray --format=ppm > "/tmp/scan_file0.ppm"
scanimage: rounded value of br-x from 215.9 to 215.88
scanimage: rounded value of br-y from 355.6 to 355.567
> convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Apr_18_2011~12-55-20.jpg"
convert: unable to open image `scans/Preview_0_Apr_18_2011~12-55-20.jpg':  @ error/blob.c/OpenBlob/2498.
```But, if i try to use a different folder:

```

> convert "/tmp/scan_file0.ppm" -scale 450x471 "/tmp/Preview_0_Apr_18_2011~12-55-20.jpg"
```The image gets converted. I'm lost, lol.
will work on fixing that
i was unaware that anything other than Lineart|Gray|Color was used for mode
[FONT=Courier New]scanimage --help[/FONT] output would be useful
you will need to delete some stuff in your tmp folder by running those command you created permission issues for the scanner server

---

### Post by pqwoerituytrueiwoq on 2011-05-10
Release Notes for version 1.2-4
[LIST]
[*]Fixed issues maerlin had (blank resolution option and Color mode issues)
[/LIST]

[LIST]
[*]Also in the drop down menus I changed degree to ° it did not look right being spelled out and having the % not spelled out in the other menus
[*]Disabled the code I added to turn the light on/off as it did not do what I wanted it to do (guess I will tamper with the warm-up option)
[*]**You will need to rescan for scanners with this update**
[/LIST]
Should I remove the "auto" option, some scanners have it under quality and I am wondering if I should limit it to numbers only?

---

### Post by pqwoerituytrueiwoq on 2011-06-22
New Version:

[LIST]
[*]Fixed issue with default scan option if the default scanner was in use
[*]New PDF option (pdf download opens a dialog) (only tested in firefox)
[*]Added a dirty hack to make a hp deskjet 2050 use a full scan
[*]If you try to save a color setting and have cookies disabled it will tell you
[*]Fixed a bug in download.php tmp is not /tmp
[/LIST]

---

### Post by Agg23 on 2011-06-22
> **pqwoerituytrueiwoq said:**
> New Version:

[LIST]
[*]Fixed issue with default scan option if the default scanner was in use
[*]New PDF option (pdf download opens a dialog) (only tested in firefox)
[*]Added a dirty hack to make a hp deskjet 2050 use a full scan
[*]If you try to save a color setting and have cookies disabled it will tell you
[/LIST]

This version's download does not work...

---

### Post by pqwoerituytrueiwoq on 2011-06-22
> **Agg23 said:**
> This version's download does not work...
on which page?
and which download form (norm,zip,pdf,etc)

---

### Post by Agg23 on 2011-06-22
> **pqwoerituytrueiwoq said:**
> on which page?
and which download form (norm,zip,pdf,etc)

The actual download from UbuntuForums.  The tar is corrupted.

**Edit:**  I also cannot get any of the beta 1.2 versions to run at all...  Maybe if you could put them on your site so I can wget them?

---

### Post by pqwoerituytrueiwoq on 2011-06-22
wtf why is it generating corrupt archives on me
*clean out /tmp folder*
edit re-uploaded in the old post

---

### Post by Agg23 on 2011-06-22
Could you put them up on your website?

**Edit:**  I tried the new version and I still can't access it.  Does the guide [here]("http://scannerserver.online02.com/node/12") not work?  When I access my index.php, the browser just downloads it...

**Edit 2:**  No need to put them on your website now...  I still can't get it to work though

---

### Post by pqwoerituytrueiwoq on 2011-06-22
go through the readme installation notes
sudo apt-get install tar apache2 php5 php5-cli imagemagick sane-utils tesseract-ocr
the original was made in cgi this one is in php

---

### Post by Agg23 on 2011-06-22
Thank you!  I finally got the beta running...  I guess I needed php5-cli.  I already had php5...

Now to see about customization...

---

### Post by pqwoerituytrueiwoq on 2011-06-22
php5-cli should not be required for basic functionality
the php version is not a beta it has its own version number and it is not a beta

---

### Post by Agg23 on 2011-06-22
Oh...  I see now it isn't beta.

What are the permissions on the files?  When I try to modify them on my main machine, then ftp them over, I get permission errors...  How would I set them correctly?

---

### Post by pqwoerituytrueiwoq on 2011-06-23
i never did figure out how to get ftp right
the permissions required for function are the readme search for chmod/chown
for other files root can do it
ex: gksu geany /var/www/inc/style.php

---

### Post by silince on 2011-09-06
Sorry if I've missed something here - is there a way of adding the pdf functionality without installing the new version?  Or should I start from scratch...

---

### Post by tieutu2004 on 2011-09-14
Help me with
 I have installed server scan HP2400
 Scan directly on ubuntu is good. but when I scan over the network, the following error.
 I do not know how to adjust again. I'm just a novice on linux
 would help
 thanks

---

### Post by pqwoerituytrueiwoq on 2011-09-16
you missed something in the install notes is what i looks like to me
if i had to guess it was this:
```
sudo adduser www-data lp
```that message you received is meant for someone moding the page trying to send a hack they found in 

since that is a incorrect error message can you post the content on this page?
[http://scan.modun.com.vn/config/scanners.json](http://scan.modun.com.vn/config/scanners.json)
[http://scan.modun.com.vn/scan/config/scanners.json]("http://scan.modun.com.vn/config/scanners.json")
should be one of those locations

---

### Post by tieutu2004 on 2011-09-18
Thank you
 I solved the problem then
 But, there is a small problem here is
 1 - I scanned a png file then the error can not be opened, but scan the file JPE is no problem at all
 2 - I can not print pdf file

---

### Post by pqwoerituytrueiwoq on 2011-09-18
1. Please elaborate @.@
2. "can't print" sounds like a driver issue, try this command:
```
sudo add-apt-repository ppa:hplip-isv/ppa;sudo apt-get update;sudo apt-get upgrade
```

---

### Post by khan_zerbero on 2011-11-08
Hi

Im trying to use this on a office eviroment with a Ubuntu 11.10, i've already installed the Scanner Server CGI script ver 1.2_Beta1 with no problems, the server detects the scanner and i can scan from every network's computer but is not the same with PHP Scaner Server.

So I read about the Php Scanner and it seems quite complete and usefull than scanner server script, however i have troubles with it. It does not detect the scanner. I did all the stuff you suggested on this threat with no succes.

First, the debug log showed this:
```
www-data@mexmarserver:/var/www/portal/scan$ scanimage -f "{\"ID\":%i,\"INUSE\":0,\"DEVICE\":\"%d\",\"NAME\":\"%v %m %t\"}," netdiscovery: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference netdiscovery: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference {"ID":0,"INUSE":0,"DEVICE":"pixma:04A92686_177CJ9gt0024","NAME":"CANON Canon imageClass MF6500 multi-function peripheral"}, www-data@mexmarserver:/var/www/portal/scan$ 
```


I changed the libnss-files.so.2 name file to libnss_files.so.6 and the debug log changed to this:

```
www-data@mexmarserver:/var/www/portal/scan$ scanimage -f "{\"ID\":%i,\"INUSE\":0,\"DEVICE\":\"%d\",\"NAME\":\"%v %m %t\"}," Floating point exception {"ID":0,"INUSE":0,"DEVICE":"smfp:XEROX WorkCentre 3550 on 192.168.1.252","NAME":"XEROX WorkCentre 3550 on 192.168.1.252 Flatbed Scanner"},{"ID":1,"INUSE":0,"DEVICE":"pixma:04A92686_177CJ9gt0024","NAME":"CANON Canon imageClass MF6500 multi-function peripheral"}, www-data@mexmarserver:/var/www/portal/scan$ 
```

It is deteting a XEROX, this printer is attached to the net but I have a Canon MFC6550 attached by usb port to my computer, and this printer/scanner is detect by the Scanner Server script.
PHP Scanner still cant detect the Canon printer.

I've already execute the Scanner Access Enabler with no succes, it keep saying in xmessage box: "No scanner devices were found"

This is what i get when typing scanimge -L in terminal:

```
Floating point exception
device `smfp:XEROX WorkCentre 3550 on 192.168.1.252' is a XEROX WorkCentre 3550 on 192.168.1.252 Flatbed Scanner
device `pixma:04A92686_177CJ9gt0024' is a CANON Canon imageClass MF6500 multi-function peripheral
```

I can scan with xsane and with scanner server script ver 1.2_Beta1

The PHP Scanner Server im using is 1.2-5 and it does not work for me.

Can someone give a hand with this problem.

Thanks a lot.

---

### Post by pqwoerituytrueiwoq on 2011-11-08
> I changed the libnss-files.so.2 name file to libnss_files.so.6you should use a symlink for this instead or renaming it other programs will expect libnss-files.so.2 while some will want libnss-files.so.6

i would guess the float point exception is the issue the script does not expect this value in the output
post what this gives you
```
cat /var/www/portal/scanconfig/scanners.json
```also post what this gives you (trying to rule out permission issues)
```
scanimage -f "{\"ID\":%i,\"INUSE\":0,\"DEVICE\":\"%d\",\"NAME\":\"%v %m %t\"},"
```i am hoping at least i can create your scanners.json file by hand so you can replace it this is looking more like a occlet issue atm but i can not be sure i will try a virtual box later (maybe tomorrow)

can you post the output of theses 2 comands
```
scanimage --help -d "smfp:XEROX WorkCentre 3550 on 192.168.1.252"
scanimage --help -d "pixma:04A92686_177CJ9gt0024"
```

---

### Post by khan_zerbero on 2011-11-08
[B]This is what i get:

~$ cat /var/www/portal/scanconfig/scanners.json
[/B]cat: /var/www/portal/scanconfig/scanners.json: No existe el archivo o el directorio[B]

 $ scanimage -f "{\"ID\":%i,\"INUSE\":0,\"DEVICE\":\"%d\",\"NAME\":\"%v %m %t\"},"

[/B]Floating point exception
{"ID":0,"INUSE":0,"DEVICE":"pixma:04A92686_177CJ9gt0024","NAME":"CANON Canon imageClass MF6500 multi-function peripheral"},user@server

**scanimage --help -d "smfp:XEROX WorkCentre 3550 on 192.168.1.252"**

```
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information
Violación de segmento

```

**scanimage --help -d "pixma:04A92686_177CJ9gt0024"**

```
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information

Options specific to device `pixma:04A92686_177CJ9gt0024':
  Scan mode:
    --resolution auto||75|150|300|600dpi [75]
        Sets the resolution of the scanned image.
    --mode auto|Color|Gray [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --source Flatbed|Automatic Document Feeder [Flatbed]
        Selects the scan source (such as a document-feeder).
    --button-controlled[=(yes|no)] [no]
        When enabled, scan process will not start immediately. To proceed,
        press "SCAN" button (for MP150) or "COLOR" button (for other models).
        To cancel, press "GRAY" button.
  Gamma:
    --custom-gamma[=(auto|yes|no)] [inactive]
        Determines whether a builtin or a custom gamma-table should be used.
    --gamma-table auto|0..255,... [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
  Geometry:
    -l auto|0..216.747mm [0]
        Top-left x position of scan area.
    -t auto|0..297.011mm [0]
        Top-left y position of scan area.
    -x auto|0..216.747mm [216.747]
        Width of scan-area.
    -y auto|0..297.011mm [297.011]
        Height of scan-area.
  Buttons:
    --button-update
        Update button state
    --button-1 <int> [0]
        Button 1
    --button-2 <int> [0]
        Button 2

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

Floating point exception
List of available devices:
    smfp:XEROX WorkCentre 3550 on 192.168.1.252 pixma:04A92686

```

Thanks for your time.

---

### Post by pqwoerituytrueiwoq on 2011-11-08
create the file **/var/www/portal/scanconfig/scanners.json** with this as its content and chown the file to www-data
```
[{"ID":0,"INUSE":0,"DEVICE":"pixma:04A92686_177CJ9gt0024","NAME":"CANON Canon imageClass MF6500 multi-function peripheral","DPI":"75|150|300|600","MODE":"Color|Gray","WIDTH":216.747,"HEIGHT":297.011}]
```that will get your usb scanner working manually

confirm that your networked scanner is networked properly (see 1st post in thread)

try using ubuntu 10.04 in a virtual box with a bridged net adapter and see if it works (if it works the problem is ubuntu 11.10)
i have tested networked scanners and did not have any issues but they were shared via ubuntu and they all worked properly
the "Floating point exception" is what is causing the problem you are having

---

### Post by khan_zerbero on 2011-11-09
Ok thank you.

Editing the scanners.json and adding the line works for me.

I supossed was the Ubuntu version, however is working now editing the file manually, i did a symlink to libnss-files.so.2 as you suggested before too.

Thanks again for it, im understanding the way it works, hope in the next releases we can scan using the ADF scanner, that would be great. I dont know too much about programing but i'll try to look if there's a way to acces the ADF and of course wait for your releases.

Thanks.

---

### Post by pqwoerituytrueiwoq on 2011-11-09
that was a quick work around
you need something working for the time being
how is the networked scanner networked?
does it work via simple scan?

this is how the script expects the output of the command, but the text "Floating point exception\n" ("\n" = line break) is making it not in that format which causes a error
this is a networked scanner
```
chad@lucid-laptop:~$ scanimage -L
device `net:10.0.0.1:hpaio:/usb/Officejet_4500_G510g-m?serial=CN12JF10VM05CQ' is a Hewlett-Packard Officejet_4500_G510g-m all-in-one
chad@lucid-laptop:~$ scanimage -f "{\"ID\":%i,\"INUSE\":0,\"DEVICE\":\"%d\",\"NAME\":\"%v %m %t\"},"
{"ID":0,"INUSE":0,"DEVICE":"net:10.0.0.1:hpaio:/usb/Officejet_4500_G510g-m?serial=CN12JF10VM05CQ","NAME":"Hewlett-Packard Officejet_4500_G510g-m all-in-one"},chad@lucid-laptop:~$
```i would think disabling the xerox it in /etc/sane.d/net.conf would remove the error message in the command and let the script work as expected with your canon scanner

can you post the output of 
scanimage --help
please use code tags
i will attempt to make the xerox work manually (assuming it shows up in there)

---

### Post by khan_zerbero on 2011-11-09
Ok since english is not my mother language (i guess you already notice that, lol)  i'll try to anwser that cuestions:

** how is the networked scanner networked?**
I have a small network of 8 computers atached to a switch  and this is attached to a DSL modem gateway, it gives IP addres in automatic mode.

So my ubuntu get an automatic ip addres (192.168.1.104 ) and this has de Canon scanner attached. However i create a virtual host called mserver  so to acces the php scanner i type mserver/scan in the browser. I have some other services in it.

All the services including  php scanner "web" can be accesed by any computer attached to the local net. Even by winbugs computers.

The access list is configured with 192.168.1.0/24

i have another multifunction printer (XEROX) that is attached to the Switch too. It has it's own ethernet card and server software.

**[COLOR=black] does it work via simple scan?[/COLOR]**
My Canon 6550 works percfectly fine with Simple Scan App, XSane Image scanning program, i can use the ADF with those. I can scan too with scanimage command in the terminal and with the Scanner Server script 1.2_Beta1 downloaded from [http://scannerserver.online02.com/](http://scannerserver.online02.com/)

I hope I've answered. If you need more data or I can help with anything else let me know.


EDIT

I get this:
```

$ scanimage --help
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information
netdiscovery: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

Options specific to device `pixma:04A92686_177CJ9gt0024':
  Scan mode:
    --resolution auto||75|150|300|600dpi [75]
        Sets the resolution of the scanned image.
    --mode auto|Color|Gray [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --source Flatbed|Automatic Document Feeder [Flatbed]
        Selects the scan source (such as a document-feeder).
    --button-controlled[=(yes|no)] [no]
        When enabled, scan process will not start immediately. To proceed,
        press "SCAN" button (for MP150) or "COLOR" button (for other models).
        To cancel, press "GRAY" button.
  Gamma:
    --custom-gamma[=(auto|yes|no)] [inactive]
        Determines whether a builtin or a custom gamma-table should be used.
    --gamma-table auto|0..255,... [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
  Geometry:
    -l auto|0..216.747mm [0]
        Top-left x position of scan area.
    -t auto|0..297.011mm [0]
        Top-left y position of scan area.
    -x auto|0..216.747mm [216.747]
        Width of scan-area.
    -y auto|0..297.011mm [297.011]
        Height of scan-area.
  Buttons:
    --button-update
        Update button state
    --button-1 <int> [0]
        Button 1
    --button-2 <int> [0]
        Button 2

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

netdiscovery: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib/i386-linux-gnu/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
List of available devices:
    pixma:04A92686

```I'll disable the xerox printer and let you know what happend.
(Ok so english is not my first language, haha).

EDIT2.
**Ok its confirmed, disabling the Xerox network printer i can scan with Canon and php scanner server.**

---

### Post by pqwoerituytrueiwoq on 2011-11-09
i edited my last post 
if you give the output of [FONT=Courier New]scanimage --help[/FONT] i may be able to get both working
i noticed the language thing when i looked at some of your command output and i could not read the text for humans in it
(in English it is referred to as 1st language not mother language not that anyone cares)

---

### Post by pqwoerituytrueiwoq on 2011-11-09
if you connect the xerox via usb to the scanner server or share it via another linux system i bet it will work i hope you like how i went out and included web based image editing
that really comes in handy if you are suck using Win XP on a guest account with out any thing installed for that
you may want to file a up stream bug report with the xerox with xane
or bug the scanners manufacture with it the most likely issues is they used spaces in the scanners name

---

### Post by khan_zerbero on 2011-11-09
I decide leave the xerox out of linux server scanner.

Well, again, im stuck with the Canon but is another problem.

I can scan from it when i press the Scan Image button the software does everything even the scanner does its job (i can see the light scanner working), it creates the scan_file0.pnm in /tmp/ folder  but when convert try to do its stuff it cant access scans folder (or at least i think that is happening), showing this:

```

/var/www/portal/scan$ scanimage -d "pixma:04A92686_177CJ9gt0024" -l 0 -t 0 -x 216.747 -y 297.011 --resolution auto --mode Gray --format=ppm > "/tmp/scan_file0.ppm" 
www-data@mexmarserver:/var/www/portal/scan$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Nov_9_2011~18-56-24.jpg" convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298. convert: missing an image filename `scans/Preview_0_Nov_9_2011~18-56-24.jpg' @ error/convert.c/ConvertImageCommand/2940. 
www-data@mexmarserver:/var/www/portal/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Nov_9_2011~18-56-24.png" convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298. convert: missing an image filename `scans/Scan_0_Nov_9_2011~18-56-24.png' @ error/convert.c/ConvertImageCommand/2940.
```So i already chown www-data scans folder and chmod 775 too but it still cant convert image and cant show it in the browser, i think it cant write even when it has permission.

I change the owner to www-data to the portal folder, this one keeps inside scan and scans folders.
/var/www/portal/scan/scans

I'll try yo use Scanner  Access Enabler but it always says: "No scanner devices were found".

Thank you again for the support.

---

### Post by pqwoerituytrueiwoq on 2011-11-09
```
sudo rm /tmp/scan_file0.ppm
```see if it works then
the assess enabler is to enable usb access for it to be able to scan
certain scanners need it to work like my umax but others like my hp and your canon do not

edit: 
run this see if you get a error message from it 
```
scanimage -d "pixma:04A92686_177CJ9gt0024" -l 0 -t 0 -x 216.747 -y 297.011 --resolution auto --mode Gray --format=ppm > "~/Desktop/scan_file0.ppm"
```
i think you may have a 0 byte scan if not the other command should fix it

---

### Post by khan_zerbero on 2011-11-10
It shows this error:

```
**~$ scanimage -d "pixma:04A92686_177CJ9gt0024" -l 0 -t 0 -x 216.747 -y 297.011 --resolution auto --mode Gray --format=ppm > "scan_file0.ppm"**

scanimage: open of device pixma:04A92686_177CJ9gt0024 failed: Invalid argument
``````
$ **scanimage -T**
scanimage: open of device pixma:04A92686 failed: Access to resource has been denied
```
Is odd i think i did something wrong because i could scan from the terminal with scanimage command before and now it shows: Invalid argument.

EDIT: Ok forget the last thing, i resolve it adding my user to the lp group.

It scans perfectly with this command:
```

~$ scanimage -d "pixma:04A92686_177CJ9gt0024" -l 0 -t 0 -x 216.747 -y 297.011 --resolution auto --mode Gray --format=ppm > "scan_file0.ppm"
scanimage: rounded value of br-x from 216.747 to 216.747
scanimage: rounded value of br-y from 297.011 to 297.011

```

---

### Post by pqwoerituytrueiwoq on 2011-11-10
since that worked odds are the 1st command should fix it
if it does it is cause you copy/pasted the scan command www-data used and www-data could not delete your scan

---

### Post by khan_zerbero on 2011-11-10
www-data can delete the scan but the problem is tha it can not write in /var/www/portal/scan/scans

I can scan in the terminal with the command line, if you see the scanner server debug console we can realise that www-data can scan too in fact it creates the scan-file0.pnm in tmp folder but when www-data executes **convert** command it shows that error but the scan-file0.pnm is deleted when convert is executed from tmp folder.

```
scanimage -d "pixma:04A92686_177CJ9gt0024" -l 0 -t 0 -x 216.747 -y 297.011 --resolution auto --mode Gray --format=ppm > "/tmp/scan_file0.ppm"  
www-data@mexmarserver:/var/www/portal/scan$ **convert** "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Nov_10_2011~11-36-59.jpg"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298. 
convert: missing an image filename `scans/Preview_0_Nov_10_2011~11-36-59.jpg' @ error/convert.c/ConvertImageCommand/2940. 
www-data@mexmarserver:/var/www/portal/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Nov_10_2011~11-36-59.png"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298.
convert: missing an image filename `scans/Scan_0_Nov_10_2011~11-36-59.png' @ error/convert.c/ConvertImageCommand/2940.
```www-data owns **portal** folder, owns **scan** folder and owns **scans** folder, this last one with chmod 775.

this is the path: /var/www/portal/scan/scans

www-data owns from **portal** to **scans** read-write permissions.

I dont realise why it cant write in scans folder or if theres another problem.

---

### Post by pqwoerituytrueiwoq on 2011-11-10
```
sudo chown www-data /var/www/portal/scan/scans; 
sudo chown -R www-data /var/www/portal/scan/scans
```
maybe that will get it

---

### Post by khan_zerbero on 2011-11-10
I did chown www-data and chmod before. However i tried again with those commands and is the same problem.

```
scanimage -d "pixma:04A92686_177CJ9gt0024" -l 0 -t 0 -x 216.747 -y 297.011 --resolution auto --mode Gray --format=ppm > "/tmp/scan_file0.ppm"  www-data@mexmarserver:/var/www/portal/scan$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Nov_10_2011~12-46-14.jpg"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298.
convert: missing an image filename `scans/Preview_0_Nov_10_2011~12-46-14.jpg' @ error/convert.c/ConvertImageCommand/2940. 
www-data@mexmarserver:/var/www/portal/scan$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Nov_10_2011~12-46-14.png" 
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298.
convert: missing an image filename `scans/Scan_0_Nov_10_2011~12-46-14.png' @ error/convert.c/ConvertImageCommand/2940.
```
Maybe is another thing not just permmissions, the "improper image header" message does not tell you something?
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298.

---

### Post by pqwoerituytrueiwoq on 2011-11-10
when i had that error it was cause [FONT="Courier New"]scan_file0.ppm[/FONT] was 0 bytes as a result of my scanner being dumb ad reporting a bay size it can't use
i think i have also had that as a result of there being a [FONT="Courier New"]scan_file0.ppm[/FONT] in my /tmp folder
[FONT="Courier New"]sudo rm /tmp/scan_file0.ppm[/FONT] and see if it works
if that does not get it i will try remote assistance if that is ok with you

---

### Post by khan_zerbero on 2011-11-10
There's no files in tmp folder, every time i scan the file is created and automatic deleted by the scanner server however i always look into it for remainning files, im starting to belive is not a permissions stuff.

I scaned from a winbugs computer with Letter Size instead of Full Scan and Color instead of Gray Scale or Auto Mode and it scaned with no problem and showed the scan in the scanner server window howerver if i try to scan again after that it does take a long long time to start scanning.

I'm scanning in tiff and png format file and it does it's job but still takes a long time to scan again.

I guess the size and gray scale mode for de MFC6550 Canon printer is the problem, or the Canon printer itself lol. 

I execute this command nex to the first scan, it shows that error:

**$ scanimage -T**
```
scanimage: scanning image of size 640x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1920 bytes...    FAIL Error: Error during device I/O

```If i wait like 10 min and execute it again:
**$ scanimage -T**
```
scanimage: scanning image of size 640x877 pixels at 24 bits/pixel
scanimage: acquiring RGB frame, 8 bits/sample
scanimage: reading one scanline, 1920 bytes...    PASS
scanimage: reading one byte...        PASS
scanimage: stepped read, 2 bytes...     PASS
scanimage: stepped read, 4 bytes...     PASS
scanimage: stepped read, 8 bytes...     PASS
scanimage: stepped read, 16 bytes...     PASS
scanimage: stepped read, 32 bytes...     PASS
scanimage: stepped read, 64 bytes...     PASS
scanimage: stepped read, 128 bytes...     PASS
scanimage: stepped read, 256 bytes...     PASS
scanimage: stepped read, 512 bytes...     PASS
scanimage: stepped read, 1024 bytes...     PASS
scanimage: stepped read, 2048 bytes...     PASS
scanimage: stepped read, 2047 bytes...     PASS
scanimage: stepped read, 1023 bytes...     PASS
scanimage: stepped read, 511 bytes...     PASS
scanimage: stepped read, 255 bytes...     PASS
scanimage: stepped read, 127 bytes...     PASS
scanimage: stepped read, 63 bytes...     PASS
scanimage: stepped read, 31 bytes...     PASS
scanimage: stepped read, 15 bytes...     PASS
scanimage: stepped read, 7 bytes...     PASS
scanimage: stepped read, 3 bytes...     PASS
```No problems after 5 or 10 minutes, and i can scan again.

Im spending our time (sorry about that) trying to get it functional  through the scanner server and  maybe people here wont even use it. I  just think server scanner is a great idea, i already showed it to a  coworker scanning a document from my smartphone and, he is excited with  the idea.

Ok, i've to go to eat something. I'll be back and do more test. I'm sure you are a bussy person so if you want we can continue later.

Thank you for your assistance.

---

### Post by pqwoerituytrueiwoq on 2011-11-10
try converting to gray scale after you have scanned in color via image editing on the scannner
hp scanners tend to work good btw

---

### Post by khan_zerbero on 2011-11-11
Ok i've been testing with your suggestion as reference.

Trys:

**1. Quality**: 150 dpi
**Size**: Letter 8.5x11
**Mode**: Color
**File:** .tiff
**Results**: It scans with no problems, but i've to wait like 10 min to use the scanner again and even to print. Large file size: 1.3 MB
**Editing**: It frezze and do nothing.
**To PDF**: I click on the pdf icon and save the file but the file does not open, pdf reader (Document Viewer) shows a message: "Cant Open document, simple text/plan document not supported."

**2. Quality**: 150 dpi
**Size:** Letter 8.5x11
Mode: Color
**File:** png
**Results**: It scans with no problemas, no waiting time to scanning again or printing. large file size: 3.5 MB
**Editing**: I can edit with no problems. Change to gray sacale mode reduce the file size to: 1.3 MB, png file type.
**To PDF**: Can click on pdf icon and save the file (1.3 MB size), the file can be openned with any pdf reader.

**3. Quality**:75 dpi
**Size**: letter 8.5x11
**Mode**: Gray Scale
**File**: png
**Results**: It scans with no problems, no waiting time to scanning again or printing. Size: 118 KB
**Edinting**. I can edit with no problems.
**To PDF**. Can click on pdf icon and save the file (119 KB size), the file can be oppenned with any pdf reader.

I think the problem is .**tiff** type, If i scan whit this type or if i edit changin the png or jpg to tiff, it do nothing and frezze the scanner some minutes.

I did a test in a winbugs pc, scanning the same document with 75 DPI and gray scale mode and using other software, the file i got is 69.7 KB size. Is there a way get a file this size in Linux PHP Scanner Server? is that a sane stuff?

So, the server scanner is working if we dont use tiff file type but the files sizes are larger than it should be. I mean, using the same scanner config (Quality,Size,Mode) and another software instead of server scanner.

---

### Post by pqwoerituytrueiwoq on 2011-11-11
> It scans with no problems, but i've to wait like 10 min to use the scanner again and even to print. Large file size: 1.3 MB
sounds like a driver issue to be but is the server scanner telling you the scanner is in use
> It frezze and do nothing.
can you post a copy of the scan (and the thumbnail) both files are located in the scans folder?
i would think since this is a large file it may take longer to process the edit
also post your editing options you selected

the current version of the php server scanner is 1.2-5

---

### Post by BigCityCat on 2011-11-19
Everything works fine till I enable the firewall. I have 6566 port allowed. Not sure what is going on.

---

### Post by pqwoerituytrueiwoq on 2011-11-19
enable port 80 for the web server (scanner server)
enable port 631 for networked printing
enable port 6566 for remote scanning via simple scan

---

### Post by BigCityCat on 2011-11-19
> **pqwoerituytrueiwoq said:**
> enable port 80 for the web server (scanner server)
enable port 631 for networked printing
enable port 6566 for remote scanning via simple scan

I have all those enabled. At first my printer wouldn't work through the firewall either but I found a solution for it by opening TCP 515 and UDP 1155. I'm using an all in one epson stylus nx420 that epson provides a linux driver for. Only the scanner will not work with firewall on. I tried all the solutions in this thread but no change. Here is sudo watch netstat -anlp with my firewall off and attempting scan. Can you see anything that would help from this info?

> Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      1187/cupsd
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      1883/dropbox
tcp        0      0 192.168.1.71:33989      98.136.48.84:5050       ESTABLISHED 2071/telepathy-haze
tcp        0      0 192.168.1.71:50573      199.47.216.147:80       ESTABLISHED 1883/dropbox
tcp        0      0 192.168.1.71:45370      98.139.143.40:80        TIME_WAIT   -
tcp       38      0 192.168.1.71:39539      199.47.216.173:443      CLOSE_WAIT  1883/dropbox
tcp        0      0 192.168.1.71:57448      107.20.249.63:443       ESTABLISHED 1883/dropbox
tcp        0      0 192.168.1.71:54823      76.13.117.181:80        TIME_WAIT   -
tcp        0      0 192.168.1.71:34195      192.168.1.69:1865       ESTABLISHED 2681/simple-scan
tcp6       0      0 :::5298                 :::*                    LISTEN      2115/telepathy-salu
tcp6       0      0 :::631                  :::*                    LISTEN      1187/cupsd
tcp6       0      0 :::445                  :::*                    LISTEN      831/smbd
tcp6       0      0 :::6566                 :::*                    LISTEN      1135/saned
tcp6       0      0 :::139                  :::*                    LISTEN      831/smbd
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1453/dhclient
udp        0      0 192.168.1.255:137       0.0.0.0:*                           1665/nmbd
udp        0      0 192.168.1.71:137        0.0.0.0:*                           1665/nmbd
udp        0      0 0.0.0.0:137             0.0.0.0:*                           1665/nmbd
udp        0      0 192.168.1.255:138       0.0.0.0:*                           1665/nmbd
udp        0      0 192.168.1.71:138        0.0.0.0:*                           1665/nmbd
udp        0      0 0.0.0.0:138             0.0.0.0:*                           1665/nmbd
udp        0      0 0.0.0.0:45413           0.0.0.0:*                           877/avahi-daemon: r
udp        0      0 0.0.0.0:631             0.0.0.0:*                           1187/cupsd
udp        0      0 0.0.0.0:17500           0.0.0.0:*                           1883/dropbox
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           877/avahi-daemon: r
udp6       0      0 :::55847                :::*                                877/avahi-daemon: 

---

### Post by pqwoerituytrueiwoq on 2011-11-19
run a port scan on your own system make sure you can see each of the ports
system->administration->network tools
also be sure you are using tcp/udp respectfully (that has screwed with me before)

---

### Post by BigCityCat on 2011-11-19
> **pqwoerituytrueiwoq said:**
> run a port scan on your own system make sure you can see each of the ports
system->administration->network tools
also be sure you are using tcp/udp respectfully (that has screwed with me before)

I did a port scan on 192.168.1.71 (not sure if this is what you wanted). Not sure how to find network address. Firewall is enabled.

139 open netbios-ssn
445 open microsoft-ds
631 open ipp
5298 open unkown
6566 open sane-port
17500 open unkown
58323 open unkown

---

### Post by pqwoerituytrueiwoq on 2011-11-19
if you are trying to use the web based server scanner port 80 is not open
are you just trying to get it to work with simple scan/xsane
you can get your address from the ifconfig command

---

### Post by BigCityCat on 2011-11-19
> **pqwoerituytrueiwoq said:**
> if you are trying to use the web based server scanner port 80 is not open
are you just trying to get it to work with simple scan/xsane
you can get your address from the ifconfig command

Hmmm in my firewall rules 80 is open maybe I need to do udp on that.
Yes trying to use simple scan cause it works when the firewall is disabled. With firewall enabled I open simple scan and it says no scanner detected.
Yes I used ifcofig but there was a lot info there. I'm pretty sure that was the correct network address.

---

### Post by BigCityCat on 2011-11-19
I have 80 tcp allow out. Do I need more than that? I did configure my printer using the web access local host. Ran the scan again same info but I have more open than that. F*** it I'm gonna just disable the firewall if I wanna scan. I't's not worth the hassell. Thanks for trying anyway. I'm happy my wireless printer is working in Ubuntu anyway.

---

### Post by pqwoerituytrueiwoq on 2011-11-19
80 is tcp

---

### Post by Catlike on 2012-01-07
Wow. You guys are SCARY! I don't understand one jot nor tiddle of this! Hope I don't need to understand it all in order to make our wireless network function with a Mac, a PC on Oneiric Ocelot, and the Canon MX860... Yikes.

---

### Post by jhansonxi on 2012-01-07
> **Catlike said:**
> Wow. You guys are SCARY! I don't understand one jot nor tiddle of this! Hope I don't need to understand it all in order to make our wireless network function with a Mac, a PC on Oneiric Ocelot, and the Canon MX860... Yikes.
An [image scanner]("http://en.wikipedia.org/wiki/Image_scanner") is like a photocopier.  You put a picture on its scanning glass and it makes a graphics file from it for your computer.  This thread is about sharing an image scanner over a network with other computer users.  If you don't have an image scanner then this thread isn't going to solve any problems for you.

---

### Post by kingofkya on 2012-03-04
Hey, I have a issue i just can not figure out with this php scanner server. I have the debug console turned on which produces the messages below, but what strange if thouse same commands manualy in www-data's shell "su www-data" it runs the commands fine. As does root. So i am confused to why this is failing.

What I have tried:
Scanning in other modes greyscale etc..
chmod 770 the /scans directory
Running commands as www-data
Lighttpd also has same issues.
chmod 777 the /dev/bus/usb  (had to do this in the past)

What confuses me is why manual entering commands works.
Also there are no errors in /var/log/apache/error.log 


  ```
www-data@hs2:/var/www$ scanimage -d "pixma:04A9173A_98884F" -l 0 -t 0 -x 216.069 -y 297.011 --resolution 75 --mode gray --format=ppm > "/tmp/scan_file0.ppm"

www-data@hs2:/var/www$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Mar_4_2012~18-47-41.jpg"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298.
convert: missing an image filename `scans/Preview_0_Mar_4_2012~18-47-41.jpg' @ error/convert.c/ConvertImageCommand/2940.
www-data@hs2:/var/www$ convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Mar_4_2012~18-47-41.png"
convert: improper image header `/tmp/scan_file0.ppm' @ error/pnm.c/ReadPNMImage/298.
convert: missing an image filename `scans/Scan_0_Mar_4_2012~18-47-41.png' @ error/convert.c/ConvertImageCommand/2940.
www-data@hs2:/var/www$ 
```

Ps: You relly need a project page for this simple but useful script.

---

### Post by pqwoerituytrueiwoq on 2012-03-04
if you ran the scan command as your self you will nee to remove the file for www-data to be able to save the scan 
[FONT="Courier New"]rm /tmp/scan_file0.ppm[/FONT]
going to make it detect that and give a message about it

---

### Post by kingofkya on 2012-03-04
Sorry yeah I made sure i did that before I tried the scanner app again. Another  thing i observed is it is creating the file in /tmp.I can run ls -l and i see the file growing then the errors show up in the debug console and tthe scan file then vanishes.

---

### Post by pqwoerituytrueiwoq on 2012-03-04
does this work?

```
scanimage -d "pixma:04A9173A_98884F" -l 0 -t 0 -x 216.069 -y 297.011 --resolution 75 --mode gray --format=ppm > "~/Desktop/scan.ppm"
convert "~/Desktop/scan.ppm" -scale 450x471 "~/Desktop/Preview_0_Mar_4_2012~18-47-41.jpg"
convert "~/Desktop/scan.ppm" -alpha off "~/Desktop/Scan_0_Mar_4_2012~18-47-41.png"

```

---

### Post by kingofkya on 2012-03-04
This is a headlesssystem so i dont have /desktop however this does work.

```


The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Sun Mar  4 19:58:08 2012 from 10.0.0.231
root@hs2:~# scanimage -d "pixma:04A9173A_98884F" -l 0 -t 0 -x 216.069 -y 297.011 --resolution 75 --mode gray --format=ppm > "/root/scan.ppm"
scanimage: rounded value of br-y from 297.011 to 297.011

root@hs2:~# convert "/root/scan.ppm" -scale 450x471 "/root/Preview_0_Mar_4_2012~18-47-41.jpg"
root@hs2:~# convert "/root/scan.ppm" -alpha off "/root/Scan_0_Mar_4_2012~18-47-41.png"
root@hs2:~# ls
cups-windows-6.0                   Scan_0_Mar_4_2012~18-47-41.png
cups-windows-6.0-source.tar.gz     scanner-access-enabler-1.2.tar.bz2
hplip-3.12.2                       scanner-access-enabler.desktop
hplip.run                          scan.ppm
Preview_0_Mar_4_2012~18-47-41.jpg  webmin_1.580_all.deb


```

---

### Post by kingofkya on 2012-03-04
As does this: (note the username)
```

root@hs2:/var/www# su www-data
$ bash
www-data@hs2:~$ scanimage -d "pixma:04A9173A_98884F" -l 0 -t 0 -x 216.069 -y 297                      .011 --resolution auto --mode color --format=ppm > "/tmp/scan_file0.ppm"
scanimage: rounded value of br-y from 297.011 to 297.011
www-data@hs2:~$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Ma                      r_4_2012~20-11-59.jpg"
www-data@hs2:~$  convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Mar_4_20                      12~20-11-59.png"
www-data@hs2:~$
```

---

### Post by pqwoerituytrueiwoq on 2012-03-04
can you run the command without being root?
you may need to use the scanner access enabler

I did see your post before you edited it and saw you are running 2.6.32-5 which is lucid's kernel and lucid does not have a new enough version of imagemagick there are instructions in the readme (FAQ section) for that

---

### Post by pqwoerituytrueiwoq on 2012-03-04
> **kingofkya said:**
> As does this: (note the username)
```

root@hs2:/var/www# su www-data
$ bash
www-data@hs2:~$ scanimage -d "pixma:04A9173A_98884F" -l 0 -t 0 -x 216.069 -y 297                      .011 --resolution auto --mode color --format=ppm > "/tmp/scan_file0.ppm"
scanimage: rounded value of br-y from 297.011 to 297.011
www-data@hs2:~$ convert "/tmp/scan_file0.ppm" -scale 450x471 "scans/Preview_0_Ma                      r_4_2012~20-11-59.jpg"
www-data@hs2:~$  convert "/tmp/scan_file0.ppm" -alpha off "scans/Scan_0_Mar_4_20                      12~20-11-59.png"
www-data@hs2:~$
```
please use the same command options for the scan
```
scanimage -d "pixma:04A9173A_98884F" **-l 0 -t 0 -x 216.069 -y 297.011 --resolution 75 --mode gray --format=ppm** > "./scan.ppm"
```some scanners are stupid and report a size they can not scan and telling them to scan a region that is not scan-able causes a error like a empty ppm file which causes that error in imagemagick
if they can mess up the size who knows what else they can mess up so lets keep the same options in use

---

### Post by kingofkya on 2012-03-04
But why would the commands still work, under www-data user?
I can update image magic but i don't think that is it I know its a issue if i try to use the brightness option but in this cases i don't think it applies. Also running as a standard user it produces a output simmer to my second post where it was running as www-data.

Thanks for your help so far.

---

### Post by kingofkya on 2012-03-04
Also i used thous options as that the commands scanner service was showing in debug console.

---

### Post by kingofkya on 2012-03-04
Here the command you requested.

scanner-user@hs2:~$ scanimage -d "pixma:04A9173A_98884F" -l 0 -t 0 -x 216.069 -y 297.011 --resolution 75 --mode gray --format=ppm > "./scan.ppm"
scanimage: rounded value of br-y from 297.011 to 297.011
scanner-user@hs2:~$ ls -l
total 552
-rw-r--r-- 1 scanner-user scanner-user 559561 Mar  4 20:28 scan.ppm
scanner-user@hs2:~$

---

### Post by pqwoerituytrueiwoq on 2012-03-04
can you comment out this line in the index.php file (near the end of the file)
[FONT=Courier New]@unlink("/tmp/scan_file$SCANNER.ppm");[/FONT]
[PHP]            exe("tesseract \"/tmp/_scan_file$SCANNER.tif\" \"scans/$S_FILENAMET\" -l \"$LANG\"",true);
            unlink("/tmp/_scan_file$SCANNER.tif");
            if(!file_exists("scans/$S_FILENAMET.txt"))//in case tesseract fails
                SaveFile("scans/$S_FILENAMET.txt","");
        }
        else{
            exe("convert \"/tmp/scan_file$SCANNER.ppm\" -alpha off \"scans/$S_FILENAME\"",true);
        }
       // @unlink("/tmp/scan_file$SCANNER.ppm");

        # Check if image is empty and post error, otherwise post image to page
        if(!file_exists("scans/$P_FILENAME")){
            Print_Message("Could not scan",'<p style="text-align:left;margin:0;">This is can be cauesed by one or more of the following:</p>'.
                '<ul><li>The scanner is not on.</li><li>The scanner is not connected to the computer.</li>'.
                '<li>You need to run the <a href="index.php?page=Access%20Enabler">Access Enabler</a>.</li>'.
                (file_exists("/tmp/scan_file$SCANNER.ppm")?"<li>Removeing <code>/tmp/scan_file$SCANNER.ppm</code> may help.</li>":'').
                '<li><code>'.$user.'</code> does not have permission to write files to the <code>'.getcwd().'/scans</code> folder.</li>'.
                '<li>You may have to <a href="index.php?page=Config">re-configure</a> the scanner.</li></ul>'.$notes,'left');
        }
        else{
            Update_Links($S_FILENAME);
            Update_Preview("scans/$P_FILENAME");
        }[/PHP]then run the web scanner
then upload [FONT=Courier New]/tmp/scan_file0.ppm[/FONT] (use a .tar.gz file on these forums for that)
once you do that run [FONT=Courier New]rm /tmp/scan_file0.ppm[/FONT] and undo the change to index.php

---

### Post by kingofkya on 2012-03-04
There, Its a Zip i dont have a linux system or 7-zip handy to make tar.gz.

Sample header:
```
scanimage: rounded value of br-y from 297.011 to 297.011
P6
# SANE data follows
638 877
255
('%('%1Jo¡Íáàçæãççäééäéçåéèåèèæêç
```

---

### Post by pqwoerituytrueiwoq on 2012-03-04
there is your issue
invalid image

will upload a fixed version in a couple minutes

---

### Post by pqwoerituytrueiwoq on 2012-03-05
Release Notes for version 1.2-6

[LIST]
[*]Fixed issue that resulted in corrupt image scans with some scanners
[*]Added error message for common error that results from copy/pasting terminal commands
[*]Added suppressed output notice in the Debug Console for certain commands
[/LIST]
Known issues (will be fixed in the next release):

[LIST]
[*]Spelling errors in readme file (lines 34/35)
[*]The exe function could use a little code cleanup
[*]Typo on config page in the debug log section (py should be by)
[/LIST]
Up coming features:

[LIST]
[*]Tool tips fade in
[*]When 2+ scanners are found it will point out a feature on the scanner list page
[*]Messages will have a close button
[*]Upload scans to imgur.com
[*]Better icon consistency (no more hidden buttons that should be disabled)
[/LIST]

---

### Post by kingofkya on 2012-03-05
Fixed above

---

### Post by pqwoerituytrueiwoq on 2012-03-05
i kinda uploaded and found a mistake and removed it about to re-upload it as a edit
edit got it uploaded now
[http://ubuntuforums.org/showthread.php?t=1519201&page=18#179](http://ubuntuforums.org/showthread.php?t=1519201&page=18#179)

---

### Post by kingofkya on 2012-03-05
Bingo Thanks a lot, shoot me your paypal email. I want to pay you for your time.:)

---

### Post by pqwoerituytrueiwoq on 2012-03-08
Release notes for 1.2-7
[LIST]
[*]Fixed spelling errors in readme file
[*]The exe function could use a little code cleanup
[*]Fixed typo on config page in the debug log section (py should be by)
[*]Tool tips fade in
[*]When 2+ scanners are found it will point out a feature on the scanner list page
[*]Messages will have a close button
[*]Upload scans to imgur.com (Tip: Go to the configure page)
[*]Better icon consistency (no more hidden buttons that should be disabled)
[*][B][COLOR=Red]New dependency php5-curl ([/COLOR][FONT=Courier New][COLOR=Red]sudo apt-get install php5-curl;sudo service apache2 restart[/COLOR][/FONT][COLOR=Red]) without doing this you will not get imgur to work with this[/COLOR]
[/B]
[/LIST]
Be sure to clear cache or do a hard refresh on a page after updating to this version
if you find any bugs let me know
Upcoming features
[LIST]
[*] Edit page will work on text files [http://i.imgur.com/qptwr.png](http://i.imgur.com/qptwr.png)
[*] Move "Parallel Scanner Congifuration" link from "Server Scanner Settings" box to the "Scanners" box
[*] Fix spelling of Configuration (Congifuration)
[/LIST]

---

### Post by pqwoerituytrueiwoq on 2012-03-09
[LIST]
[*] Edit page will work on text files [http://i.imgur.com/qptwr.png](http://i.imgur.com/qptwr.png)
[*] Move boxes around on the Configuration page
[*] Fix spelling of Configuration (Congifuration) (and other various spelling errors)
[*]Fixed up some css issues ('Paper List' and 'Server Scanner Settings')
[*]Fixed image size (scan thumbnails) in Google Chrome Frame on scans page
[*]Fixed imgur.com upload issue on scans page
[*]Chrome frame will not active on IE9 if it is installed
[*]Orientation is no longer blank after scanning in IE9 when orientation option is disabled
[*]Added e-mail feature (Only tested with Gmail)
[LIST]
[*]If you use this feature out side of your local network you should enable http**s**
[*]You should make sure your router is secured (prevent someone from changing your DNS servers) which you should do anyway
[*]If you have more than one recipient the email will be sent with undisclosed recipients (aka Bcc)
[*]If you have a need to add a custom message to a email send it to your self and forward it with a edit (i may add a custom message feature at some point)
[/LIST]
 
[/LIST]
I did run into a issues with uploading to imgur with chrome i added some code to try to debug it and it fixed just decided to work :confused: so if you get a invalid JavaScript object notation error, let me know
EDIT:
there is a error in the readme there is a fixed version at github

[SIZE=4]Moving project to [github]("https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/downloads")[/SIZE]
hopefully that works out:lolflag:

---

### Post by shad0wca7 on 2012-06-10
I'd been rolling around the net trying to find updates for this and finally found this thread - awesome work! :D

---

### Post by silince on 2012-07-06
Hi - I notice that even after cropping, the download to pdf function has a margin on the right hand side - is there a way of rermoving this?  I've been scanning A4 btw.

---

### Post by pqwoerituytrueiwoq on 2012-07-06
sorry,i dont think that can be done as long as i have no way to convert between pixels (px) and points (pt)

the only way i was able to get it on the page converting things to percentages then i had to see if it was taller than wide... idk how to explain it from here

if *[page height / 100] - [page width / 100] <= [image width / 100] - [image height / 100]* assume if the image's width fits while maintaining the aspect ratio so will the height and vice-versa

I am not very good at coming up with formulas so there may be flaws in that

to center a object that will fit horizontally i would do this:[I]
([container width]-[content width])/2[/I] that is my left margin
the problem comes when the container is measured in pt and the content is measured in px

if you figure out a formula that you think will work post it and i will try it

---

### Post by jhansonxi on 2012-07-08
I updated scanner-access-enabler to v1.4 which corrects a detection bug in v1.3 (basically it didn't detect anything).  You can download it from [my MediaFire account here]("http://www.mediafire.com/?4r1aw9ix9ayb0u0").

---

### Post by pqwoerituytrueiwoq on 2012-07-09
thanks for the info
there was a version 1.3 did i miss that or not note it as a version update?
was 1.3 the one you added the -s option?

---

### Post by jhansonxi on 2012-07-09
> **pqwoerituytrueiwoq said:**
> thanks for the info
there was a version 1.3 did i miss that or not note it as a version update?
was 1.3 the one you added the -s option?
That was added in 1.2 and I'm not sure who all had access to the 1.3 broken version.  Some of my clients did.  Compared to 1.2 the changes were mostly cosmetic.

---

### Post by daysleeper76 on 2012-12-19
Hi to all,
i have installed the last version and now i can see the scanned image, but if i click the mail config button nothing happens, and in the preview pane of the main page all the buttons are disabled.. only if i go in the scanned file page i can use some button like download but the pdf button isn't working.
What can i do to enable all of this?
Thanks in advance.

Carlo S.

---

### Post by jhansonxi on 2012-12-19
> **daysleeper76 said:**
> Hi to all,
i have installed the last version and now i can see the scanned image, but if i click the mail config button nothing happens, and in the preview pane of the main page all the buttons are disabled.. only if i go in the scanned file page i can use some button like download but the pdf button isn't working.
What can i do to enable all of this?
Thanks in advance.

Carlo S.

Could be a permissions problem.  Check the Apache log (somewhere in /var/log) when you attempt to use the buttons.  Could also be a problem with your web browser, possibly scripts being blocked.

---

### Post by pqwoerituytrueiwoq on 2012-12-19
> **daysleeper76 said:**
> Hi to all,
i have installed the last version and now i can see the scanned image, but if i click the mail config button nothing happens, and in the preview pane of the main page all the buttons are disabled.. only if i go in the scanned file page i can use some button like download but the pdf button isn't working.
What can i do to enable all of this?
Thanks in advance.

Carlo S.
did you install the pdf dependency [php-fpdf]("apt:php-fpdf") 
what browser are you using?
if you updated from a old version hold ctrl and hit F5 to do a hard refresh and skip the old cached javascript file

---

### Post by enjoy10 on 2013-06-20
New version of php scanner server running in ubuntu server 12.04  is compatible with ADF support for[COLOR=#666666][FONT=Helvetica] [/FONT][/COLOR][COLOR=#000000][FONT=Helvetica]HP LaserJet 100 colorMFP M175nw[/FONT][/COLOR][COLOR=#666666][FONT=Helvetica] [/FONT][/COLOR]  [https://github.com/claenjoy/PHP-Scanner-Server](https://github.com/claenjoy/PHP-Scanner-Server)

enjoy !

---

### Post by pqwoerituytrueiwoq on 2013-06-22
[Version 1.3-0](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/wiki/Downloads) released, [change log here](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/wiki/Change-Log)

---

