---
title: "Antivirus/firewall ?"
date: 2010-11-28
forum: General Help
---

### Post by gmenfan83 on 2010-11-28
Hi i am happy to say i am new to Ubuntu as i have just tried it out today and love it ......my quwstion is im coming from windows where everything needs to be locked down and have looked but see mixed reviews on the antivirus subject for Ubuntu....if i need any what would be my best option for a free antivirus or is it uneeded?

---

### Post by Frogs Hair on 2010-11-28
If you worried about sending infected files to a Windows user , there is virus scanner and Klam AV in the repository . Avast also has a Linux version. Welcome to the forums !

---

### Post by wojox on 2010-11-28
[Antivirus]("https://help.ubuntu.com/community/Antivirus")

---

### Post by kgarbutt on 2010-11-28
Hi, if you are running the Gnome desktop, you can run gufw and clamtk. To check them out, type from the terminal:

apt-cache show gufw
apt-cache show clamtk

to install them, type in the terminal:
sudo apt-get install gufw clamtk

Descriptions:
gufw = graphical user interface for ufw (firewall)
clamtk = graphical front-end for ClamAV (virus protection)

---

### Post by jmszr on 2010-11-28
gmenfan83,

Welcome aboard!

You should find this of interest: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) .

---

### Post by karthick87 on 2010-11-28
You can also install clamav,it is a cross platform antivirus software.
```
sudo apt-get install clamav
```

---

### Post by gmenfan83 on 2010-11-28
hi thank you all for your help as i am new to this ..i installed some suggested add ons as well as clam av through script but how do i check clam av or does it just do its own thing in the backround ?again thank you all for your help and patience

---

### Post by Sef on 2010-11-28
> /firewall ?

A firewall is installed by default: iptables, but if you want to change it, you have to do so by the command line. If you want a GUI to change it, then follow these directions:

Applications > Ubuntu Software Center > Search: ufw > click on the install button

---

### Post by karthick87 on 2010-11-28
> **gmenfan83 said:**
> hi thank you all for your help as i am new to this ..i installed some suggested add ons as well as clam av through script but how do i check clam av or does it just do its own thing in the backround ?again thank you all for your help and patience

You have to run manually i guess,

```
sudo clamscan -r /home
```

To update virus definitions:

```
sudo freshclam
```

---

### Post by gmenfan83 on 2010-11-28
> **karthick87 said:**
> You have to run manually i guess,

```
sudo clamscan -r /home
```To update virus definitions:

```
sudo freshclam
```

thank you

---

### Post by gmenfan83 on 2010-11-28
now lets just say a virus was found how would you go about deleting it?the listed anti virus programs that have been listed say the only detect not delete

---

### Post by WorMzy on 2010-11-28
clamscan has a remove option, but since false positives are possible, it shouldn't really be used. It also has a move option, which allows you to move the infected files somewhere (preferably into your ext4 partition, since Windows cannot access that, and therefore cannot execute it)

```
sudo clamscan -r --move=/home/username/ /
```

---

### Post by gmenfan83 on 2010-11-28
> **WorMzy said:**
> clamscan has a remove option, but since false positives are possible, it shouldn't really be used. It also has a move option, which allows you to move the infected files somewhere (preferably into your ext4 partition, since Windows cannot access that, and therefore cannot execute it)

```
sudo clamscan -r --move=/home/username/ /
```
ran it and it says it doesnt exist or its not in library?

---

### Post by WorMzy on 2010-11-28
That was just an example. Replace "username" with your username if you want to use it.

---

### Post by the_phenom on 2010-11-28
> **WorMzy said:**
> clamscan has a remove option, but since false positives are possible, it shouldn't really be used. It also has a move option, which allows you to move the infected files somewhere (preferably into your ext4 partition, since Windows cannot access that, and therefore cannot execute it)

```
sudo clamscan -r --move=/home/username/ /
```

You'll want to be careful with that command.  In Linux, mailboxes are typically a single file.  So, if ClamAV detects a virus in your (e.g.) Thunderbird inbox, the whole inbox will get yanked (in this case, moved).  I learned this the hard way...

---

### Post by karthick87 on 2010-11-28
There is a possibility that CLAMAV anitivirus will produce false positive results.So be sure before you delete a file.

---

