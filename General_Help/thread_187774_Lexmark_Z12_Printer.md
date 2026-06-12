---
title: "Lexmark Z12 Printer"
date: 2006-06-03
forum: General Help
---

### Post by brownrl on 2006-06-03
Sorry for the posting in the desktop area weird links on the forum brought me to there first and now I am here.

Anyways:

System -> Administration -> Printing -> Add New Printer
Z12 Autodeteced perfectly
Forward -> Forward -> Apply

DOES NOT PRINT ANYTHING

Tried: USB, Parallel, ubuntu's PPD, linuxprinting.org PPD, google, ubuntuforums search, 2 days headng bashing.

Anyhelp would be hugely appreciated.

BTW: I know Lexmark sucks but its a loaner/gift printer.

If you know a way to get this POS working without having to hack/rebuild cups or gs that would rule as I do not want to do it again later when the next ubuntu comes.

I am writing an article about how Ubuntu finally makes linux useable by making the command shell unnecessary.

THANKS THANKS THANKS
If you have some help then you are l33t!

Rob

---

### Post by meng on 2006-06-03
You've obviously researched this problem extensively, so I'm probably not telling you anything new when I note that linuxprinting officially classifies this model/driver combination as "partially" compatible, which is just one step removed from "paperweight".
[http://www.linuxprinting.org/printer_list.cgi?make=Lexmark](http://www.linuxprinting.org/printer_list.cgi?make=Lexmark)

Of course, with "partially" you would expect it to print *something*, but I'm just saying that even if you get that far your expectations should not be too high.

---

### Post by brownrl on 2006-06-03
No doubt I have seen that page and it does give some bad feelings.

However, I would imagine that partially means, just black and white, or only a certain resolution...

But paperweight is a decent description too... so I guess I am going to go buy the cheapy HP whatever then printing should work unless someone else knows the secret sauce needed to make it go?

R

---

### Post by brownrl on 2006-06-06
Got it to work.

Parallel Port
Black and White printing only
Bidirectional Turned On


Not sure why it works now... I did so much screwing around with cups and everything else so I don't know why it now works. 

I tried to install the z11 sourceforge driver. I think maybe that did something with the /dev/lp0. Like enabled it...

Either way good luck for the other z12 owners out there.

---

### Post by Jim.Frey on 2006-06-16
Lexmark Z12 now works!  :D   I have spent a many hours trying to get this to
work after installing Dapper.  With Breezy, it worked perfectly on the USB port.
With Dapper, I always got a Printer Fault! on USB.   On the parallel port it just
advanced the paper and stopped.

The solution was in the bios:  dma was off.  

Hope this helps somebody.

Jim

---

