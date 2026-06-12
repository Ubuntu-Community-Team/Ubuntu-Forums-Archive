---
title: "Citrix ICA Files in Ubuntu"
date: 2012-08-01
forum: General Help
---

### Post by sonand on 2012-08-01
Hi!

I have a customer that runs Linux Redhat 5.5 Enterprise edition with ICAClient-11.100-1.
We have installed a standalone XenApp 6.5 server for publishing applications to the linux machine.

We need to use ICA files for launching the applications.

My problem is that i'm not able to get the ICA file assosicated with the Citrix plugin on the linux machine..
- When I start the ICA file it just shows the content of the ICA file..

When launching through web interface address using Firefox I can start the applications..

So I need some information on how to associate ICA files correctly with citrix client, and general info about howto use ica files in Linux environments..

I have set up a lab environment with Ubuntu Linux with the newest Citrix receiver for Linux.

This is the ICA file i'm testing with (this one works in Windows environments)

Encoding
InputEncoding=ISO8859_1

WFClient
Version=2
HttpBrowserAddress=servername:8080
Username=user1
Domain=domainname
ClearPassword=pw

ApplicationServers
servername=

name
Address=servername
InitialProgram=#nameofprogram
ClientAudio=On
AudioBandwidthLimit=2
TWIMode=On
DesiredColor=16
UseLocalUserAndPassword=On
DesiredHRes=1900
DesiredVRes=1200
Compress=On
TransportDriver=TCP/IP
WinStationDriver=ICA 3.0
BrowserProtocol=HTTPonTCP

Compress
DriverName= PDCOMP.DLL
DriverNameWin16= PDCOMPW.DLL
DriverNameWin32= PDCOMPN.DLL

- Do I need something extra in the ICA file when using it in Linux environments , or do some other Linux tweaks ? :)

Any help in this case is highly appreciated !

---

### Post by albandy on 2012-08-01
For a single user:
right click on the ica file.
then go to "Open With", click "Add" and choose the binary location of citrix ica client.

For all users:
open the file 
 /usr/share/applications/defaults.list 
and associate ica extension to ica binary

Edited:
Create a file called citrix.desktop in /usr/share/applications with this contents:

[Desktop Entry]
Exec=/opt/Citrix/ICAClient/wfica.sh %U
Version=1.0
Name=ICA
GenericName=ICA
X-GNOME-FullName=ICA
Comment=ICA
Icon=
StartupNotify=true
Terminal=false
Type=Application

---

### Post by sonand on 2012-08-01
FANTASTIC :)
Now it Works!

What a quick response !
 
THANKS !!!!
 
One more thing: Any special Things I need to think of when writing ICA files that will be started in Linux Environments ?

---

