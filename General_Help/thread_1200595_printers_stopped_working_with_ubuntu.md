---
title: "printers stopped working with ubuntu"
date: 2009-06-30
forum: General Help
---

### Post by Twig E. Pottox on 2009-06-30
Been happily using ubuntu for almost 3 years and never had a printer problem. it always just worked. suddenly last week printers on 2 different machines stopped working. on the machine with the dell printer it prints a few random characters (&^ash&^) then pulls another sheet of paper and repeats until I either shut off the machine or remove its paper supply. I hate to admit that this machine will print the same file from its XP side. so that rules out connectors or printer problems. 

A second machine acted up on the same day. the error message  says no printer is connected although one is. However when a print command is given the machines led's start flashing and no printing occurs.  

Any Ideas on how to troubleshoot this one? I did notice there was a cups file update shortly before the problems started. thanks in advance

---

### Post by Tamlynmac on 2009-06-30
Apparently this printer uses the HP print driver: [http://www.linuxprinting.org/show_printer.cgi?recnum=Dell-P1500](http://www.linuxprinting.org/show_printer.cgi?recnum=Dell-P1500)

The newest driver can be found here: [http://hplipopensource.com/hplip-web/install.html](http://hplipopensource.com/hplip-web/install.html)

The automatic installer instructions are located here:[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

I would suggest the automatic installer - simply follow the instructions.

Good Luck and I hope this helps.

---

### Post by Twig E. Pottox on 2009-06-30
thanks for the input but it did not work..I tried the re install got this far and then it says it  dosent recognise the usb: (note this is a dual boot and xp prints fine)

> steve@amd2900:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.9.6b)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usbsteve@amd2900:~$ hp-setup

HP Linux Imaging and Printing System (ver. 3.9.6b)
Printer/Fax Setup Utility ver. 9.0

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb
Searching... (bus=usb, search=(None) desc=0)
error: No devices found on bus: usb



Note the computer was printing fine until last week.
 This computer prints on the xp side.  the other computer that stopped printing at the same time (a different type of printer) also says there is no printer attached although it is.  


Now my desktop is crammed full of hp install icons an i still cant print

could there be something with the usb? my keybpard and mouse are usb and working fine.
this does not make sense

---

### Post by Tamlynmac on 2009-06-30
Perhaps a problem with that particular USB port?

I experienced a usb port failure due to excessive use (plug & unplug) of a memory stick. Immediately upon insertion in another port the stick was recognized.

Also, have you tried rebooting? I believe that is one of the final steps in the driver install process. It's been a while since I installed that driver, but I do believe it required a reboot.

As I indicated, my original response was based on the link I provided for the Dell1500. I in no way just assumed it was an HP, nor that it required the HP driver.

---

### Post by Twig E. Pottox on 2009-06-30
Thanks again for your response. I have tried several usb ports to no avail. I have also re booted machines, printers etc. 
what stands out is this: Both computers/ printers failed on the same day printing the same files. .doc files generated by open office word. One of the computers is a dual boot set up that prints fine on xp on the same files and  usb port that Ubuntu wont print on . this seems to me to rule out a hardware problem.

The particular file that the printing failed on is one that was a .pdf that I opened in office word and modified and saved as a .doc file. 

I know I'm reaching here with these details but I am offering all that I can think of that could have affected the 2 computers.  Both of these setups had previously worked/ printed fine on many occasions. now they indicate  that there is no printer connected when there is one connected. But if that is so why does the printer start to print upon the print command only it prints a line of garbage then repeats until i shut it off. It is getting a command from the computer to print but dosen't print what is being sent. therefor again the usb connection is good.

Again two computers and printers that worked fine for months failing in the same hour with the same files, while the one computer that is dual boot prints fine from the XP side.  This leads me to believe its not a hardware issue.  I've isolated that out.  Could I have gotten a virus from a PDF file?

again thanks in advance for your help. I think I have a tricky one here.

---

### Post by TomR55 on 2009-06-30
No, I don't believe that you have a virus. I had similar problems earlier this week. Seems that no matter what I did, I could not get any HP InkJet printer(s) to work with Jaunty. 

So, I removed all of the HPLIP and Cups software, and re-installed Cups from the Synaptic Package Manager. 

Went out and bought a refurbed P1006, figuring that I'd use the latest HPLIP and move to laser. Why? Because I suspect that the older generation Cups software, in particular software dealing with InkJet printers is not working with Jaunty.

Next, I navigated to the HPLIP download page, and obtained hp3.9.6b.run and followed the instructions. 

Now, I took the rufurbed printer and installed it on a Windoze box, to make sure that it worked. Next, I shut everything down, moved it to the Linux machine, re-started and followed instructions.

Results:

Well, I can print generated Postscript from my TexLive software, which is what I really needed. I can also print from Browsers, etc. Cannot print from Adobe PDF, however. But, I doubt that this is virus-related. Rather, I believe that it's a software problem (on the Linux side).

Obviously, this is less than a perfect solution. Oh, in order to test the assertion that the latest Cups updates broke anything, I installed those too ... but no difference.

I don't know if any of this really helps, but it's more information that perhaps will prove useful to you in your investigation.

Regards,

TomR

---

### Post by Twig E. Pottox on 2009-07-01
Thanks Tom, at least I'm not alone with this problem. and glad you were able to patch yours together.

My situation is not just with the HP laser and 9.04.  My second machine, which is having the same problem, is running 8.04 and the printer is a Epson stylus C88 ink jet. I have reinstalled the drivers on this machine to no avail. Similarly I have run hp3.9.6b.run on the machine with the HP. After successfully deleting and reinstalling the software it hung when it was time to locate the printer thru the usb. 

That's where the problem lies with both systems. They don't see the printer. But when a print command is given there is some reaction from the printers but the desired printing fails. This tells me that the issue is one of recognizing the usb printers. most likely a software glitch  Again these printers were recognized by the computers until they both failed at the same time last week.

Is there something besides the cups and drivers that could be the culprit?

As much as I like tinkering with these things I really need to get back to strewing resumes (CVs)with these computers so I can once again afford my little diversions as a responsible employed person. 

Thanks again and thanks in advance for any more ideas.

---

### Post by Twig E. Pottox on 2009-07-01
bump  - anybody had these issues?

---

### Post by greenstar on 2009-07-04
Yes, and I have found no solution as yet. 

I'm using a Samsung ML-2510 which is attached to one of my ubuntu boxes and shared out to the others on my network. It prints fine from the machine it's attached to, but causes all kind of havoc on the machines using it as a network printer. The flashing lights and freezes as described above. It completely locks up all applications that I've tried printing from. It also lock up when trying to open the printer properties from System->Administration->Printing.

Any help would be greatly appreciated.

---

### Post by Twig E. Pottox on 2009-07-05
I don't Think this is the same problem.  The system and programs are fine. local printers don't work no network printers.  only the printing is affected. No crashing just the printer prints a line of garbage then loads another sheet to do the same etc, etc,. ......


This problem has shown up on a third computer this one a Vista / Ubuntu dual boot unit.  I loaded Ubuntu 9.04 on a new hard drive yesterday, did all the updates loaded the printer drivers and attempted to print a test page.  again experienced the above loop.  Again this computer prints to this printer from the windows side I presume this removes hardware problems from the equation.  

Still looking for a solve. Any ideas will be appreciated, thanks in advance

---

### Post by Twig E. Pottox on 2009-07-07
Here's an error message. I cant make much sense out of it.
note HP makes the dell P1500 and the 1100 driver has worked for months

> Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Dell-Laser-Printer-P1500 (default)>,
 'cups_instance': None,
 'cups_queue': 'Dell-Laser-Printer-P1500',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Dell/Laser%20Printer%20P1500',
                       'printer-info': u'Dell Dell Laser Printer P1500',
                       'printer-is-shared': True,
                       'printer-location': u'amd2900',
                       'printer-make-and-model': u'Dell 1100, SpliX V. 2.0.0',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 143444,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Dell-Laser-Printer-P1500'},
 'cups_printer_remote': False,
 'is_cups_class': False}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'Altitude': u'LOW',
                                            u'ColorModel': u'Gray',
                                            u'Duplex': u'None',
                                            u'EconoMode': u'0',
                                            u'InputSlot': u'Auto',
                                            u'JamRecovery': u'False',
                                            u'MediaType': u'OFF',
                                            u'PageRegion': u'Letter',
                                            u'PageSize': u'Letter',
                                            u'PowerSave': u'5',
                                            u'Resolution': u'600dpi',
                                            u'TonerDensity': u'3'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Error log checkpoint):
{'cups_server_settings': {'DefaultAuthType': 'Basic',
                          'MaxLogSize': '2000000',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '0',
                          '_remote_admin': '0',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '0',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 14663L,
 'error_log_debug_logging_set': True}
Page 7 (Print test page):
{'test_page_attempted': '05/Jul/2009:11:31:41 +0000',
 'test_page_job_status': [(True,
                           17,
                           'Dell-Laser-Printer-P1500',
                           'Test Page',
                           'Canceled',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-us',
                            'document-format': u'application/postscript',
                            'job-hold-until': u'no-hold',
                            'job-id': 17,
                            'job-k-octets': 17,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/17',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'steve',
                            'job-preserved': False,
                            'job-printer-state-message': u'Printer is now on-line.',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1246811597,
                            'job-printer-uri': u'ipp://amd2900:631/printers/Dell-Laser-Printer-P1500',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 7,
                            'job-state-reasons': u'job-canceled-by-user',
                            'job-uri': u'ipp://localhost:631/jobs/17',
                            'job-uuid': u'urn:uuid:380a8566-27a7-3b53-485d-d44ffef55635',
                            'printer-uri': u'ipp://localhost/printers/Dell-Laser-Printer-P1500',
                            'time-at-completed': 1246811532,
                            'time-at-creation': 1246811501,
                            'time-at-processing': 1246811501})],
 'test_page_successful': False}
Page 8 (Error log fetch):
{'error_log': ['D [05/Jul/2009:11:31:24 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:24 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:24 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Jul/2009:11:31:24 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:24 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:24 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:24 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Jul/2009:11:31:24 -0500] [Job 1] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 2] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 3] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 4] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 5] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 6] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 7] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 8] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 9] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 10] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 11] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 12] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 13] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 14] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 15] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] [Job 16] Loading attributes...',
               'D [05/Jul/2009:11:31:24 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:24 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:24 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:24 -0500] Create-Printer-Subscription /',
               'D [05/Jul/2009:11:31:24 -0500] cupsdCreateSubscription(con=0xb8038fb0(8), uri="/")',
               'D [05/Jul/2009:11:31:24 -0500] pullmethod="ippget"',
               'D [05/Jul/2009:11:31:24 -0500] notify-lease-duration=86400',
               'D [05/Jul/2009:11:31:24 -0500] notify-time-interval=0',
               'D [05/Jul/2009:11:31:24 -0500] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [05/Jul/2009:11:31:24 -0500] Added subscription 27 for server',
               'I [05/Jul/2009:11:31:24 -0500] Saving subscriptions.conf...',
               'D [05/Jul/2009:11:31:24 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:25 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:25 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:25 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:25 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:25 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:41 -0500] cupsdAcceptClient: 9 from localhost (Domain)',
               'D [05/Jul/2009:11:31:41 -0500] cupsdReadClient: 9 POST /printers/Dell-Laser-Printer-P1500 HTTP/1.1',
               'D [05/Jul/2009:11:31:41 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:41 -0500] Print-Job ipp://localhost/printers/Dell-Laser-Printer-P1500',
               'D [05/Jul/2009:11:31:41 -0500] [Job ???] Auto-typing file...',
               'I [05/Jul/2009:11:31:41 -0500] [Job ???] Request file type is application/postscript.',
               'D [05/Jul/2009:11:31:41 -0500] add_job: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:41 -0500] Adding default job-sheets values "none,none"...',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] Adding start banner page "none".',
               'I [05/Jul/2009:11:31:41 -0500] Saving subscriptions.conf...',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] Adding end banner page "none".',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] File of type application/postscript queued by "steve".',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] hold_until=0',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] Queued on "Dell-Laser-Printer-P1500" by "steve".',
               'I [05/Jul/2009:11:31:41 -0500] Saving subscriptions.conf...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] job-sheets=none,none',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] banner_page = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] argv[0]="Dell-Laser-Printer-P1500"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] argv[1]="17"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] argv[2]="steve"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] argv[3]="Test Page"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] argv[4]="1"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] argv[5]="job-uuid=urn:uuid:380a8566-27a7-3b53-485d-d44ffef55635"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] argv[6]="/var/spool/cups/d00017-001"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[9]="SERVER_ADMIN=root@amd2900"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[11]="TMPDIR=/var/spool/cups/tmp"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[12]="TZ=America/Chicago"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[13]="USER=root"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[16]="IPP_PORT=631"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[17]="CHARSET=utf-8"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[18]="LANG=en_US.UTF8"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[19]="PPD=/etc/cups/ppd/Dell-Laser-Printer-P1500.ppd"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[20]="RIP_MAX_CACHE=8m"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[21]="CONTENT_TYPE=application/postscript"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[22]="DEVICE_URI=usb://Dell/Laser%20Printer%20P1500"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[23]="PRINTER=Dell-Laser-Printer-P1500"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[24]="FINAL_CONTENT_TYPE=printer/Dell-Laser-Printer-P1500"',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] Started filter /usr/lib/cups/filter/pstopdf (PID 4945)',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] Started filter /usr/lib/cups/filter/pdftopdf (PID 4948)',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] Started filter /usr/lib/cups/filter/pdftoraster (PID 4949)',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] Started filter /usr/lib/cups/filter/rastertoqpdl (PID 4952)',
               'I [05/Jul/2009:11:31:41 -0500] [Job 17] Started backend /usr/lib/cups/backend/usb (PID 4955)',
               'I [05/Jul/2009:11:31:41 -0500] Saving subscriptions.conf...',
               'D [05/Jul/2009:11:31:41 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] pstopdf 6 args: 17 steve Test Page 1 job-uuid=urn:uuid:380a8566-27a7-3b53-485d-d44ffef55635 /var/spool/cups/d00017-001',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] PPD: /etc/cups/ppd/Dell-Laser-Printer-P1500.ppd',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] SpliX SpliX filter V. 2.0.0 by Aur\xc3\xa9lien Croc (AP\xc2\xb2C)',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] SpliX More information at: [http://splix.ap2c.org](http://splix.ap2c.org)',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] SpliX Compiled with: Threads=enabled (#=2, Cache=30), JBIG=disabled, BlackOptim=enabled',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] SpliX Monochrome printer Dell 1100 with QPDL v. 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] SpliX Cache controller thread loaded and is waiting for a job',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Printer using device file "/dev/usblp0"...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] backendRunLoop(print_fd=0, device_fd=5, use_bc=1, side_cb=0xb7fb8a80)',
               'I [05/Jul/2009:11:31:41 -0500] Saving subscriptions.conf...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Resolution: 600',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Page size: Letter',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Width: 612.00, height: 792.00, absolute margins: 10.75, 15.00, 601.25, 777.00',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Relative margins: 10.75, 15.00, 10.75, 15.00',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] PPD options: -r600 -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] PostScript to be injected:',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Running cat | /usr/bin/ps2pdf13 -dAutoRotatePages=/None -dAutoFilterColorImages=false                -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                -dDoNumCopies -dPDFSETTINGS=/printer -r600 -dDEVICEWIDTHPOINTS=612.00 -dDEVICEHEIGHTPOINTS=792.00 - -',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] GPL Ghostscript 8.64: Set UseCIEColor for UseDeviceIndependentColor to work properly.',
               'D [05/Jul/2009:11:31:41 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:31:41 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:41 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:41 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Jul/2009:11:31:41 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:41 -0500] cupsdCloseClient: 12',
               'D [05/Jul/2009:11:31:41 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:31:41 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:41 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:41 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:41 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:41 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:41 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:41 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:41 -0500] Get-Job-Attributes ipp://localhost/jobs/17',
               'D [05/Jul/2009:11:31:41 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:41 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:41 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:41 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:41 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:41 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:41 -0500] cupsdCloseClient: 12',
               'D [05/Jul/2009:11:31:41 -0500] PID 4945 (/usr/lib/cups/filter/pstopdf) exited with no errors.',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Ghostscript command line: /usr/bin/gs -dQUIET -dPARANOIDSAFER -dNOPAUSE -dBATCH -sDEVICE=cups -sstdout=%stderr -sOutputFile=%stdout -I/usr/share/cups/fonts -r600x600 -dMediaPosition=1 -dDEVICEWIDTHPOINTS=612 -dDEVICEHEIGHTPOINTS=792 -dcupsBitsPerColor=1 -dcupsColorOrder=0 -dcupsColorSpace=3 -dcupsCompression=13 -scupsPageSizeName=Letter -c -f -_',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[8]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[9]="SERVER_ADMIN=root@amd2900"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[10]="SOFTWARE=CUPS/1.3.9"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[11]="TZ=America/Chicago"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[12]="USER=root"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[13]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[14]="CUPS_ENCRYPTION=IfRequested"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[15]="IPP_PORT=631"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[16]="CHARSET=utf-8"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[17]="LANG=en_US.UTF8"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[18]="PPD=/etc/cups/ppd/Dell-Laser-Printer-P1500.ppd"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[19]="RIP_MAX_CACHE=8m"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[20]="CONTENT_TYPE=application/postscript"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[21]="DEVICE_URI=usb://Dell/Laser%20Printer%20P1500"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[22]="PRINTER=Dell-Laser-Printer-P1500"',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] envp[23]="FINAL_CONTENT_TYPE=printer/Dell-Laser-Printer-P1500"',
               'D [05/Jul/2009:11:31:41 -0500] PID 4948 (/usr/lib/cups/filter/pdftopdf) exited with no errors.',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] num_components = 1, depth = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_gray = 1, dither_grays = 2',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_color = 0, dither_colors = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Updating PageSize to [612 792]...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting initial media size, [612 792] = 5100x6600 pixels...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting MediaPosition to 1...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting cupsBitsPerColor to 1...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting cupsColorOrder to 0...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting cupsColorSpace to 3...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting cupsCompression to 13...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting cupsPageSizeName to "Letter"...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] num_components = 1, depth = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_gray = 1, dither_grays = 2',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_color = 0, dither_colors = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting initial media size, [612 792] = 5100x6600 pixels...',
               'I [05/Jul/2009:11:31:41 -0500] Saving subscriptions.conf...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] num_components = 1, depth = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_gray = 1, dither_grays = 2',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_color = 0, dither_colors = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting LeadingEdge to 0...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] num_components = 1, depth = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_gray = 1, dither_grays = 2',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_color = 0, dither_colors = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Updating PageSize to [612 792]...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] size = Letter',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] margins[] = [ 0.149306 0.208333 0.149306 0.208333 ]',
               'D [05/Jul/2009:11:31:41 -0500] PID 4949 (/usr/lib/cups/filter/pdftoraster) exited with no errors.',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting LeadingEdge to 0...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] num_components = 1, depth = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_gray = 1, dither_grays = 2',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_color = 0, dither_colors = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Setting LeadingEdge to 0...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] num_components = 1, depth = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_gray = 1, dither_grays = 2',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] max_color = 0, dither_colors = 0',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] Updating PageSize to [612 792]...',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] size = Letter',
               'D [05/Jul/2009:11:31:41 -0500] [Job 17] margins[] = [ 0.149306 0.208333 0.149306 0.208333 ]',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdCloseClient: 12',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:42 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdCloseClient: 12',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:42 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Document width=4928 height=6350',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Page width=5104 (638) height=6350',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Margin width in bytes=11 height=125',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Clipping X=0 Y=0',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Line size=616, Plane size=4210800, bytes to copy=616',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] cups_print_chunked - flip = 0, height = 6350',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Next requested page : 1 (# pages into memory=0/30)',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Page 1 (4921\xc3\x976350 on 5104\xc3\x976600) has been successfully loaded into memory',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=22204',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=972',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=6936',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=3124',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=600',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=296',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=1952',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=15040',
               'I [05/Jul/2009:11:31:42 -0500] Saving subscriptions.conf...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting AdvanceDistance to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting AdvanceMedia to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Collate to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting CutMedia to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Duplex to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Jog to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting LeadingEdge to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Margins to 0 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting MirrorPrint to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting NegativePrint to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting OutputFaceUp to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Separations to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting TraySwitch to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Tumble to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsMediaType to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsBitsPerColor to 1...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsColorOrder to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsColorSpace to 3...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsCompression to 13...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsRowCount to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsRowFeed to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsRowStep to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsBorderlessScalingFactor to 1.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger0 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger1 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger2 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger3 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger4 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger5 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger6 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger7 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger8 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger9 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger10 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger11 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger12 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger13 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger14 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger15 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal0 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal1 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal2 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal3 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal4 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal5 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal6 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal7 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal8 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal9 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal10 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal11 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal12 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal13 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal14 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal15 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString0 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString1 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString2 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString3 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString4 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString5 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString6 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString7 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString8 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString9 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString10 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString11 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString12 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString13 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString14 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString15 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsMarkerType to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsRenderingIntent to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsPageSizeName to "Letter"...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] num_components = 1, depth = 1',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] max_gray = 1, dither_grays = 2',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] max_color = 0, dither_colors = 0',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Updating PageSize to [612 792]...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] size = Letter',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] margins[] = [ 0.149306 0.208333 0.149306 0.208333 ]',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=22668',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=26224',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=27636',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=22520',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=25768',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=28140',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=28484',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=21828',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=11820',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=1608',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting AdvanceDistance to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting AdvanceMedia to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Collate to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting CutMedia to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Duplex to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Jog to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting LeadingEdge to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Margins to 0 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting MirrorPrint to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting NegativePrint to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting OutputFaceUp to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Separations to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting TraySwitch to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting Tumble to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsMediaType to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsBitsPerColor to 1...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsColorOrder to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsColorSpace to 3...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsCompression to 13...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsRowCount to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsRowFeed to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsRowStep to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsBorderlessScalingFactor to 1.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger0 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger1 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger2 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger3 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger4 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger5 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger6 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger7 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger8 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger9 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger10 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger11 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger12 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger13 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger14 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsInteger15 to 0...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal0 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal1 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal2 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal3 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal4 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal5 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal6 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal7 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal8 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal9 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal10 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal11 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal12 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal13 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal14 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsReal15 to 0.0000...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString0 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString1 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString2 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString3 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString4 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString5 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString6 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString7 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString8 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString9 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString10 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString11 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString12 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString13 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString14 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsString15 to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsMarkerType to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsRenderingIntent to ""...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Setting cupsPageSizeName to "Letter"...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] num_components = 1, depth = 1',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] cupsColorSpace = 3, cupsColorOrder = 0',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] cupsBitsPerPixel = 1, cupsBitsPerColor = 1',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] max_gray = 1, dither_grays = 2',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] max_color = 0, dither_colors = 0',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Updating PageSize to [612 792]...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] size = Letter',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] margins[] = [ 0.149306 0.208333 0.149306 0.208333 ]',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=304',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=28516',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=72',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=412',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=212',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=20560',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX No more pages',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Compression thread: work done. See ya',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=2068',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=9352',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=14792',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=7704',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=16584',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=7240',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=16320',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=5256',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=8756',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=6332',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=4220',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=3492',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=384',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=172',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=136',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=132',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=164',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=1648',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=10944',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=7876',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=28852',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=23488',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=1932',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xe, size=19808',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=68',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Finished band encoding: type=0xd, size=3880',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Page 1 has been compressed and is ready for rendering',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] SpliX Compression thread: work done. See ya',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdCloseClient: 12',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:42 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdCloseClient: 12',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:42 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:42 -0500] [Job 17] Read 8192 bytes of print data...',
               'I [05/Jul/2009:11:31:42 -0500] Saving subscriptions.conf...',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdCloseClient: 12',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 12 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:42 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:42 -0500] cupsdCloseClient: 12',
               'D [05/Jul/2009:11:31:42 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:31:42 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:31:42 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:31:42 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:31:42 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:31:43 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:43 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:43 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:43 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:44 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:44 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:45 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:45 -0500] [Job 17] Received 4 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:45 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:45 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:45 -0500] [Job 17] Received 25 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:45 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:46 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:46 -0500] [Job 17] Received 6 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:46 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Received 1 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Received 151 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:48 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Received 1 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Received 1 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:49 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:50 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Received 47 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:51 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:52 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:52 -0500] [Job 17] Received 50 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:52 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:53 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:53 -0500] [Job 17] Received 4 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:53 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:54 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:54 -0500] [Job 17] Received 25 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:54 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:54 -0500] [Job 17] Wrote 8192 bytes of print data...',
               'D [05/Jul/2009:11:31:54 -0500] [Job 17] Received 212 bytes of back-channel data!',
               'D [05/Jul/2009:11:31:54 -0500] [Job 17] Read 8192 bytes of print data...',
               'D [05/Jul/2009:11:32:12 -0500] cupsdAcceptClient: 12 from localhost (Domain)',
               'D [05/Jul/2009:11:32:12 -0500] cupsdReadClient: 12 POST /jobs/ HTTP/1.1',
               'D [05/Jul/2009:11:32:12 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:32:12 -0500] Cancel-Job ipp://localhost/jobs/17',
               'D [05/Jul/2009:11:32:12 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'I [05/Jul/2009:11:32:12 -0500] Saving subscriptions.conf...',
               'I [05/Jul/2009:11:32:12 -0500] Saving subscriptions.conf...',
               'I [05/Jul/2009:11:32:12 -0500] [Job 17] Canceled by "steve".',
               'D [05/Jul/2009:11:32:12 -0500] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:32:12 -0500] PID 4952 (/usr/lib/cups/filter/rastertoqpdl) exited with no errors.',
               'D [05/Jul/2009:11:32:13 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [05/Jul/2009:11:32:13 -0500] [Job 17] Unloading...',
               'D [05/Jul/2009:11:32:13 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [05/Jul/2009:11:32:13 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:32:13 -0500] Get-Jobs ipp://localhost/printers/',
               'D [05/Jul/2009:11:32:13 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:32:13 -0500] cupsdCloseClient: 13',
               'D [05/Jul/2009:11:32:13 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [05/Jul/2009:11:32:13 -0500] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [05/Jul/2009:11:32:13 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:32:13 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:32:13 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:32:13 -0500] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:32:13 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:32:13 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:32:13 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:32:13 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:32:13 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:32:13 -0500] cupsdCloseClient: 13',
               'D [05/Jul/2009:11:32:58 -0500] PID 4955 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [05/Jul/2009:11:33:13 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:33:13 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:33:13 -0500] Get-Notifications /',
               'D [05/Jul/2009:11:33:13 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'D [05/Jul/2009:11:33:13 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:33:13 -0500] [Job 1] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 2] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 3] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 4] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 5] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 6] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 7] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 8] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 9] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 10] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 11] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 12] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 13] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 14] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 15] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] [Job 16] Unloading...',
               'D [05/Jul/2009:11:33:13 -0500] Report: clients=3',
               'D [05/Jul/2009:11:33:13 -0500] Report: jobs=17',
               'D [05/Jul/2009:11:33:13 -0500] Report: jobs-active=0',
               'D [05/Jul/2009:11:33:13 -0500] Report: printers=1',
               'D [05/Jul/2009:11:33:13 -0500] Report: printers-implicit=0',
               'D [05/Jul/2009:11:33:13 -0500] Report: stringpool-string-count=1458',
               'D [05/Jul/2009:11:33:13 -0500] Report: stringpool-alloc-bytes=8608',
               'D [05/Jul/2009:11:33:13 -0500] Report: stringpool-total-bytes=32736',
               'D [05/Jul/2009:11:33:17 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:33:17 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:33:17 -0500] Get-Job-Attributes ipp://localhost/jobs/17',
               'D [05/Jul/2009:11:33:17 -0500] [Job 17] Loading attributes...',
               'D [05/Jul/2009:11:33:17 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:33:17 -0500] cupsdReadClient: 8 POST / HTTP/1.1',
               'D [05/Jul/2009:11:33:17 -0500] cupsdAuthorize: No authentication data provided.',
               'D [05/Jul/2009:11:33:17 -0500] Cancel-Subscription /',
               'D [05/Jul/2009:11:33:17 -0500] cupsdIsAuthorized: requesting-user-name="steve"',
               'I [05/Jul/2009:11:33:17 -0500] Saving subscriptions.conf...',
               'D [05/Jul/2009:11:33:17 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)',
               'D [05/Jul/2009:11:33:17 -0500] cupsdAcceptClient: 13 from localhost (Domain)',
               'D [05/Jul/2009:11:33:17 -0500] cupsdReadClient: 13 GET /admin/log/error_log HTTP/1.1',
               'D [05/Jul/2009:11:33:17 -0500] cupsdAuthorize: No authentication data provided.'],
 'error_log_debug_logging_unset': True}
Page 9 (Printer state reasons):
{'printer-state-message': u'Printer is now on-line.',
 'printer-state-reasons': [u'none']}
Page 10 (Locale issues):
{'printer_page_size': u'Letter',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_US',
 'user_locale_messages': 'en_US'}

---

### Post by Richard Perry on 2009-07-12
I have had nothing but problems with jaunty.  Initially I couldn't connect to the internet either wired or wireless.  I solved that by using Windows to download a live cd.  Reinstalled and internet problems solved.  Then the printer, an HP j6400 wireless all-in-one, stopped working.  It had worked with the upgrade that I installed over.  I have gone through the forums and tried everything including removing HPLIP and reinstalling a later release from sourceforge.  Nothing has worked.

But I have found the perfect solution.  Download 8.10, remove jaunty, install 8.10.  Return to happy computing and wait for the geniuses to figure out what they screwed up and how to fix it.  Maybe they will check to see that future releases actually work before they release them.

Why do we need all these new releases anyway?

Can't wait for google to simplify things.

---

