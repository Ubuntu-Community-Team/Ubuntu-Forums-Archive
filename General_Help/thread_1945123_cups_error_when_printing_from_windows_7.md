---
title: "cups error when printing from windows 7"
date: 2012-03-22
forum: General Help
---

### Post by r.stiltskin on 2012-03-22
I installed my brother printer (connected to my Ubuntu 10.04 LTS desktop) on a new HP/Windows 7 Home Premium laptop.  Installed it as a network printer with the same configuration as I've used on Windows XP and Windows 2000 machines.  It was "successfully installed", but can't print a test page.

Immediately after trying to print I found this message in my cups access_log:

<the laptop's lan address> - - [22/Mar/2012:12:58:27 -0400] "POST /printers/HL-5150D-series HTTP/1.1" 200 75 windows-ext client-error-bad-request

and I found these messages in my cups error_log:

E [22/Mar/2012:12:58:27 -0400] Missing printer-uri, job-uri, or ppd-name attribute!
E [22/Mar/2012:12:58:27 -0400] Returning IPP client-error-bad-request for windows-ext (no URI) from <the laptop's lan address>

I have checked that printer name a dozen times -- as far as I can see it is exactly correct, same hyphenation, same uppercase/lowercase characters, no spaces, and so on.

What can be causing these errors?


Here is the corresponding message in the access_log after printing from another laptop (running Windows XP):
<WinXP laptop lan address> - - [22/Mar/2012:14:39:54 -0400] "POST /printers/HL-5150D-series HTTP/1.1" 200 177847 Print-Job successful-ok


I also tried to print from the Win2K machine and couldn't -- somehow the properties page for that one was messed up and it had *no port at all* checked for this printer.  That produced cups  messages EXACTLY THE SAME (except for the lan address) as the error messages produced when printing from Windows 7:
<Win2K lan address> - - [22/Mar/2012:14:52:27 -0400] "POST /printers/HL-5150D-series HTTP/1.1" 200 75 windows-ext client-error-bad-request
E [22/Mar/2012:14:52:27 -0400] Missing printer-uri, job-uri, or ppd-name attribute!
E [22/Mar/2012:14:52:27 -0400] Returning IPP client-error-bad-request for windows-ext (no URI) from <Win2K lan address>

But I reinstalled the printer in the Win2K machine and now it too can print normally and  the access log now shows:
<Win2K lan address> - - [22/Mar/2012:14:53:35 -0400] "POST /printers/HL-5150D-series HTTP/1.1" 200 158521 Print-Job successful-ok

---

### Post by ottosykora on 2012-03-22
well on w7, a printer connected to other computer is not understood as network printer but it is local printer.

Try to install it as local printer and then enter the path to it and it should work.

---

### Post by Mark Phelps on 2012-03-22
Is this a Windows 7 question? Or a Linux CUPS question?

If it's strictly a problem with Win7, you should post the problem to a Win7 forum: sevenforums.com.

---

### Post by r.stiltskin on 2012-03-22
To be honest, Mark, I'm not sure.  For a while, when I saw what seem to be ambiguous or contradictory cups error messages I thought it might be a cups problem.  Now I think, probably not.

But here are two explicitly cups questions:

Can you suggest a way to capture the exact, full contents of the requests that are being received by cups, to aid in diagnosis?

Also, referring to the "Missing printer-uri, job-uri, or ppd-name attribute!" messages, do you know of any resource that would be helpful in deciphering exactly what cups is complaining about?

and @ottosykora: it doesn't work when designated as a local printer either.

---

### Post by imachavel on 2012-03-22
[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html)

this **** look SO complicated. I wish I had configured this once before, because I don't want to experiment with all this now for the first time. Do me a favor and pm me. I want to get on xchat and try some troubleshooting configuring windows 7 to use a cups printer. But did the admins say you installed the printer as a host based printer and not a network based printer? Amazing, that won't work. Also I can't parallel the method I would explain for you to use, especially since windows 7 doesn't have supported drivers for my printer in any way shape or form, but it'd be nice because if we both used the same method, it'd be easy to come back to this thread and post a fix to solve the problem. Pm me if you wish maybe we can work something out. Btw have you looked at this page?

[https://help.ubuntu.com/8.04/serverguide/C/cups.html](https://help.ubuntu.com/8.04/serverguide/C/cups.html)

now if you want to set up the printer on windows 7 as a network based printer I believe you simply need to install printer drivers that are network based printer drivers from the printer manufacturers web site, then I'm not sure how to configure it with a network i.p. address, assign a port in the router, ping the port, etc. Windows obviously doesn't use cups it uses another spooler service

---

### Post by r.stiltskin on 2012-03-22
I think I can say at this point that it's not a cups problem at all, but a Windows 7 problem.  The error messages that I described earlier occur while the Win 7 printer installation wizard is running.  I tried doing some wireshark captures, but as far as I can see, after "installation", when I try to print from the Win7 machine it doesn't generate any network activity at all.

---

### Post by sammiev on 2012-03-22
[This]("http://ubuntuforums.org/showthread.php?t=1676121") may help you.

---

### Post by r.stiltskin on 2012-03-22
Thanks sammiev, but there's nothing new there.  I've already been configuring the port in Win7 as <server lan address>:631/printers/HL-5150D-series, exactly the same as the ones in my WinXP and Win2K machines (which work).  But Windows 7 just isn't communicating with that port.

I can enter that address in a browser on the Windows 7 machine and that opens up the Brother printer in the browser, but of course that does me no good in terms of printing.

This is a pre-installed HP version of Windows 7, so HP must have done something odd in some obscure corner of Windows settings that's mucking things up.

---

### Post by r.stiltskin on 2012-03-23
Apologies to anyone who objects to discussing a "Windows problem" here, but I feel that enough of us want to make our printers available to Windows clients to consider this a Linux problem too.

There are a number of threads about this problem on various forums which contain a lot of misinformation.  In most of them, people are explaining how to install the CUPS printer as a network printer using procedures that worked for older versions of Windows but don't work for Windows 7 (at least not *my* Windows 7).  In some, people talk about installing the printer in Windows 7 as a local, not a network, printer; that one works for standalone network printers but not printers managed by CUPS attached to a Linux server.  And a couple of them talk about adding a  "PreferredConnection" entry in the Windows registry under HKEY_CURRENT_USER\Printers\Settings.  These solutions *may have* worked for some people (I'm not convinced) but they don't work for the version of Windows 7 that HP preinstalled in my laptop.  HP, or MS, seem to have completely disabled IPP in this version of Windows.

The solution I ended up with (which in retrospect should have been obvious) was to create a Samba share of the printer: Samba makes the printer available to Windows, Samba sends the print job to CUPS, voila!  All I needed were a few minor changes to /etc/samba/smb.conf.  It already had
```
  printing = cups
  printcap = cups
``` in the [global] section, so CUPS support was already there.
I didn't want to share all printers this way, so I set (also in [global])
```
  load printers = no
```

And then I added this to create the share for the laser printer, making it available to anyone who can access my lan (HL-5150D-series is just the name of the printer as I installed it in CUPS)
```

[HL-5150D-series]
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   use client driver = yes
   create mask = 0700
```

---

### Post by davidvandoren on 2012-03-23
did you use this driver on the windows 7 side?
select a Manufacturer of "Generic" and the Printer "MS Publisher Imagesetter"

it should work.

you have to open port 631 on windows 7 also 
it's a bit complicated as Iremember

---

### Post by r.stiltskin on 2012-03-23
It was not a driver problem.


... or a port problem.  I was addressing the printer as
<server lan address>:631/printers/<name of printer>
from the very beginning (which works in older versions of Windows).  But Windows 7 was unable or unwilling to configure it that way.  It kept reverting to port 9100 or something like that.

---

### Post by davidvandoren on 2012-03-23
did you open the windows 7 firewall configuration?
If not, do so and open the port 631.
I had to do that for my wife's pc in order to make it work.
Bu don't ask me how I watched a youtube video myself to do that.

Windows:confused:

---

### Post by r.stiltskin on 2012-03-23
Actually, I turned off the firewall completely to be sure that it wastn't getting in the way.

---

### Post by davidvandoren on 2012-03-23
try setting up the printer again from scratch.

Instead installing the driver from the cd, do the following;
when asked to provide the driver select a Manufacturer of "Generic" and the Printer "MS Publisher Imagesetter"

this has always worked for me so far no matter what printer model.

you can also try to connect the printer via the internet ip but only if you have a static ip.

or try sharing via samba,

---

### Post by r.stiltskin on 2012-03-23
Sorry, I know your intentions are good, but haven't you read the previous posts?

The problem has nothing to do with the driver -- Windows was not sending *anything* over the network.  (And actually I installed the Microsoft driver provided by Windows Update, not Brother's old driver which is not Win7 compatible.)

And yes the server's lan address is static, but while Windows let me enter that lan address and port 631 in the Add Printer Wizard, it didn't actually configure the port that way.

And please note that the thread is [solved] and the solution, described in post #9, was to use SAMBA to share the printer.

---

### Post by r.stiltskin on 2012-04-05
Update on this problem:

SAMBA turned out to be a terrible solution, and I have since disabled that printer share.

I discovered that whenever the laptop was on and running Windows 7 (Home Premium), there was a constant stream of network traffic on the order of 300Kbps between the Windows 7 laptop and the Ubuntu 10.05 server, hogging so much bandwidth that other computers in the house had trouble loading webpages.  I found this in the Windows 7 Resource Monitor under Network Activity which referred to it as "System" with PID 4.  I don't have any more details about this, but I did verify that as soon as I deleted the printer (in control panel) the activity stopped, and each time I reinstalled the printer, the activity restarted.

I also monitored this activity in Wireshark -- I can't explain exactly what the packets represented, but they were clearly between the laptop and the server, and they were clearly printer-related (although there were no documents in any print queue).

So -- Samba is not the answer.

Happily, a few hours later I found the "right" solution -- how to get IPP working on the Windows 7 laptop. 

Solution is posted here:

[http://www.sevenforums.com/network-sharing/220645-printer-linux-cups-server-cant-print-windows-7-a.html#post1869694]("http://www.sevenforums.com/network-sharing/220645-printer-linux-cups-server-cant-print-windows-7-a.html#post1869694")

---

