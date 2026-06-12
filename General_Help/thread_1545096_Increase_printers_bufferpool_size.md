---
title: "Increase printers buffer/pool size"
date: 2010-08-03
forum: General Help
---

### Post by daniel-strae on 2010-08-03
First of all, sorry for my bad english ;)

Hi guys, i need to print some prn files (that can ben 2 from 50Mb size) on 4 epson p50 usb printers in the same time.

My first problem was that ubuntu used to see the 4 printers as one, using the one that i switch on for first and ignoring the other 3.

So i added 'blacklist usblp' to the '/etc/modprobe.d/blacklist.conf', disinstalled and reinstalled the printers and now they work 'stand alone'.

My problem now is that if i try to print more than 1 copy to a printer, or 1 copy on all the printers, i get this error in cups:

"unable to write 8192 byte on the printer!"

and the print jobs disappear.

But if i print 1 copy on 1 printer it works..

I've tryed those command:

```

lp -d SX-UP -n 10 ~/Scrivania/test.prn

```

Where SX-UP is my printer name and test.prn is the file (actually, 31Mb).

I tryed even:
```

lpr -# 10 -P SX-UP ~/Scrivania/test.prn

```

and
```

cat ~/Scrivania/test.prn | lpr -# 10 -P SX-UP

```

But the same problem happen

To send the prn to all the printers, i do 
```

lp -d SX-UP -n 10 ~/Scrivania/test.prn & lp -d SX-DW -n 10 ~/Scrivania/test.prn & lp -d DX-UP -n 10 ~/Scrivania/test.prn & lp -d DX-DW -n 10 ~/Scrivania/test.prn &

```

becose the cups classes doesnt work (i get a "device not connected" or something like error).



Anyone has some idea about that?
The prn files that i need to print cant be edited, and need to be printed in the same time on all the printers, about 100 copy for each printer (of course in can give 25 or 100 copy instead of 100, its not a problem)

How can i solve that?
It seems to me that is the printer buffer/spoiler/pool problem, but i dont know how ubuntu handle it and how to increase/manage it.

---

### Post by daniel-strae on 2010-08-04
anyone?

---

