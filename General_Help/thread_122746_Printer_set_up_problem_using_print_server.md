---
title: "Printer set up problem using print server"
date: 2006-01-28
forum: General Help
---

### Post by gslater on 2006-01-28
Hi

I am trying to set up my printer on Breezy and cant seem to get it right.  

Here is what I have:

[LIST]
[*]Belkin F1UP0001 Print Server
[*]HP PSC750 Printer/scanner, connected to
[/LIST]

I initially set up the printer on my windows PC using the supplied software which works ok.  When I look at the printer properties it says that it is connected onto 192.168.0.8

Here is what I have tried:

Tried using printer setup in "System", "Administration" & "Printing"....with the connection URI as [http://192.168.0.8](http://192.168.0.8)

I have also tried to download and run the drivers recommened on the HP site for linux ([http://hpinkjet.sourceforge.net/)...but](http://hpinkjet.sourceforge.net/)...but) when I get to the instrucxtion to add the printer it says:

# Enter this command to search for the printer:
$ hp-probe -bnet
# If hp-probe fails, go to the printer, print the network configuration and enter the IP address with this command.
$ hp-makeuri 192.168.0.8

....at which point it comes back with a message:

Creating URIs for '192.168.0.8':
 [ERROR]: Failed (error code=12). Please check address of device and try again.

Can anyone help?:confused:

---

### Post by gslater on 2006-01-29
bump

---

### Post by gslater on 2006-01-30
Still trying

---

### Post by jctilly on 2006-09-18
hello,

use this [http://www.belkin.com/support/download/files/F1UP0001%2520and%2520F5D7231.pdf](http://www.belkin.com/support/download/files/F1UP0001%2520and%2520F5D7231.pdf)

system/administration/printer

add printer

in connection choose HP jet direct

if u use second usb port change port to 9101

nothing else ;) 

jc

---

### Post by stephanvaningen on 2007-11-23
Indeed JCTilly: I did it in similar way
--
Here ([http://ubuntuforums.org/showthread.php?t=122855&highlight=f1up0001](http://ubuntuforums.org/showthread.php?t=122855&highlight=f1up0001)) I wrote on how I did it in Gutsy (7.10).

---

