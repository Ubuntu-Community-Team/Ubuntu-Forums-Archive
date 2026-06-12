---
title: "I can't get any applications to print on an Epson Stylus Photo 750!"
date: 2006-03-13
forum: General Help
---

### Post by tgoose on 2006-03-13
While the **edit: nozzle test** page happily prints away, nothing else does anything. It shows up in the printer queue but doesn't get any further than that. I've tried with the Gimp and most parts of OpenOffice.org but with no joy. Does anyone have any ideas? Thanks in advance.

---

### Post by z_diver on 2006-03-13
What happens if you use lp in conjunction with a text file directly?  Do you get any error messages?  

```
lpq
lp mytest.txt
```

---

### Post by learning curve on 2006-03-13
See if there is a different driver available for that printer or just try to uninstall and then re-install.  Is your printer direct connected via USB or Networked?

If you strke me down, I shall become more powerful than you can possibly imagine.

Learning Curve:)

---

### Post by Tipo on 2006-03-13
Probably a dumb question to ask now, but do you have your printer set up via: System -> Administration -> Printing?

---

### Post by rplantz on 2006-03-13
I got both my Epson Stylus CX-6400 all-in-one and Samsung ML-1430 printers working using System->Administration->Printing. First, I deleted the printers. Then I plugged both of them in (USB) and turned them on. When I added the printers (in Systme->Administration->Printing), both were detected. I added them one at a time, using the defaults that were presented to me. I think the key was to have them plugged in and turned on when I added them, although I haven't tried to prove this.

---

### Post by tgoose on 2006-03-14
[QUOTE=z_diver]What happens if you use lp in conjunction with a text file directly?  Do you get any error messages?  

```
lpq
lp mytest.txt
```[/QUOTE]
I get
```
lp: unable to print file: client-error-bad-request
```

[QUOTE=learning curve]See if there is a different driver available for that printer or just try to uninstall and then re-install.  Is your printer direct connected via USB or Networked?[/QUOTE]
It's connected by USB, although I think the original settings had it to networking :-k . I've fiddled around with it a bit in a bid to get it working so I might have done more harm than good!

[QUOTE=Tipo]Probably a dumb question to ask now, but do you have your printer set up via: System -> Administration -> Printing?[/QUOTE]
It says "ready" underneath it

[QUOTE=rplantz]I got both my Epson Stylus CX-6400 all-in-one and Samsung ML-1430 printers working using System->Administration->Printing. First, I deleted the printers. Then I plugged both of them in (USB) and turned them on. When I added the printers (in Systme->Administration->Printing), both were detected. I added them one at a time, using the defaults that were presented to me. I think the key was to have them plugged in and turned on when I added them, although I haven't tried to prove this.[/QUOTE]
I just get the same reponses from everything as before.


Thanks for all the suggestions so far :) The exact error message I get in the print queue (from OpenOffice) is "Pending: printer-stopped".

I've also just noticed I made a mistake in my first post :oops:. When I said it printed the test page, I meant that mtink printed the nozzle test page. The actual "test page" button just adds to the queue like everything else.

---

### Post by tgoose on 2006-03-14
Oddly enough I've now found one page from a couple of days ago that I remember was printed from Evince, but that does the same thing too now. From time to time an exclamation mark appears on the printer icon and it keeps telling me it's paused. If I resume it is simply pauses again after a couple of seconds.

edit: 

Having found my problem now seems to have similarites with [http://www.ubuntuforums.org/showthread.php?t=121580](http://www.ubuntuforums.org/showthread.php?t=121580) , I've followed some advice on there and come up with an error log:
```

D [14/Mar/2006:17:01:33 +0000] LoadAllJobs: Loading attributes for job 5...
D [14/Mar/2006:17:01:33 +0000] LoadAllJobs: Loading attributes for job 7...
D [14/Mar/2006:17:01:33 +0000] LoadAllJobs: Loading attributes for job 6...
D [14/Mar/2006:17:01:33 +0000] LoadAllJobs: Loading attributes for job 9...
D [14/Mar/2006:17:01:33 +0000] LoadAllJobs: Loading attributes for job 8...
D [14/Mar/2006:17:01:33 +0000] LoadAllJobs: Loading attributes for job 10...
I [14/Mar/2006:17:01:33 +0000] Full reload complete.
D [14/Mar/2006:17:01:33 +0000] StartListening: NumListeners=1
D [14/Mar/2006:17:01:33 +0000] StartListening: address=7f000001 port=631
D [14/Mar/2006:17:01:33 +0000] ResumeListening: setting input bits...
D [14/Mar/2006:17:01:38 +0000] AcceptClient: 5 from localhost:631.
D [14/Mar/2006:17:01:38 +0000] ReadClient: 5 POST / HTTP/1.1
D [14/Mar/2006:17:01:38 +0000] ProcessIPPRequest: 5 status_code=0
D [14/Mar/2006:17:01:38 +0000] ReadClient: 5 POST / HTTP/1.1
D [14/Mar/2006:17:01:38 +0000] ProcessIPPRequest: 5 status_code=0
D [14/Mar/2006:17:01:38 +0000] ReadClient: 5 POST / HTTP/1.1
D [14/Mar/2006:17:01:38 +0000] ProcessIPPRequest: 5 status_code=1
D [14/Mar/2006:17:01:38 +0000] AcceptClient: 6 from localhost:631.
D [14/Mar/2006:17:01:38 +0000] ReadClient: 6 POST / HTTP/1.1
D [14/Mar/2006:17:01:38 +0000] ProcessIPPRequest: 6 status_code=0
D [14/Mar/2006:17:01:38 +0000] ReadClient: 6 POST / HTTP/1.1
D [14/Mar/2006:17:01:38 +0000] ProcessIPPRequest: 6 status_code=0
D [14/Mar/2006:17:01:38 +0000] ReadClient: 6 POST / HTTP/1.1
D [14/Mar/2006:17:01:38 +0000] ProcessIPPRequest: 6 status_code=1
D [14/Mar/2006:17:01:39 +0000] AcceptClient: 7 from localhost:631.
D [14/Mar/2006:17:01:39 +0000] ReadClient: 7 POST /printers/Stylus-Photo-750 HTTP/1.1
D [14/Mar/2006:17:01:39 +0000] print_job: auto-typing file...
D [14/Mar/2006:17:01:39 +0000] print_job: request file type is application/postscript.
D [14/Mar/2006:17:01:39 +0000] check_quotas: requesting-user-name = 'thomas'
D [14/Mar/2006:17:01:39 +0000] print_job: requesting-user-name = 'thomas'
D [14/Mar/2006:17:01:39 +0000] Adding default job-sheets values "none,none"...
I [14/Mar/2006:17:01:39 +0000] Adding start banner page "none" to job 11.
I [14/Mar/2006:17:01:39 +0000] Adding end banner page "none" to job 11.
I [14/Mar/2006:17:01:39 +0000] Job 11 queued on 'Stylus-Photo-750' by 'thomas'.
D [14/Mar/2006:17:01:39 +0000] Job 11 hold_until = 0
D [14/Mar/2006:17:01:39 +0000] StartJob(11, 0x8096c78)
D [14/Mar/2006:17:01:39 +0000] StartJob() id = 11, file = 0/1
D [14/Mar/2006:17:01:39 +0000] job-sheets=none,none
D [14/Mar/2006:17:01:39 +0000] banner_page = 0
D [14/Mar/2006:17:01:39 +0000] StartJob: argv = "Stylus-Photo-750","11","thomas","Untitled1","1","PageSize=A4","/var/spool/cups/d00011-001"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[0]="PATH=/usr/lib/cups/filter:/bin:/usr/bin"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[2]="USER=root"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[3]="CHARSET=utf-8"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[4]="LANG=en"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[5]="TZ=Europe/London"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[6]="PPD=/etc/cups/ppd/Stylus-Photo-750.ppd"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[7]="CUPS_SERVERROOT=/etc/cups"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[8]="RIP_MAX_CACHE=8m"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[9]="TMPDIR=/var/spool/cups/tmp"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[10]="CONTENT_TYPE=application/postscript"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[11]="DEVICE_URI=hp:/no_device_found"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[12]="PRINTER=Stylus-Photo-750"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[13]="CUPS_DATADIR=/usr/share/cups"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[14]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[15]="CUPS_SERVER=localhost"
D [14/Mar/2006:17:01:39 +0000] StartJob: envp[16]="IPP_PORT=631"
D [14/Mar/2006:17:01:39 +0000] StartJob: statusfds = [ 8 9 ]
D [14/Mar/2006:17:01:39 +0000] StartJob: filterfds[1] = [ 10 -1 ]
D [14/Mar/2006:17:01:39 +0000] StartJob: filter = "/usr/lib/cups/filter/pstops"
D [14/Mar/2006:17:01:39 +0000] StartJob: filterfds[0] = [ 11 12 ]
D [14/Mar/2006:17:01:39 +0000] start_process("/usr/lib/cups/filter/pstops", 0xbf9e3000, 0xbf9e2578, 10, 12, 9)
I [14/Mar/2006:17:01:39 +0000] Started filter /usr/lib/cups/filter/pstops (PID 10683) for job 11.
D [14/Mar/2006:17:01:39 +0000] StartJob: filter = "/usr/lib/cups/filter/foomatic-rip"
D [14/Mar/2006:17:01:39 +0000] StartJob: filterfds[1] = [ 10 13 ]
D [14/Mar/2006:17:01:39 +0000] start_process("/usr/lib/cups/filter/foomatic-rip", 0xbf9e3000, 0xbf9e2578, 11, 13, 9)
I [14/Mar/2006:17:01:39 +0000] Started filter /usr/lib/cups/filter/foomatic-rip (PID 10684) for job 11.
D [14/Mar/2006:17:01:39 +0000] StartJob: backend = "/usr/lib/cups/backend/hp"
D [14/Mar/2006:17:01:39 +0000] StartJob: filterfds[0] = [ -1 11 ]
D [14/Mar/2006:17:01:39 +0000] start_process("/usr/lib/cups/backend/hp", 0xbf9e3000, 0xbf9e2578, 10, 11, 9)
I [14/Mar/2006:17:01:39 +0000] Started backend /usr/lib/cups/backend/hp (PID 10685) for job 11.
D [14/Mar/2006:17:01:39 +0000] ProcessIPPRequest: 7 status_code=0
D [14/Mar/2006:17:01:39 +0000] [Job 11] Page = 595x842; 0,0 to 595,842
D [14/Mar/2006:17:01:39 +0000] [Job 11] slowcollate=0, slowduplex=0, sloworder=0
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%BoundingBox: (atend)
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%Creator: OpenOffice.org 1.9.129
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%For: thomas
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%CreationDate: Tue Mar 14 17:01:39 2006
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%Title: Untitled1
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%LanguageLevel: 3
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%DocumentData: Clean7Bit
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%Pages: (atend)
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%PageOrder: Ascend
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%EndComments
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%BeginProlog
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%BeginResource: procset PSPrint-Prolog 1.0 0
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%EndResource
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%EndProlog
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%BeginSetup
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%EndSetup
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%Page: 1 1
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%Page: 1 1
D [14/Mar/2006:17:01:39 +0000] [Job 11] pw = 595.0, pl = 842.0
D [14/Mar/2006:17:01:39 +0000] [Job 11] PageLeft = 0.0, PageRight = 595.0
D [14/Mar/2006:17:01:39 +0000] [Job 11] PageTop = 842.0, PageBottom = 0.0
D [14/Mar/2006:17:01:39 +0000] [Job 11] PageWidth = 595.0, PageLength = 842.0
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%PageBoundingBox: 0 0 595 842
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%BeginPageSetup
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%BeginFeature: *PageSize A4
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%EndFeature
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%EndPageSetup
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%PageTrailer
D [14/Mar/2006:17:01:39 +0000] [Job 11] 0 %%Trailer
D [14/Mar/2006:17:01:39 +0000] [Job 11] Saw Trailer!
D [14/Mar/2006:17:01:39 +0000] [Job 11] Saw EOF!
D [14/Mar/2006:17:01:39 +0000] [Job 11] perl: warning: Setting locale failed.
D [14/Mar/2006:17:01:39 +0000] [Job 11] perl: warning: Please check that your locale settings:
D [14/Mar/2006:17:01:39 +0000] [Job 11] LANGUAGE = (unset),
D [14/Mar/2006:17:01:39 +0000] [Job 11] LC_ALL = (unset),
D [14/Mar/2006:17:01:39 +0000] [Job 11] LANG = "en"
D [14/Mar/2006:17:01:39 +0000] [Job 11] are supported and installed on your system.
D [14/Mar/2006:17:01:39 +0000] [Job 11] perl: warning: Falling back to the standard locale ("C").
D [14/Mar/2006:17:01:39 +0000] [Job 11] unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84
D [14/Mar/2006:17:01:39 +0000] [Job 11] unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710
D [14/Mar/2006:17:01:39 +0000] [Job 11] unable to send ModelQuery: Broken pipe: prnt/hpijs/hplip_api.c 370
D [14/Mar/2006:17:01:39 +0000] [Job 11] unable to send Event hp:/no_device_found 11 500: Broken pipe
D [14/Mar/2006:17:01:39 +0000] [Job 11] foomatic-rip version $Revision: 3.43.2.11 $ running...
D [14/Mar/2006:17:01:39 +0000] [Job 11] Parsing PPD file ...
D [14/Mar/2006:17:01:39 +0000] [Job 11] *cupsFilter: "application/vnd.cups-postscript 0 foomatic-rip"
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option ColorSpace
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option PageSize
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option PageRegion
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option ImageableArea
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option PaperDimension
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option Resolution
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option Dithering
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option Unidirectional
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option Weaving
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option Encoding
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option stcolor
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option Uniform
D [14/Mar/2006:17:01:39 +0000] [Job 11] Added option Font
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] Parameter Summary
D [14/Mar/2006:17:01:39 +0000] [Job 11] -----------------
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] Spooler: cups
D [14/Mar/2006:17:01:39 +0000] [Job 11] Printer: Stylus-Photo-750
D [14/Mar/2006:17:01:39 +0000] [Job 11] PPD file: /etc/cups/ppd/Stylus-Photo-750.ppd
D [14/Mar/2006:17:01:39 +0000] [Job 11] Printer model: Epson Stylus Photo 750 Foomatic/stcolor (recommended)
D [14/Mar/2006:17:01:39 +0000] [Job 11] Job title: Untitled1
D [14/Mar/2006:17:01:39 +0000] [Job 11] File(s) to be printed:
D [14/Mar/2006:17:01:39 +0000] [Job 11] <STDIN>
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] GhostScript extra search path ('GS_LIB'): /usr/share/cups/fonts
D [14/Mar/2006:17:01:39 +0000] [Job 11] Pondering option 'PageSize=A4'
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] ================================================
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] File: <STDIN>
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] ================================================
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] Reading PostScript input ...
D [14/Mar/2006:17:01:39 +0000] [Job 11] --> This document is DSC-conforming!
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] -----------
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginProlog
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%EndProlog
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] -----------
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginSetup
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *Resolution 360dpi
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Resolution=360dpi --> Setting option
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %% FoomaticRIPOptionSetting: Resolution=360dpi
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Resolution=360dpi --> Setting option
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *Unidirectional False
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Unidirectional=False --> Correcting numerical/string option to Unidirectional=0 (Command line argument)
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *PageSize A4
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: PageSize=A4 --> Option will be set by PostScript interpreter
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *stcolor False
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: stcolor=False --> Correcting numerical/string option to stcolor=0 (Command line argument)
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *Weaving Off
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Weaving=Off --> Setting option
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %% FoomaticRIPOptionSetting: Weaving=Off
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Weaving=Off --> Setting option
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *Dithering ColourFastCMYK
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Dithering=ColourFastCMYK --> Setting option
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %% FoomaticRIPOptionSetting: Dithering=ColourFastCMYK
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Dithering=ColourFastCMYK --> Setting option
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *Uniform False
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Uniform=False --> Correcting numerical/string option to Uniform=0 (Command line argument)
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *Encoding RunLength
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Encoding=RunLength --> Setting option
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %% FoomaticRIPOptionSetting: Encoding=RunLength
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: Encoding=RunLength --> Setting option
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%EndSetup
D [14/Mar/2006:17:01:39 +0000] [Job 11] Inserting PostScript code for CUPS' page accounting
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] -----------
D [14/Mar/2006:17:01:39 +0000] [Job 11] New page:  1 1
D [14/Mar/2006:17:01:39 +0000] [Job 11] Inserting option code into "PageSetup" section.
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginPageSetup
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%BeginFeature: *PageSize A4
D [14/Mar/2006:17:01:39 +0000] [Job 11] Option: PageSize=A4 --> Option will be set by PostScript interpreter
D [14/Mar/2006:17:01:39 +0000] [Job 11] Found: %%EndPageSetup
D [14/Mar/2006:17:01:39 +0000] [Job 11] End of page header
D [14/Mar/2006:17:01:39 +0000] [Job 11] Flushing FIFO.
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] Starting renderer
D [14/Mar/2006:17:01:39 +0000] [Job 11] JCL: <job data>
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] renderer PID kid4=10689
D [14/Mar/2006:17:01:39 +0000] [Job 11] renderer command: gs -q -dBATCH -dPARANOIDSAFER -dQUIET -dNOPAUSE -sDEVICE=stcolor -r360x360 -dnoWeave -sDithering=gscmyk -sOutputCode=runlength -sOutputFile=-  -
D [14/Mar/2006:17:01:39 +0000] [Job 11] perl: warning: Setting locale failed.
D [14/Mar/2006:17:01:39 +0000] [Job 11] perl: warning: Please check that your locale settings:
D [14/Mar/2006:17:01:39 +0000] [Job 11] LANGUAGE = (unset),
D [14/Mar/2006:17:01:39 +0000] [Job 11] LC_ALL = (unset),
D [14/Mar/2006:17:01:39 +0000] [Job 11] LANG = "en"
D [14/Mar/2006:17:01:39 +0000] [Job 11] are supported and installed on your system.
D [14/Mar/2006:17:01:39 +0000] [Job 11] perl: warning: Falling back to the standard locale ("C").
D [14/Mar/2006:17:01:39 +0000] [Job 11] foomatic-gswrapper: gs '-dBATCH' '-dPARANOIDSAFER' '-dQUIET' '-dNOPAUSE' '-sDEVICE=stcolor' '-r360x360' '-dnoWeave' '-sDithering=gscmyk' '-sOutputCode=runlength' '-sOutputFile=/dev/fd/3' '/dev/fd/0' 3>&1 1>&2
D [14/Mar/2006:17:01:39 +0000] [Job 11]
D [14/Mar/2006:17:01:39 +0000] [Job 11] Closing renderer
D [14/Mar/2006:17:01:39 +0000] [Job 11] unable to send Event hp:/no_device_found 11 5012: Broken pipe
D [14/Mar/2006:17:01:40 +0000] [Job 11] tail process done writing data to STDOUT
D [14/Mar/2006:17:01:40 +0000] [Job 11] KID4 finished
D [14/Mar/2006:17:01:40 +0000] [Job 11] KID3 exited with status 0
D [14/Mar/2006:17:01:40 +0000] [Job 11] KID4 exited with status 0
D [14/Mar/2006:17:01:40 +0000] [Job 11] Renderer exit stat: 0
D [14/Mar/2006:17:01:40 +0000] [Job 11] KID3 finished
D [14/Mar/2006:17:01:40 +0000] [Job 11] Renderer process finished
D [14/Mar/2006:17:01:40 +0000] [Job 11]
D [14/Mar/2006:17:01:40 +0000] [Job 11] Closing foomatic-rip.
D [14/Mar/2006:17:01:43 +0000] ReadClient: 5 POST / HTTP/1.1
D [14/Mar/2006:17:01:43 +0000] ProcessIPPRequest: 5 status_code=0
D [14/Mar/2006:17:01:43 +0000] ReadClient: 5 POST / HTTP/1.1
D [14/Mar/2006:17:01:43 +0000] ProcessIPPRequest: 5 status_code=0
D [14/Mar/2006:17:01:43 +0000] ReadClient: 5 POST / HTTP/1.1

```

---

### Post by groggyboy on 2006-03-16
I feel your pain tgoose.  Any luck?  I've got an Epson Stylus C88 that's little more than giant paperweight right now.  CUPS recognizes it (using the C84 driver), but my symptoms are identical to yours.  I find this very unfortunate.  My livelyhood right now depends on my writing skills, and my printer is an important tool.  I'm not about to lay down money for a new printer!  Printing is one of the very few reasons I still have windows.  So if ANYONE can help...

---

### Post by tgoose on 2006-03-18
I've been reinstalling things left right and centre and setting up the printer every way I can think of, and I've still got nothing. On the positive side, at least I haven't broken anything else!

---

