---
title: "Tring to get drivers for Commercial  DVD's to play"
date: 2010-11-04
forum: General Help
---

### Post by 340six on 2010-11-04
I have another thread from when I did the wifes lap top. I put a driver in for:
Hers plays them in applications,sound&music,movie player I tried the same driver and it did not install.
Did it 2 times no dice.
now trying adding the repository
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)
but it stops with
[b]reading package list
Kevin@kevin-desktop:~ [/b]
help:popcorn:
it went smooth 2 days ago when I did hers

---

### Post by dcstar on 2010-11-04
> **340six said:**
> I have another thread from when I did the wifes lap top. I put a driver in for:
Hers plays them in applications,sound&music,movie player I tried the same driver and it did not install.
Did it 2 times no dice.
now trying adding the repository
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)
but it stops with
[b]reading package list
Kevin@kevin-desktop:~ [/b]
help:popcorn:
it went smooth 2 days ago when I did hers

The repository may be down, just be patient.

---

### Post by 340six on 2010-11-04
Ok thought I did something wrong and down loaded it and did not install the down load.
I pasted in this in the "gnome-terminal"
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

[B]What is best to do now? wait few hours or friday and try again? Edit I just saw this....
[/B]Medibuntu's repository is deactivated by [upgrading to a newer Ubuntu release]("https://help.ubuntu.com/community/UpgradeNotes"), so you should run this command again after the release upgrade. 
What to try now?

---

### Post by Yezinki on 2010-11-04
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update


sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list

---

### Post by 340six on 2010-11-04
I was going to just try and install just the drivers I need and get the "libdvdcss2"
But they show 
i386, amd64 and powerpc
I downloaded something The DVD shows in Places I see the down load but does noty look installed?

Says: Could not open location 'computer:///CD%5CDVD%20Drive.drive' No application is registered as handling this file :confused: so trying something else and will toss the other in the trash
Thanks for any and all help in advance

---

### Post by Yezinki on 2010-11-04
np.........post the link.........I'll  get ya.

---

### Post by 340six on 2010-11-04
> **Yezinki said:**
> np.........post the link.........I'll  get ya.
i368
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

powerpc
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_powerpc.deb

amd64
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
**I have no idea what one to use**

---

### Post by 340six on 2010-11-04
this is the web page
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository)

---

### Post by Schrute Farms on 2010-11-04
> **340six said:**
> i368
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

powerpc
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_powerpc.deb

amd64
wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb
**I have no idea what one to use**

Which version of Ubuntu are you using?
32 bit use i386
64 bit use AMD64
If you are on an old PowerPC Apple mac then use Power pc

---

### Post by mc4man on 2010-11-04
> but it stops with
reading package list
Kevin@kevin-desktop:~ 

There's a good chance you already actually added medibuntu fine and a simple 
sudo apt-get install libdvdcss2
would take care of

This is the simplest method (copy and paste as one command
```
sudo apt-get install libdvdread4 && \
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Yezinki on 2010-11-05
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

sudo apt-get --yes install app-install-data-medibuntu apport-hooks-medibuntu

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu2_powerpc.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu2_powerpc.deb

---

### Post by 340six on 2010-11-05
> **schrute farms said:**
> which version of ubuntu are you using?**
32 bit use i386
64 bit use amd64
if you are on an old powerpc apple mac then use power pc
10.04

---

### Post by 3rdalbum on 2010-11-05
Wait a second. You say you've added the Medibuntu repository to your system already. You don't need to manually download a .deb file from the website and open it, you can just install it through Synaptic Package Manager or through the 'apt-get' command.

```
sudo apt-get install libdvdcss2
```

or install the "libdvdcss2" package from Synaptic Package Manager/Software Center.

---

