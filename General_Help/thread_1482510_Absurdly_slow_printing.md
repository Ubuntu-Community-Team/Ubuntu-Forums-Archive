---
title: "Absurdly slow printing"
date: 2010-05-13
forum: General Help
---

### Post by Kalidor on 2010-05-13
I have ubuntu 10.04 and an usb laserjet 1320 (hp). As soon as I order to print a document the printer led starts flashing which means it starts receiving data immediately... but the data flow must be very slow because it takes 5 minutes for the printer to start printing one page after that, and 5 more minutes for the following page and so on... hplip is correctly installed i believe. 
Pls help me I really need the printer.

---

### Post by mike555 on 2010-05-13
You might change the usb plugs (I found out my computers front usb plugs are usb1.1 , but the back ones are usb2 ) or if your using an extension usb cable make sure it's usb2.

---

### Post by Rasa1111 on 2010-05-13
Same thing here Kalidor,
I dont print much though.

good info mike, good to know
i will try that..
I dont believe i have tried my printer plugged into the back yet. 
thanks

---

### Post by Kalidor on 2010-05-13
hmmm no windows prints just fine.

---

### Post by Kalidor on 2010-05-13
up

---

### Post by Rasa1111 on 2010-05-13
> **mike555 said:**
> You might change the usb plugs (I found out my computers front usb plugs are usb1.1 , but the back ones are usb2 ) or if your using an extension usb cable make sure it's usb2.


well, mike~
interestingly, [and surprisingly]~
that did indeed make my printer print at the normal speed. 
simply moving the USB plug to the back... 
niiice! thanks!

---

### Post by Kalidor on 2010-05-13
Yeah but it did absolutely nothing for me, instead.

---

### Post by Rasa1111 on 2010-05-13
darn,
sorry bro,
guess we cant win'em all right. lol

i do feel kinda bad that i got a fix from your thread and you didnt...
however.. Im sure someone wiser will be along to help.. soon enough. :KS

---

### Post by Kalidor on 2010-05-13
lol

---

### Post by Kalidor on 2010-05-13
up

---

### Post by Kalidor on 2010-05-14
up

---

### Post by killabee44 on 2010-06-01
Guys,

I am also having this exact same issue with Lucid and a Brother 2170w. The printer lights up but stays flashing. The printer status shows the que moving extremely slow. 

I read somewhere that it might be a permissions issue. Im not sure how to diagnose it though. Wish there was a utility I could run. 

Here is:  -l /usr/lib/cups/backend/lpd

```
-rwxr--r-- 2 root root 44056 2010-05-14 11:55 /usr/lib/cups/backend/lpd
robert@robert-desktop:~$ sudo service cups restart

```

Edit: Here are two errors I found in my cups error log at var/log/cups/error_log:

```
E [01/Jun/2010:14:21:47 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [01/Jun/2010:14:51:16 -0400] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
```

Thanks.

---

### Post by killabee44 on 2010-06-01
The problem with this might be a bad driver (based on the CUPS log).

I didn't have this problem with jaunty but that was 32bit. I just installed the 64 bit version of Lucid on this machine and started having this problem. 

It looks like Brother does not have a proper 64bit driver for the HL-2170w. I went to their site and got the linux driver they have available for this printer and when I double click the .deb file get an error refusing to install because it was "i386". 

I hope there is another driver available that will work or it's a different problem. 

If anyone has any input, it would be welcome. Thanks.

Edit. Im gonna start my own thread. Should have done so instead of threadjacking! :)

Edit: 

Ok, I finally have a fix thanks to johnny_vc...

It is really a workaround but it works so who cares.

> I think this a bigger issue than just with that printer, I found a workaround solution which is to reinstall the printer using :

Device URL : socket://IP_of_the_printer:9100

Make and Model : Generic PCL 5e Printer Foomatic/gutenprint-ijs-simplified.5.0

I did it through the CUPS web interface on Lucid 10.04 so it was slightly different.

1. Log on to the cups web interface: [http://localhost:631/admin]("http://localhost:631/admin") (for username and pw I used the sudo for this pc).

2. Select "**Add Printer**"
3. From "Other Network Printers:" I selected:** LPD/LPR Host or Printer **
4. under "Connection" put in: **socket://IP_of_the_printer:9100** (of course, substitute in the IP of your printer)
5. Name, description, location: fill those out as you wish without spaces
6. Sharing: I did not check this box.
7. Make: Select **Generic** and click Continue
8. Model: [B]Generic PCL 5e Printer Foomatic/hpijs-pcl5e (recommended)
[/B] (this model is the closest by name to what Johnny_vc told me to use. I figured mine is different because I'm using Lucid) 
9. Click "Add Printer" and you're done.

I hope this helps someone else. Good luck.

---

### Post by klausner on 2010-06-04
> **killabee44 said:**
> The problem with this might be a bad driver (based on the CUPS log).

I didn't have this problem with jaunty but that was 32bit. I just installed the 64 bit version of Lucid on this machine and started having this problem. 

It looks like Brother does not have a proper 64bit driver for the HL-2170w. I went to their site and got the linux driver they have available for this printer and when I double click the .deb file get an error refusing to install because it was "i386". 

I hope there is another driver available that will work or it's a different problem. 

......

Ok, I finally have a fix thanks to johnny_vc...

It is really a workaround but it works so who cares.



I did it through the CUPS web interface on Lucid 10.04 so it was slightly different.

1. Log on to the cups web interface: [http://localhost:631/admin]("http://localhost:631/admin") (for username and pw I used the sudo for this pc).

2. Select "**Add Printer**"
3. From "Other Network Printers:" I selected:** LPD/LPR Host or Printer **
4. under "Connection" put in: **socket://IP_of_the_printer:9100** (of course, substitute in the IP of your printer)
5. Name, description, location: fill those out as you wish without spaces
6. Sharing: I did not check this box.
7. Make: Select **Generic** and click Continue
8. Model: [B]Generic PCL 5e Printer Foomatic/hpijs-pcl5e (recommended)
[/B] (this model is the closest by name to what Johnny_vc told me to use. I figured mine is different because I'm using Lucid) 
9. Click "Add Printer" and you're done.

I hope this helps someone else. Good luck.

WOW! Mark this thread SOLVED!.

Installed the PCL 5e Foomatic driver per the above instructions, and saw the printer start to respond almost instantly, instead of hanging forever.

Note: You can't pick drivers when using the System->Administration->Printing menu. You must log into cups as described above. 

Thanks.
=D>

---

### Post by killabee44 on 2010-06-04
Yeah, should be marked as solved. Im not the OP though. Moderator around?

---

### Post by Bunyak on 2010-08-31
Absurdly fast wonderful and sexy printing!\\:D/

Thanks a bunch.  Worked like a charm!

---

### Post by taz35 on 2010-10-01
This generic driver worked great for my HP Officejet 6300 series:
Generic PCL 6/PCL XL Printer Foomatic/hpijs-pcl5e

---

### Post by rscottdrysdale on 2010-11-05
i, too, am experiencing extremely slow printing with 10.04 LTS (P4HT@3GHz, 2G RAM).  i have an HP CP2025 color laserjet on ethernet.

i tried the "delete existing printer, log into CUPS via http, add printer, select generic, pcl5e..." thing outlined above, and it's still slow as hell (several minutes per page).

and the output looks bad compared to the same page printed from windows.  i'm printing directions from google maps with firefox, with the map plus directions.  the map is readable, but looks a bit crude compared to the same page printed from windows.

i don't print from ubuntu very often (the machine is mostly a RAID5 server), but it's in the kitchen so it can be handy when guests are over.  my first ubuntu install was 9.04, and the machine has been updating itself since then.  i don't remember having the problem with the older ubuntu.

any other suggestions?

---

