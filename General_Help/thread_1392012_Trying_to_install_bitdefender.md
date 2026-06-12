---
title: "Trying to install bitdefender"
date: 2010-01-27
forum: General Help
---

### Post by nikef on 2010-01-27
Hi all 
can someone  point me in the right direction for the download of bitdefender i am running ubuntu 9.10 

There is so many to choose from i just don't know thanks for any help :p

---

### Post by nikef on 2010-01-27
I already have the key , thanks

---

### Post by hhlp on 2010-01-27
Installation

Add the repository by going to System -> Administration -> Software Sources and click on the 'Third Party Software' tab. Now click on 'Add' and copy+paste the following line:

deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free

Click on 'Close' and press 'Reload' when prompted. Ignore the 'No repository key' error (if displayed). To add the repository key open a Terminal (Applications -> Accessories -> Terminal) and copy+paste the following lines::

wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc)
sudo apt-key add bd.key.asc

Now update the sources list:

sudo apt-get update

To install the graphical interface and command line program copy+paste the following line:

sudo apt-get install bitdefender-scanner-gui

Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications -> System Tools -> BitDefender Scanner).

Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button.

---

### Post by t4thfavor on 2010-01-27
Head over to there site, it's on there download site.


[http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/)

---

### Post by nikef on 2010-01-27
> **hhlp said:**
> Installation

Add the repository by going to System -> Administration -> Software Sources and click on the 'Third Party Software' tab. Now click on 'Add' and copy+paste the following line:

deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free

Click on 'Close' and press 'Reload' when prompted. Ignore the 'No repository key' error (if displayed). To add the repository key open a Terminal (Applications -> Accessories -> Terminal) and copy+paste the following lines::

wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc)
sudo apt-key add bd.key.asc


Now update the sources list:

sudo apt-get update

To install the graphical interface and command line program copy+paste the following line:

sudo apt-get install bitdefender-scanner-gui

Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications -> System Tools -> BitDefender Scanner).

Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button.

Thanks i have done it all except the bit where i have to install the scanner -gui  it says it  can not find it .

---

### Post by nikef on 2010-01-27
> **t4thfavor said:**
> Head over to there site, it's on there download site.


[http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/EN_FR_BR_RO/Linux/)


Thanks yes i have been there and tried to install most of them , but ubuntu will not except them

---

### Post by t4thfavor on 2010-01-27
I used the one on the site many times, never had a problem with what you described above.

---

### Post by nikef on 2010-01-27
I have tried them all and none of them will install :sad:

---

### Post by nikef on 2010-01-27
> **hhlp said:**
> Installation

Add the repository by going to System -> Administration -> Software Sources and click on the 'Third Party Software' tab. Now click on 'Add' and copy+paste the following line:

deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free

Click on 'Close' and press 'Reload' when prompted. Ignore the 'No repository key' error (if displayed). To add the repository key open a Terminal (Applications -> Accessories -> Terminal) and copy+paste the following lines::

wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc)
sudo apt-key add bd.key.asc

Now update the sources list:

sudo apt-get update

To install the graphical interface and command line program copy+paste the following line:

sudo apt-get install bitdefender-scanner-gui

Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications -> System Tools -> BitDefender Scanner).

Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button.

Thanks i have managed to install it :)

---

