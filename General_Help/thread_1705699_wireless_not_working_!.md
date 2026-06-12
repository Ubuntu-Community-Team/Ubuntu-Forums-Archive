---
title: "wireless not working !"
date: 2011-03-12
forum: General Help
---

### Post by adamkhawla on 2011-03-12
my wireless not working on  laptop ( my laptop is HP G60-533cl  and ubuntu 10.10) !!! please help me

---

### Post by Hippytaff on 2011-03-12
can you run this script and post the 'wireless-results.txt' file by copy and pasting - and if you could highlight and click the # icon to make it easier to read :-)

---

### Post by Hippytaff on 2011-03-13
If you don't want to run the script, can you post the output of these commands. Open a terminal CTRL+ALT+T and do
```
lspci | grep -i wirel
```
```
lsusb | grep -i wirel
```
```
lshw - C Network
```
```
iwconfig
```
```
ifconfig
```
The script basically does all that for you and puts it into a text file, but I understand people being wary about running scripts people post in forums :-)

---

