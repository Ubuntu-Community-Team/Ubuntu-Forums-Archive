---
title: "How to restore contacts to a Nokia C1-01"
date: 2011-04-23
forum: General Help
---

### Post by coldraven on 2011-04-23
I needed to get my contacts from my old Nokia 5140 to my new Nokia C1-01.
Using a CA-42 (USB to serial) cable I created a backup file (.lmb) using ```
gammu --backup my_contacts.lmb
```The .gammurc file looked like this
#######################
[gammu]

port = /dev/ttyUSB0
model = 5140
connection = fbusdlr3
synchronizetime = yes
logfile = 
logformat = nothing
use_locking = 
gammuloc = 


Then I paired the C1-01 with Bluetooth and got the port with
```
hcitool scan
```or you can use Nautilus and do a Ctrl+L to see the port.
Then the channel number using
```
sdptool search DUN
```Then edit .gammurc to look like this
#######################
[gammu]

port = D8:2A:7E:C2:51:83
model = NAUTO
connection = bluephonet
channel = 1
synchronizetime = yes
logfile = 
logformat = nothing
use_locking = 
gammuloc = 


Then restore your contacts
```
gammu --restore my_contacts.lmb
```This will erase any existing contacts so if you have already made some use --addnew instead.
```
gammu --addnew my_contacts.lmb
```

---

