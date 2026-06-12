---
title: "Sharing printer with Windows 7 &amp; Vista"
date: 2012-08-11
forum: General Help
---

### Post by Old_Grey_Wolf on 2012-08-11
I have cups and samba set up on an old laptop as a printer server. The printer is an Epson Stylus NX215. The laptop is running Xubuntu 12.04. 

My Linux computers can print to it without any problems. 

I can connect to the laptop and add the printer in both Windows 7 and Vista. When I get to the "Print Test Page", it doesn't print. Both versions of Windows think the file was sent to the server; however, when I look in the printer queue on the laptop, there is nothing there.

Any suggestions?

---

### Post by Old_Grey_Wolf on 2012-08-12
bump

---

### Post by GeneralCody on 2012-08-12
You should try to set it up with TCP/IP printing.

Try something like this:

[http://andlinux.org/wiki/index.php5?title=Howto:_setup_Windows_printers](http://andlinux.org/wiki/index.php5?title=Howto:_setup_Windows_printers)

---

### Post by Old_Grey_Wolf on 2012-08-12
That seems to describe printing from Linux to a printer shared by a Windows box. I have bookmarked your link if I find I have no other choice that going that way.

I am trying to print from Windows to a printer shared by a Linux box.



____________
Off topic. I found your avatar to be intersting considering a 1 ton rover was landed on Mars in the last few days. It may be decades before what is depicted in your avatar could actually happen.

---

### Post by Old_Grey_Wolf on 2012-08-14
bump

---

### Post by Old_Grey_Wolf on 2012-08-19
I have the printer shared from a Windows box at the moment.

That is not my preferred solution. I would prefer to share it from a Linux box. 

This is my last bump to this thread.

---

### Post by davidvandoren on 2012-08-20
Set-up your printer on your linux box. Make sure it is working.
If you want to use a local network you'll need to either share the windows internet connection or you'll have to have two Ethernet cards. 

Open System Administration and then Printing 

Select your printer and click on Server then open Settings

check mark; Show printers shared by other systems
                      Publish shared printers connected to this system
                     Allow printing from the internet.

click ok
right click on your printer make sure it says shared and enabled.
set it as default.

 If yo don't want to share the windows internet and only have one Ethernet Card, You'll have to edit hosts.allow

 
Open terminal and change into the etc directory

type ```
sudo gedit hosts.allow
```enter this ```
all: ip_address_of_windows_machine
```click save and close window.
I guess it's not really safe though!

Then either open Firewall configuration if installed and open port 631 in and out. I am not sure which ones are need though maybe open both TCP and UDP.

For my pc, I've set a two launchers on my Desktop and entered the following.

```
gnome-terminal -x bash -c "sudo ufw allow 631"
``` to open the printer for the network and 

```
gnome-terminal -x bash -c "sudo ufw deny 631"
```for closing it after printing is finish. 

Now you'll need to go to your vista or windows machine and open the firewall ports as well 631. You can find instructions on youtube for that. 

Finally you'll need to have a static IP if you want to print over the internet. 
If you don't have one maybe DYNDNS or something like that could work. 

Otherwise open your printer set-up routine on the windows machine and 

  select Connect to a printer on the internet 
enter the printer URL
```
http://my-internet-ip:631/printers/printername
```local network
```
http://linux-box-ip:631/printers/printername
```

You'll need to check on your linux box for the correct printer name
```
http://localhost:631/printers/
```


You'll be prompted to select a driver 
select a Manufacturer of "Generic" and the Printer "MS Publisher Imagesetter"

driver will install and work.

---

### Post by Old_Grey_Wolf on 2012-08-20
Thanks for the help. I will look at it again next weekend. I probably have port 631 blocked somewhere on my home network.

---

