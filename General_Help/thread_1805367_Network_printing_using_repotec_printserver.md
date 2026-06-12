---
title: "Network printing using repotec printserver"
date: 2011-07-15
forum: General Help
---

### Post by john johansson on 2011-07-15
I'm trying to print using a repotec print server.
I have installed the print drivers for a canon mp540 and can print via usb.
When I try to set up the same Printer as a network printer the system cant find the driver.
The network printing works fine in windows. I can ping the server so I think its a matter of getting the system to look for the driver in the right place. I'm a complete novice in linux so help would be appreciated.

---

### Post by bduxbury on 2012-03-03
> **john johansson said:**
> I'm trying to print using a repotec print server.
I have installed the print drivers for a canon mp540 and can print via usb.
When I try to set up the same Printer as a network printer the system cant find the driver.
The network printing works fine in windows. I can ping the server so I think its a matter of getting the system to look for the driver in the right place. I'm a complete novice in linux so help would be appreciated.

John I am using a repotec rp ub2801A under ubuntu version 10.04 with a hp 2550 laser printer.
First thing is go to windows and look at the printer properties find out from the port setting what the IP address is that was assigned to the print server.  you may remember what it is already.

In Ubuntu click on system - administration - printing 
then click on ADD
select network printer
select app socket / hp direct as type
in the host box type in 192.168.1.xx
xx being the ip address whatever you made it for the print server you might have a different ip range like 10.0.0.1 - 10.0.0.254
the port number has to be 9100 

I got my hp to print via the usb ip print server 

Hopefully this will help you with your situation as it took me a while to figure this out for myself to get it to work for my situation which is similar to yours
if you cannot find the driver listed you may need to use a ndis wrapper to wrap the windows printer driver inf file into ubuntu- 
see [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) on how to use an ndis wrapper in ubuntu.

 Alternatively but not very likely the manufacturer may have an ubuntu driver on their web site that can be downloaded.
If it can be downloaded go to terminal under accessories
type in 
 [B]sudo ./canonLBP_install.sh PRINTER_MODEL

You will have to change the cannonlbp_install.sh to the file name you down loaded 
and printer_model is the actual printer model name you have. eg LBP810 

ls
cd directory name
[/B] 
to find the file you downloaded ls is a directory commandto list the contents

---

