---
title: "How to print from Windows 7 on Maverick Samba/CUPS server?"
date: 2011-04-10
forum: General Help
---

### Post by iamtim on 2011-04-10
I have a pair of Windows 7 Home premium desktops I am trying to hook up to a Brother Fax4100 machine USB'ed into my Ubuntu 10.10 box. The box is updated and upgraded and running Samba and CUPS.

1. I can print from an OS 10.6 macmini and a pair of Windows XP laptops without trouble. I know CUPS is working.

2. I have browsable = yes in my Samba printers section. I can actually see them in my OSX finder. I KNOW Samba is working

3. net view \\<hostname> on the Windows 7 box returns the printer share names correctly. So I REALLY know Samba is working

I have twiddled and tweaked my smb.conf to a faretheewell and am now running with

[global]
  printcap name = cups  
  printing = cups   
  security = share   
[printers]   
  browseable = yes   
  printable = yes   
  public = yes   
  create mode = 0700   
  guest only = yes   
  use client driver = yes
  guest account = smbprint   
  path = /home/smbprint

per [http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html](http://tldp.org/HOWTO/Debian-and-Windows-Shared-Printing/sharing_with_windows.html)

But I cannot get my Windows 7 boxes to find the printers through the add printer wizard, either as a \\<hostname>\Brother_Fax-4100 queue or by http://<ipaddress>:631/printers/Brother_FAX-4100. 

The W7 boxes SAY they've added them, but they won't print test pages or test documents. The printer doesn't show up in Network Places. Any monkeying around in the queues throws an "Access denied." error.

I have turned off the Homegroup feature in W7. Network and printer sharing is on. I have defined the print server hostname in the W7 host file. I can go to [https://hostname:631](https://hostname:631) and find the CUPS page on the W7 machines.

I have spent two weekends on this to absolutely no avail. Can anybody tell me how to get Windows 7 CUPS and Samba printer working?

---

### Post by ruudschellekens on 2011-06-02
I am having the EXACT same problem. Macs are printing fine, printer works, file share works, printer shared seems to be OK. Can it be authentication? My mac asked for a user + pass when printing. Windows does not.

The sad part is that I managed to get the printer working yesterday. Now I rebooted my ubuntu machine and it is not working any longer. :S

Has anyone found a solution?

---

### Post by drdos2006 on 2011-06-02
It has been a while since I tried this but the upshot is this.
Windows 7 has removed Internet Printing Protocol from Windows 7.
( They want you to connect Windows 7 to a Windows server)
Microsoft has issued a patch but I could never get it to work so I removed Windows 7 completely.
Google result for Windows 7 IPP is this:

[http://answers.microsoft.com/en-us/windows/forum/windows_7-hardware/problem-adding-ipp-printer-to-windows-7-client/4bb7f253-ba0a-4d01-9a4e-7841563d114b](http://answers.microsoft.com/en-us/windows/forum/windows_7-hardware/problem-adding-ipp-printer-to-windows-7-client/4bb7f253-ba0a-4d01-9a4e-7841563d114b)

regards

---

