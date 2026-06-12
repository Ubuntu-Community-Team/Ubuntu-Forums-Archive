---
title: "Printer / lpr"
date: 2006-02-08
forum: General Help
---

### Post by SwollenGoat on 2006-02-08
I have installed my printer using the System->Administration->Printing gui, and it prints a test page just fine.  I can also print if i open up a gui program and select the "print" option from, e.g., the file menu of an open office program.

However, if I navigate to a directory using bash and then try lpr on a document in the directory, nothing occurs.  I prefer to use lpr to print, so I'd like to get this working.

Does anyone have any ideas for how to fix this?  Any help would be greatly appreciated.

---

### Post by lamego on 2006-02-08
Does "lpstat -v" shows your printer  listed ?

---

### Post by SwollenGoat on 2006-02-08
No, all I get from lpstat -v is  ```
system for lp: localhost
system for all: localhost

```

I also tried lpq and I get  ```
Printer: lp@R2-D2 'HP PSC 2210' (dest hp2210@/usb/PSC_2200_Series?serial=MY28HD82130G")
 Queue: 1 printable job
 Server: pid 10133 active
 Unspooler: pid 10138 active
 Status: sleeping 60 secs before retry, starting sleep at 18:44:37.841
 Rank   Owner/ID               Pr/Class Job Files                 Size Time
1      john@R2-D2+452               A   452 shttpd.py             1441 08:52:11
Printer 'hp2210@/usb/PSC_2200_Series?serial=MY28HD82130G"' - cannot open connection - getconnection: cannot get address for '/usb/PSC_2200_Series?serial=MY28HD82130G"'

```

I'm guessing it has something to do with the USB connection, but I don't know what.  Any ideas??

Thanks in advance.

---

### Post by SwollenGoat on 2006-02-09
anyone?

---

