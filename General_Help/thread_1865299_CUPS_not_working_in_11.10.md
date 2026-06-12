---
title: "CUPS not working in 11.10?"
date: 2011-10-19
forum: General Help
---

### Post by lowracer on 2011-10-19
Howdy,
I just upgraded my 11.04 system on a T510 Lenovo laptop to Ubuntu 11.10.  I was able to print to my HP M1212nf printer before the upgrade.  Of course after the install the printer was no longer available to send print jobs to, so I tried to reinstall via the hplip program.  This installer could not find the right PPD for this printer. 

So I tried to find the PPD on the net to no avail.  Then I tried to get into CUPS to see what the heck is going on and typing localhost:631 into Firefox gives the error message "Firefox can't establish a connection to the server at localhost:631."  

So I uninstall & reinstall CUPS in the ubuntu software center.  I got a screenful of errors on doing that.  What is going on here?  Is CUPS supported under 11.10 and how can I get this networked printer to print? 

Thanks...
-Mark

---

### Post by bibble235 on 2011-10-19
You need to provide logs.

People might suggest you do a 

sudo apt-get --purge remove cups
sudo apt-get update
sudo apt-get install cups

---

### Post by sammiev on 2011-10-19
I'm using CUPS on mine without any problems, so it's supported. I tried it 2 days a go when the kids had homework to print from their laptop. Would be nice to see the logs to see what happen.

---

### Post by lowracer on 2011-10-20
> **bibble235 said:**
> 
sudo apt-get --purge remove cups
sudo apt-get update
sudo apt-get install cups

That did the trick.  Thanks!
-Mark

---

