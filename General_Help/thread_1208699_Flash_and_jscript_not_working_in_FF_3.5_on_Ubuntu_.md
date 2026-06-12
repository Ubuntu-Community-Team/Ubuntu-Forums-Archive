---
title: "Flash and jscript not working in FF 3.5 on Ubuntu 9.04"
date: 2009-07-09
forum: General Help
---

### Post by PlatosGimp on 2009-07-09
I have completely uninstalled ff 3.0x, uninstalled and re-installed ff 3.5 and uninstalled and reinstalled adobe flash with "sudo apt-get install flashplugin-installer", but flash is still not working in 3.5 under Ubuntu 9.04. When I go to a site with flash, no image and just links to download the flash plugin?

Any suggestions?


Extensions:

scribefire
forecastfox
twitterbar
user agent switchin
vmware remote console plugin
xmarks
ubuntu firefox modifications (but shows as disabled)

---

### Post by nacho32 on 2009-07-09
under firefox under tool  then addons is flash listed their? flash 10.0.r22
great page to install flash [http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

---

### Post by PlatosGimp on 2009-07-09
No its not listed under "Tools" "Addons" and when I tried to follow the steps from the url you provided, if I go to "about:plugins" I do see flash there, 

Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

###So I tried to remove with the following:

jstork@johnny-lt:~$ sudo apt-get remove flashplugin-nonfree
[sudo] password for jstork: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.2 linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic dkms
  python-indicate
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


###And then I tried with this:

jstork@johnny-lt:~$ sudo apt-get remove flashplugin-installerReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xulrunner-1.9.2 linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic dkms
  python-indicate
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  flashplugin-installer
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 180kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 184584 files and directories currently installed.)
Removing flashplugin-installer ...

###But it still shows up under about:plugins


Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

Any suggestions?


jscript also does not work any more

---

### Post by lovinglinux on 2009-07-09
For your flash problem....

See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [url=http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT
004]**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**[/url].

BTW, you shouldn't remove Firefox 3.0. This could break things like the searchplugins. Additionally, some packages depend on it, for example gecko-mediaplayer plugin.

I don't know how you installed Firefox 3.5 but I suggest reading the "Install Other Versions" of the tutorial above. It explains the 4 most common methods of installation and the differences between them.

---

