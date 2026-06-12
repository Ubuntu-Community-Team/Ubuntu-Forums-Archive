---
title: "Print Server"
date: 2010-02-28
forum: General Help
---

### Post by ShadowOps on 2010-02-28
Hi I'm looking to set up a basic server for printing and file sharing.. 
The problem is the printer has no Linux drivers what so ever and the network consists of Windows and Mac boxes...

Is there a way to set up an ubuntu server to act just like one of the print server devices from Lexmark?

The printer is a Lexmark x5070

---

### Post by dcstar on 2010-02-28
> **ShadowOps said:**
> Hi I'm looking to set up a basic server for printing and file sharing.. 
The problem is the printer has no Linux drivers what so ever and the network consists of Windows and Mac boxes...

Is there a way to set up an ubuntu server to act just like one of the print server devices from Lexmark?

The printer is a Lexmark x5070

In theory a Linux Print Sever will only be a conduit for the print jobs from your clients to the printer connected to the Linux server, and they are the ones that will use the Printer Drivers. AFAIK you will only need Linux print driver when trying to print from a Linux PC.

You should be able to just set up shared printers according to the various HOWTOs around the place.

---

