---
title: "Printing to wrong tray on network printer"
date: 2009-07-27
forum: General Help
---

### Post by ugalileo on 2009-07-27
I'm using a network printer via ip address and DLink PrintServer sucessfully via Dlink Print Server DPR-1260 from both windows and ubuntu.

Problem is, ubuntu always prints to the MP Tray (Manual paper feed thru door), not from Tray1(default).  Changing the settings does not help.

Model: Brother HL-1650. 

Installed 
# Printer configuration file for CUPS v1.3.9
# Written by cupsd on 2009-07-27 03:25
<DefaultPrinter Brother-HL-1650>
Info Brother HL-1650
Location
DeviceURI socket://192.168.2.6:9100
State Idle
StateTime 1248679493
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

I did
# sudo apt-get isntall brother-cups-wrapper-laser1 
That did not bring in more Brother printer models and did not help.

Any idea what to do here? Is this a bug?
Thank you

---

