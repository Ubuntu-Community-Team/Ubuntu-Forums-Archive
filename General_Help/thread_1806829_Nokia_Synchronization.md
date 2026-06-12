---
title: "Nokia Synchronization"
date: 2011-07-18
forum: General Help
---

### Post by shashanksingh on 2011-07-18
I have a nokia N78 which sync's with the machine in Windows 7 using Ovi Suite.

Any ubuntu alternative for that?
If yes, a tutorial for the same would be a lot helpful.

---

### Post by coldraven on 2011-07-18
I can tell you how to easily backup and restore your contacts, if you want more you will have to read ```
man gammu
```First install gammu from the Software Centre
Then switch on Bluetooth on your phone and pair it with your computer. It helps if you have given your phone a name so you can easily see it when connected.
Click on the Bluetooth symbol and select "Browse Files".You should then be able to browse folders using Nautilus.
Press Ctr+L to see the path name to your phone, mine looks like this ```
obex://[D8:2A:7E:C2:51:83]/

```Then run ```
gammu --config
```It will create a .gammurc file in your home folder, if you did not know the answers when you ran the config you can easily just edit the file.
Mine looks like this
```
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
```You can see that I pasted in the port number that we got from Nautilus.

Then to backup my contacts I just type this
```
gammu --backup my_contacts.lmb
```To restore use
```
gammu --restore my_contacts.lmb
```This will erase any existing contacts so if you have already made some use --addnew instead.
    
```
gammu --addnew my_contacts.lmb
```You only have to do the setup once, after that it is super-fast!
You can try Wammu which is a GUI for gammu but I have never managed to make it work.

---

### Post by shashanksingh on 2011-07-19
Thank you @coldraven, that would have really helped ifI had bluetooth enabled on my desktop.
I connect my cellphone using a USB cable, so I thought maybe Wammu with a GUI may be easier to try.
But when I ask it to search for connected phones automatically, it does find two devices (which I assume are my phone and memory card), but it goes on to an infinite slumber and I can't continue since it says it hasn't finished.

---

### Post by coldraven on 2011-07-20
My last phone had a USB to Serial cable and it took many attempts to extract all my contacts. That's why I wanted a Bluetooth phone, I will never have to find the cable amongst all my clutter! Buy yourself a Bluetooth dongle!

Good luck!

---

### Post by shashanksingh on 2011-07-21
> **coldraven said:**
> My last phone had a USB to Serial cable and it took many attempts to extract all my contacts. That's why I wanted a Bluetooth phone, I will never have to find the cable amongst all my clutter! Buy yourself a Bluetooth dongle!

Good luck!

I would rather not buy a dongle just for synchronising my phone, which I do maybe once a month or so. Id rather invest that in getting cooler speakers/headphones.. 8)

Anways, I only hope to sync my phone with ubuntu someday, coz this aint working well (Wammu from GUI, will have to try from command line)

---

