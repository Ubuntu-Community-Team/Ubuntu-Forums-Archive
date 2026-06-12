---
title: "Anyone knows how to backup call information from Wammu?"
date: 2011-05-30
forum: General Help
---

### Post by wijit on 2011-05-30
I use Wammu to connect to my Nokia via bluetooth. I can retrieve all contacts, calls and SMSes from the mobile. I also can backup the retrieved contacts and SMSes via the "Backups" menu. I also want to backup calls but Wammu provides no menu for the purpose. Right clicking on the call list shows backup menu but only Wammu header info is filed. If anyone knows how to do this please help.

---

### Post by coldraven on 2011-05-30
I don't know about Wammu, it just was too buggy for me.
I just use gammu in a terminal, Wammu is just a GUI for gammu. You would need to create a .gammurc file in your home folder with the connection type. Mine looks like this
```
[gammu]

port = D8:2A:7E:C2:51:83
model = NAUTO
connection = bluephonet
synchronizetime = no
logfile = /home/[COLOR=Navy]yourusername[/COLOR]/.gammulog
logformat = textalldate
use_locking = no
gammuloc = 
```You can find the port easily, when your phone is connected by bluetooth and visible to Nautilus just do Ctrl+L to see the path to your phone.
Or use these commands
sdptool search DUN #searches for the channel number
hcitool scan       #find bluetooth device


Then the command should get your call list (DC=dialed calls)(1 to 20, depends on how many calls your phone keeps) See man gammu
```
gammu --getmemory DC 1 20 -nonempty
```

---

### Post by coldraven on 2011-05-30
To save the output to a text file do this
```
gammu getmemory DC 1 20 -nonempty >my-call-list.txt
```

---

