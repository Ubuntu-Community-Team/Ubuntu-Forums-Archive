---
title: "Can print test page, not documents"
date: 2010-05-06
forum: General Help
---

### Post by Angus77 on 2010-05-06
I know my driver works and that cups is up and running, because I can print off test pages to my heart's content, but I can't get any actual documents printed.

I'm connected over the network at work to a Japanese NEC MultiWriter 3650n (it seems to be Japanese-only---the only help I could find on drivers was in Japanese).  It shows up in System=>Administration=>Printing.  I set it as the default printer, and, as I said, it prints off test pages without a hitch.  But whenever I open, say, a PDF and try to print it, the document appears to get sent, but never actually prints, and never shows up in the print queue (while the completed test pages do).

Can anyone give me a hand?

---

### Post by anglican on 2010-05-06
> **Angus77 said:**
> I know my driver works and that cups is up and running, because I can print off test pages to my heart's content, but I can't get any actual documents printed.

I'm connected over the network at work to a Japanese NEC MultiWriter 3650n (it seems to be Japanese-only---the only help I could find on drivers was in Japanese).  It shows up in System=>Administration=>Printing.  I set it as the default printer, and, as I said, it prints off test pages without a hitch.  But whenever I open, say, a PDF and try to print it, the document appears to get sent, but never actually prints, and never shows up in the print queue (while the completed test pages do).

Can anyone give me a hand?

Is there anything useful in the logfile (/var/log/cups/error_log)?

H

---

### Post by Angus77 on 2010-05-06
I tried to print a PDF this morning, and this is what I got in /var/log/cups/error_log:

```
E [07/May/2010:08:23:03 +0900] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [07/May/2010:08:24:51 +0900] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/MultiWriter-) from localhost
```

Of course, printing PDFs from the Windows box in the office doesn't pose such "format-not-supported" problems.

---

### Post by anglican on 2010-05-07
> **Angus77 said:**
> I tried to print a PDF this morning, and this is what I got in /var/log/cups/error_log:

```
E [07/May/2010:08:23:03 +0900] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [07/May/2010:08:24:51 +0900] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/MultiWriter-) from localhost
```Of course, printing PDFs from the Windows box in the office doesn't pose such "format-not-supported" problems.

Is the line 

application/octet-stream

at the end of the file /etc/cups/mime.types commented out? If so, remove the comment (the '#' at the beginning), restart cups and see if that helps. Also the similar line in /etc/cups/mime.convs (they're both right at the end of the file). BTW you may find comments like "Windows box... doesn't pose such... problems" reduces your chance of getting help here. It **can** get peoples backs up. :wink:

H

---

### Post by Angus77 on 2010-05-07
Sorry, the only thing I meant about the "Windows box" comment was that the printer does, in fact, support the format.  At home I haven't owned a box running Windows since I switched to Feisty (I even make my wife & kids use Ubuntu;) ). 

Neither /etc/cups/mime.types nor /etc/cups/mime.convs seem to exist.  I don't know if /etc/mime.types is the same thing, but the line application/octet-stream in it is not commented out.  Is this a change in Lucid, maybe, or is it a real problem?

---

### Post by anglican on 2010-05-10
> **Angus77 said:**
> Sorry, the only thing I meant about the "Windows box" comment was that the printer does, in fact, support the format.  At home I haven't owned a box running Windows since I switched to Feisty (I even make my wife & kids use Ubuntu;) ). 

Neither /etc/cups/mime.types nor /etc/cups/mime.convs seem to exist.  I don't know if /etc/mime.types is the same thing, but the line application/octet-stream in it is not commented out.  Is this a change in Lucid, maybe, or is it a real problem?
No, /etc/mime.types is not to do with cups printing. Try creating files /etc/cups/local.types:

```
# Raw filter...
#
# Uncomment the following filter to allow printing of arbitrary files
# without the -oraw option.
#

application/octet-stream        application/vnd.cups-raw        0       -
```and /etc/cups/local.convs:

```
#
# Raw print file support...
#
# Comment the following type to prevent raw file printing.
#

application/octet-stream
```H

---

### Post by Angus77 on 2010-05-11
I don't know what has changed, but I can no longer print test pages (this was before adding the two files you recommended).  I get a report that the printer is low on toner, but that doesn't appear to be the case (everyone else is printing fine, and the printer itself is not giving a low-on-toner warning).

Here's what I now get in /var/log/cups/error_log :

```
E [12/May/2010:08:51:49 +0900] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [12/May/2010:08:52:24 +0900] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/MultiWriter-) from localhost
E [12/May/2010:08:55:12 +0900] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [12/May/2010:08:55:22 +0900] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [12/May/2010:08:56:07 +0900] PID 3531 (/usr/lib/cups/filter/necfilter) crashed on signal 13!
D [12/May/2010:08:56:07 +0900] [Job 21] The following messages were recorded from 08:56:06 AM to 08:56:07 AM
D [12/May/2010:08:56:07 +0900] [Job 21] Adding start banner page "none".
D [12/May/2010:08:56:07 +0900] [Job 21] Adding end banner page "none".
D [12/May/2010:08:56:07 +0900] [Job 21] File of type application/postscript queued by "angus".
D [12/May/2010:08:56:07 +0900] [Job 21] hold_until=0
D [12/May/2010:08:56:07 +0900] [Job 21] Queued on "MultiWriter-" by "angus".
D [12/May/2010:08:56:07 +0900] [Job 21] job-sheets=none,none
D [12/May/2010:08:56:07 +0900] [Job 21] argv[0]="MultiWriter-"
D [12/May/2010:08:56:07 +0900] [Job 21] argv[1]="21"
D [12/May/2010:08:56:07 +0900] [Job 21] argv[2]="angus"
D [12/May/2010:08:56:07 +0900] [Job 21] argv[3]="Test Page"
D [12/May/2010:08:56:07 +0900] [Job 21] argv[4]="1"
D [12/May/2010:08:56:07 +0900] [Job 21] argv[5]="PageSize=A4 job-uuid=urn:uuid:f668d233-71fe-3e90-5dce-83fa9e5f861e job-originating-host-name=localhost"
D [12/May/2010:08:56:07 +0900] [Job 21] argv[6]="/var/spool/cups/d00021-001"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[8]="HOME=/var/spool/cups/tmp"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[10]="SERVER_ADMIN=root@mother-mary"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[11]="SOFTWARE=CUPS/1.4.3"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[13]="TZ=Asia/Tokyo"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[14]="USER=root"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[15]="CUPS_SERVER=/var/run/cups/cups.sock"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[16]="CUPS_ENCRYPTION=IfRequested"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[17]="IPP_PORT=631"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[18]="CHARSET=utf-8"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[19]="LANG=en_CA.UTF-8"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[20]="PPD=/etc/cups/ppd/MultiWriter-.ppd"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[21]="RIP_MAX_CACHE=254498k"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[22]="CONTENT_TYPE=application/postscript"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[23]="DEVICE_URI=socket://172.16.22.104:9100"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[24]="PRINTER_INFO=MultiWriter"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[25]="PRINTER_LOCATION=172.16.22.104"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[26]="PRINTER=MultiWriter-"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[27]="CUPS_FILETYPE=document"
D [12/May/2010:08:56:07 +0900] [Job 21] envp[28]="FINAL_CONTENT_TYPE=printer/MultiWriter-"
D [12/May/2010:08:56:07 +0900] [Job 21] Started filter /usr/lib/cups/filter/necfilter (PID 3531)
D [12/May/2010:08:56:07 +0900] [Job 21] Started backend /usr/lib/cups/backend/socket (PID 3532)
D [12/May/2010:08:56:07 +0900] [Job 21] /usr/lib/cups/backend/socket: Permission denied
D [12/May/2010:08:56:07 +0900] [Job 21] Backend returned status 22 (unknown)
D [12/May/2010:08:56:07 +0900] [Job 21] End of messages
D [12/May/2010:08:56:07 +0900] [Job 21] printer-state=3(idle)
D [12/May/2010:08:56:07 +0900] [Job 21] printer-state-message="/usr/lib/cups/backend/socket failed"
D [12/May/2010:08:56:07 +0900] [Job 21] printer-state-reasons=toner-low-report

```

And, strange as it seems, as I was typing this up, I got a popup message to the effect that my job had been printed.  There was nothing in the printer, though.

---

### Post by anglican on 2010-05-12
> **Angus77 said:**
> I don't know what has changed, but I can no longer print test pages (this was before adding the two files you recommended).  I get a report that the printer is low on toner, but that doesn't appear to be the case (everyone else is printing fine, and the printer itself is not giving a low-on-toner warning).

snip

And, strange as it seems, as I was typing this up, I got a popup message to the effect that my job had been printed.  There was nothing in the printer, though.

Looks like backends not properly installed. Try:

```
sudo dpkg-reconfigure cupsys

```and

```
sudo dpkg-reconfigure cups
```

H

---

### Post by Angus77 on 2010-05-14
I'll have to try this Monday.

Thanks for all the help!

---

### Post by Angus77 on 2010-05-17
It doesn't seem to have changed anything.  The output of /var/log/cups/error_log seems to spit out the same information.

---

### Post by anglican on 2010-05-18
> **Angus77 said:**
> It doesn't seem to have changed anything.  The output of /var/log/cups/error_log seems to spit out the same information.
What (if anything) is in /usr/lib/cups/backend - i.e. what do you see from "ls -l /usr/lib/cups/backend"? Having re-configured cups it might be worth trying to remove and then re-install the printer.

H

---

### Post by Angus77 on 2010-05-18
I've removed and reinstalled the printer.

In /usr/lib/cups/backend:

```
total 424
-rwxr-xr-x 1 root root  7250 2010-02-16 02:02 beh
-rwxr-xr-x 1 root root 38896 2010-04-09 19:35 bluetooth
-rwx------ 1 root root 22036 2009-12-01 04:58 cups-pdf
-rwxr--r-- 2 root root 17636 2010-04-10 00:13 dnssd
-rwxr-xr-x 1 root root 17956 2010-04-12 19:48 hp
-rwxr-xr-x 1 root root  8393 2010-04-12 19:47 hpfax
-rwxr--r-- 3 root root 43328 2010-04-10 00:13 http
-rwxr--r-- 3 root root 43328 2010-04-10 00:13 ipp
-rwxr--r-- 2 root root 39228 2010-04-10 00:13 lpd
-r-xr-xr-x 2 root root 29988 2010-04-10 00:13 parallel
-r-xr-xr-x 2 root root  9444 2010-04-10 00:13 scsi
-r-xr--r-- 2 root root 29988 2010-04-10 00:13 serial
lrwxrwxrwx 1 root root    21 2010-04-30 08:54 smb -> ../../../bin/smbspool
-r-xr-xr-x 2 root root 21736 2010-04-10 00:13 snmp
-r-xr-xr-x 2 root root 29988 2010-04-10 00:13 socket
-r-xr--r-- 2 root root 38180 2010-04-10 00:13 usb
```

I had to use sudo to view it---is that normal?

I'm now able to print test pages again, but get rejected when I try to print a PDF.  This is my /var/log/cups/error_log:

```
E [19/May/2010:09:58:26 +0900] Returning IPP client-error-document-format-not-supported for Send-Document (ipp://localhost:631/printers/MultiWriter-) from localhost
E [19/May/2010:09:59:50 +0900] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [19/May/2010:10:04:27 +0900] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [19/May/2010:10:04:27 +0900] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/May/2010:10:07:13 +0900] [cups-deviced] PID 2015 (parallel) stopped with status 13!
E [19/May/2010:10:07:13 +0900] [cups-deviced] PID 2016 (smb) stopped with status 13!
E [19/May/2010:10:07:13 +0900] [cups-deviced] PID 2017 (socket) stopped with status 13!
E [19/May/2010:10:07:13 +0900] [cups-deviced] PID 2018 (scsi) stopped with status 13!
E [19/May/2010:10:07:13 +0900] [cups-deviced] PID 2013 (hp) stopped with status 13!
E [19/May/2010:10:07:13 +0900] [cups-deviced] PID 2019 (beh) stopped with status 13!
E [19/May/2010:10:07:13 +0900] [cups-deviced] PID 2025 (hpfax) stopped with status 13!
E [19/May/2010:10:07:14 +0900] [cups-deviced] PID 2029 (snmp) stopped with status 13!
E [19/May/2010:10:07:14 +0900] [cups-deviced] PID 2027 (bluetooth) stopped with status 13!
E [19/May/2010:10:09:49 +0900] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [19/May/2010:10:18:31 +0900] [Job 28] Unable to send trailing nul to printer: Broken pipe
E [19/May/2010:10:18:31 +0900] [Job 28] Remote host did not accept data file (32)
E [19/May/2010:10:31:12 +0900] Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/MultiWriter-) from localhost
```

Job 28 didn't go through because there was a problem with the printer that someone came in and fixed.  Other than that I've been able to send test pages to my heart's content.

---

### Post by Angus77 on 2010-05-18
It turns out I could print off a .doc file.

Unfortunately, all the files I _want_ to print are PDFs.

---

### Post by Bucky Ball on 2010-11-08
I know this is a bit old, but ever have any luck with it? My wife's computer has had the same problem for a few months and I just bought a new laptop and sure enough; PDFs do print but take forever (same as my wife's machine).

What is this bug?

---

### Post by HermanAB on 2010-11-08
Howdy,

You can send a PDF file straight to the printer:
[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

$ lpr -H 192.168.1.10 test.pdf

---

### Post by Bucky Ball on 2010-11-08
> **HermanAB said:**
> Howdy,

You can send a PDF file straight to the printer:
[http://www.aeronetworks.ca/howtos/print-howto.html](http://www.aeronetworks.ca/howtos/print-howto.html)

$ lpr -H 192.168.1.10 test.pdf

Cheers, but I'd much rather just click print.

---

### Post by CrusaderAD on 2012-08-17
I know this is an old thread, but any ideas? Why would you be able to print a test page, or from the command line, but not from the print dialog box in applications?

---

### Post by oldos2er on 2012-08-17
Please start a new thread for your question. Old thread closed.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

