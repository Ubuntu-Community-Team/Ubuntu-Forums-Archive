---
title: "need help with printer driver"
date: 2011-05-02
forum: General Help
---

### Post by mike2507 on 2011-05-02
i need some help to install a driver for my printer

i downloaded a .tar file from " canon" website but have no clue on what to do with it 
[http://software.canon-europe.com/software/0028619.asp](http://software.canon-europe.com/software/0028619.asp)


thanks in advance for helping this linux noob

---

### Post by mike2507 on 2011-05-26
it's been 3 weeks since i posted this problem , time to bump it ;)

---

### Post by demonipuch on 2011-05-26
Hi

Open a terminal and run these commands :
```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-common cnijfilter-mp140series
```This will add a **[ppa]("https://launchpad.net/%7Emichael-gruz/+archive/canon")** to your source list and install your printer driver.

Let me know if it helped

---

### Post by mike2507 on 2011-05-26
> **demonipuch said:**
> This will add a **[ppa]("https://launchpad.net/%7Emichael-gruz/+archive/canon")** to your source list and install your printer driver.

Let me know if it helped

when i click on the link , i read :

>  You can update your system with **_[COLOR=Red]unsupported[/COLOR]_** packages from           this **_[COLOR=Red]untrusted[/COLOR]_** PPA by adding **ppa:michael-gruz/canon**           to your system's Software Sources.i assume this is because it is a non-official package and it's save to use ?

---

### Post by demonipuch on 2011-05-26
yes it is completely safe

edit : If you wish not to use this ppa you can still configure your printer with the driver provided by the canon support. You'll need to untar the archive and install the packages with dpkg. There may be some error (libcupsys2 dependency or wrong architecture package if you're running a 64 bits system) but it can be solve. This ppa is just an easy way to install canon drivers.

---

### Post by mike2507 on 2011-05-26
thanks for the help [demonipuch]("http://ubuntuforums.org/member.php?u=1162387"), everythings works now =D>

all i need now is a new color cartridge, but i suppose you can't help me with that ;)

---

### Post by demonipuch on 2011-05-26
Glad it helped

Have fun printing :)

---

