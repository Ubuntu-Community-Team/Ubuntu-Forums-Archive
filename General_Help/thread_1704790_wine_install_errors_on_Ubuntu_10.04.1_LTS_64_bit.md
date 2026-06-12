---
title: "wine install errors on Ubuntu 10.04.1 LTS 64 bit"
date: 2011-03-11
forum: General Help
---

### Post by smashingpumpkin on 2011-03-11
Hello,

I'm new to the community.
I mess around on linux & unix for work sometimes,
but I've always used windows for private use.

I've decided to give ubuntu a shot now though :)

I'm running into a problem when I try to install Wine.
(I need MS office)

When I try to install wine using apt-get, it is giving me the following error:
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2
E: Broken packages
I've googled around, and found the following instructions on the WINEHQ website on how to install wine:
> 
**Applications->Ubuntu Software  Center**, then selecting **Edit->Software Sources**. Choose the **Other  Software** tab and click **Add**.
=> add *ppa:ubuntu-wine/ppa *as a repository
Then use their link pointing to apt://wine1.2 to install
This pretty much gives the same error,
when trying this I get a pop up message stating:
> Can not install 'wine1.2' (E:Unable to correct problems, you have held broken packages.) I have tried to correct any broken packages using synaptic.
-> edit -> fix broken packages
This didn't change anything.

I have also tried all of the following:
apt-get  clean 
apt-get  update
apt-get  upgrade
apt-get dist-upgrade

=> all these commands have ran succssfully
=> the apt-get upgrade has also upgraded "winetricks"

However, when I try to install wine, I still get the exact same errors.

I don't know what else I can do... :-(

Did anyone have the same problem on 10.04.1 LTS 64 bit ?

---

### Post by cottfcfan on 2011-03-11
Have you enabled Medibuntu?
Wine gets the msttcorefonts package from there.
[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)
you may also need to run:
```
sudo apt-get -f install
```
to sort out any broken packages.

---

### Post by smashingpumpkin on 2011-03-11
thanks for the reply.

I've installed medibuntu.
I've also run sudo apt-get -f install,
but it doesn't say anything out of the ordinary:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

still unable to install wine with the same errors as before

---

### Post by harkumar on 2011-03-11
open office is a good alternative...it has all the formats of MS OFFICE too...give it a chance!!

---

### Post by howefield on 2011-03-11
> **cottfcfan said:**
> Have you enabled Medibuntu?
Wine gets the msttcorefonts package from there.
[http://medibuntu.org/repository.php](http://medibuntu.org/repository.php)
you may also need to run:
```
sudo apt-get -f install
```
to sort out any broken packages.

Just to mention that Wine doesn't depend on the availability of the Medibuntu repository, Wine pulls in ttf-mscorefonts-installer from the Ubuntu repositories. 

[http://packages.medibuntu.org/lucid/index.html](http://packages.medibuntu.org/lucid/index.html)

---

### Post by smashingpumpkin on 2011-03-11
> **harkumar said:**
> open office is a good alternative...it has all the formats of MS OFFICE too...give it a chance!!

I was expecting this :)

I've got open office.
But I have issues when opening my previous xls documents that were made in excel 2007,
when printing, the page ends differ from how they were in excel,
some things that were supposed to be on one page end up printing on 2 pages,
with one or more columns on the second page.

Anyhow, 
even if I would completely abandon ms office and go open office,
I would still want wine to work to occasionally run a windows app when needed.

---

### Post by smashingpumpkin on 2011-03-11
It seems that I get different errors when I try the following:

first I try apt-get install **wine,**
then I try apt-get install **wine1.2**

$ sudo apt-get install **wine**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2
E: Broken packages




$ sudo apt-get install **wine1.2**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine1.2: Depends: ia32-libs (>= 1.6) but it is not going to be installed
           Depends: lib32asound2 (> 1.0.14) but it is not going to be installed
           Depends: libc6-i386 (>= 2.6-1) but it is not going to be installed
           Depends: lib32nss-mdns (>= 0.10-3) but it is not going to be installed
           Recommends: winbind but it is not going to be installed
E: Broken packages



It seems he's asking for 32 bit libraries,
which I probably don't have since I'm running a 64 bit ubuntu ?

---

### Post by howefield on 2011-03-11
> **smashingpumpkin said:**
> It seems he's asking for 32 bit libraries,
which I probably don't have since I'm running a 64 bit ubuntu ?

You can run 32 bit software in 64 bit Ubuntu using 32 libraries. That's not the issue.

It is asking for versions more current than what you have available it seems. 

What version of Ubuntu are you using ?

Edit, sorry, I see it in the thread title.

---

### Post by smashingpumpkin on 2011-03-14
Is this maybe a known problem in version 10.04.1 LTS 64 bit ?

---

### Post by cottfcfan on 2011-03-14
Not a known problem, I'm running the same version.
I'd try starting again.
remove Wine completely in synaptic or:
```
sudo apt-get remove --purge wine1.2*.*
```
then delete your .wine folder in your home folder, and any traces of wine from your .local/share/applications folder.
Then try wine 1.3. It works fine for me.

---

### Post by smashingpumpkin on 2011-03-15
I ran the command you specified,
but this unfortunately deleted more than just wine and made my ubuntu unusable (so many components were de-installed that it was impossible to use the gnome environment, logon impossible (unless command line logon). :lolflag:

anyway, I've reinstalled ubuntu from scratch (exactly the same version),
and running apt-get install wine worked like a charm :guitar:

not sure what I did to screw it up before,
ah well.

thanks all for your replies

---

### Post by cottfcfan on 2011-03-16
smashingpumpkin,
Glad you got it sorted.
See what you mean about the command, takes out more than just Wine.
Sorry for the misinfo, should have tried it myself 1st.
On the positive side it got you sorted.:D

Command has been changed..

---

### Post by jesuspresley on 2011-05-23
> **cottfcfan said:**
> Not a known problem, I'm running the same version.
I'd try starting again.
remove Wine completely in synaptic or:
```
sudo apt-get remove --purge wine*.*
```
then delete your .wine folder in your home folder, and any traces of wine from your .local/share/applications folder.
Then try wine 1.3. It works fine for me.

If this is kind of a destructive command, can you please delete it from this thread? 

:)

---

