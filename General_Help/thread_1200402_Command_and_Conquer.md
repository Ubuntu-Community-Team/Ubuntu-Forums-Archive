---
title: "Command and Conquer"
date: 2009-06-30
forum: General Help
---

### Post by accodata on 2009-06-30
Hi

I am trying to install Command and Conquer that runs on win95 and win98, I have installed wine, to try to install the games, but when I go to the install.exe I get an error say that I have Windows 5.1, I have no idea how to install command and conquer I have the orginal discs, anyone with any help would be appreciated!!!

I understand that I need an earlier WINE, but no idea how to do that with loosing all my information on this pc.

thanks


Accodata

---

### Post by synapsys on 2009-06-30
Try opening up a terminal and typing:

```
winecfg
```a window will pop up. There is a drop box at the bottom of the window where you can choose your windows version. Try that.

If you really need an older version of wine, you can get that here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by accodata on 2009-06-30
I did that, this is what I got


tracey@tracey-desktop:~$ winecfg
The program 'winecfg' is currently not installed.  You can install it by typing:
sudo apt-get install wine
bash: winecfg: command not found

Never got a pop up box, what have I done wrong?

thanks

Accodata

---

### Post by synapsys on 2009-06-30
> **accodata said:**
> 
The program 'winecfg' is currently not installed.  You can install it by typing:
sudo apt-get install wine

It seems you don't have wine installed.
Or it is corrupt.

```
sudo apt-get purge wine
sudo apt-get install wine
```

---

### Post by accodata on 2009-06-30
tracey@tracey-desktop:~$ sudo apt-get purge wine
[sudo] password for tracey: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  kdelibs4c2a kdelibs-data latex-xft-fonts liblualib50 koffice-data ruby1.8
  ruby libavahi-qt3-1 winbind liblua50 libruby1.8 koffice-libs
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tracey@tracey-desktop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdelibs4c2a kdelibs-data latex-xft-fonts liblualib50 koffice-data ruby1.8
  ruby libavahi-qt3-1 winbind liblua50 libruby1.8 koffice-libs
The following packages will be REMOVED:
  kdelibs-data kdelibs4c2a koffice-data koffice-libs latex-xft-fonts
  libavahi-qt3-1 liblua50 liblualib50 libruby1.8 ruby ruby1.8 winbind
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
After this operation, 85.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 157950 files and directories currently installed.)
Removing koffice-libs ...
Removing kdelibs4c2a ...
Removing kdelibs-data ...
Removing koffice-data ...
Removing latex-xft-fonts ...
Updating fontconfig cache for /usr/share/fonts/truetype/latex-xft-fonts
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
Removing libavahi-qt3-1 ...
Removing liblualib50 ...
Removing liblua50 ...
Removing ruby ...
Removing ruby1.8 ...
Removing libruby1.8 ...
Removing winbind ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
tracey@tracey-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  winbind wine-gecko
The following NEW packages will be installed:
  winbind wine wine-gecko
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/16.7MB of archives.
After this operation, 72.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package wine.
(Reading database ... 152282 files and directories currently installed.)
Unpacking wine (from .../wine_1.0.1-0ubuntu6_i386.deb) ...
Selecting previously deselected package wine-gecko.
Unpacking wine-gecko (from .../wine-gecko_0.1.0-0ubuntu1_all.deb) ...
Selecting previously deselected package winbind.
Unpacking winbind (from .../winbind_2%3a3.3.2-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up wine (1.0.1-0ubuntu6) ...
 * Setting kernel variables (/etc/sysctl.conf)...                        [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-console-messages.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/10-network-security.conf)...  [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/30-tracker.conf)...           [ OK ] 
 * Setting kernel variables (/etc/sysctl.d/30-wine.conf)...              [ OK ] 

Setting up wine-gecko (0.1.0-0ubuntu1) ...
Setting up winbind (2:3.3.2-1ubuntu3) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
tracey@tracey-desktop:~$ 

Accodata

---

### Post by synapsys on 2009-06-30
Now use

```
winecfg
```

and choose 95 or 98 then install C&C

---

### Post by accodata on 2009-06-30
Your are bloody awesome 

thank you

Accodata!!!!!!!!!!!!!!

---

