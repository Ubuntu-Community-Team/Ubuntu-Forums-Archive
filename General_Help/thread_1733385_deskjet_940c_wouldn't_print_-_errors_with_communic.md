---
title: "deskjet 940c wouldn't print - errors with communication and the initial device"
date: 2011-04-19
forum: General Help
---

### Post by shayli147 on 2011-04-19
hello:)
[i use Ubuntu linux 10.04 LTS - the Lucid Lynx]


 i tried to print a document and i got the following message from the "document print status (my jobs)":
"There was a problem processing document 'take it easy' (job 400)"
i tried to print other things but i got the same error.
after any print request i sent the printer asked me to release the paper it took, and when i release it, it printed this:
"Unable to open the initial device, quitting."


 i have "HP Device Manager" installed on my computer, and lately i  tried to install a wireless printer (officejet 4500 g510n-z) through it,  and it failed because the connection between the printer and my  computer disconnected before the terminal finished the installation. i  didn't try to print with the deskjet right after it but now when i try-  it doesn't work, so it might have something to do with my current  problem... also when i looked at the HP Device Manager i saw the deskjet  printer icon marked with X so i used this program's option "Setup  Device" and the X mark disappeared.. and it still doesn't work.
 

well, this is all i know to tell, i hope you could help me to fix it!
thanks a lot for helpers!
 

Shay

---

### Post by Mark Phelps on 2011-04-19
I've found that simply installing HP printers using CUPS works fine, especially if you also use the CUPS drivers.

To access CUPS, open a browser to "localhost:631"

---

### Post by shayli147 on 2011-04-19
> **Mark Phelps said:**
> I've found that simply installing HP printers using CUPS works fine, especially if you also use the CUPS drivers.

To access CUPS, open a browser to "localhost:631"

wow thanks, i didn't know this option before! useful

---

