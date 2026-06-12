---
title: "The CUPS server could not be contacted"
date: 2006-06-08
forum: General Help
---

### Post by JackAcid on 2006-06-08
Hello,
Just upgraded my sony Viao laptop to Ubuntu 6.06. Everything else seems to work OK, but when I try to print I get error messages and when I try to select system=> administration => Printers.... the message is "The CUPS server could not be contacted".

Checking the services, shows me printer services (cupsys) is running (i.e. the box is checked). I have tried re-booting, also tried re-starting Print Services. Neither seems to work.

The printer is a HP deskjet 6122 and it worked perfectly in Ubuntu 5.10. 
Serial connection to the printer. The printer may not be an issue yet. need to get the CUPS server working!
Any Ideas???

Thanks!

---

### Post by jazzmuzik on 2006-06-08
can you surf to [http://localhost:631](http://localhost:631) ?

What's the output from this:

sudo /etc/init.d/cupsys restart

If it shows that 'ok' try printing again. If that doesn't work I'd first try deleting the printer driver and creating a new one. If that doesn't work I'd remove the cups package, remove any CUPS config files and resintall it and try again.

---

### Post by JackAcid on 2006-06-09
[QUOTE=jazzmuzik]can you surf to [http://localhost:631](http://localhost:631) ?

What's the output from this:

sudo /etc/init.d/cupsys restart

If it shows that 'ok' try printing again. If that doesn't work I'd first try deleting the printer driver and creating a new one. If that doesn't work I'd remove the cups package, remove any CUPS config files and resintall it and try again.[/QUOTE]


I tried restarting from the command line and got the [ok] but the message still says "the CUPS server......"
tried from the web browser, but can't get to the admin page. like it can't find that particular url. the other buttons load a page that simply says {error}, cant get to the page to manage the server either.

Looking at Synaptic, I have lots of cups related packages loaded. do you think I need to uninstall ALL of them?

---

### Post by jazzmuzik on 2006-06-09
I don't really know if you need to install all or some. I was just saying what I would do in a similar situation. Actually, I would first exhaust every bit of help you can find first. I would search on Google web and then Google Groups until I'd find an answer.

---

### Post by GoldBuggie on 2006-06-09
on server
```
sudo /usr/share/cups/enable_browsing 1
sudo /usr/share/cups/enable_sharing 1
```

on client
```
sudo /usr/share/cups/enable_browsing 1
```

---

### Post by grendelkhan on 2006-06-09
This is a local printer, right?

---

### Post by JackAcid on 2006-06-12
[QUOTE=grendelkhan]This is a local printer, right?[/QUOTE]
Yes , it is a local printer. 
I just noticed that the hardware browser does not find the printer when I have it connected to the parralel port, but it finds it when I have it plugged in to the USB.
The whole mess just worked in breezy, aaaarrrrrgh!

I tried the enable-browsing command and still get the original error. There is another thread in this forum I have been trying to follow as well. 

Thanks for the help so far!

---

### Post by grendelkhan on 2006-06-12
Is this a multifunction printer?  I have issues with permissions on my multifunction epson.

---

### Post by JackAcid on 2006-06-12
Not sure if duplexing counts as multifunction, but really it's just a printer. No scan/fax or anything else.

BTW, any Idea what this means?
mike@ubuntu:~$ sudo dpkg --list 'hplip*'
Password:
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  hplip          0.9.7-4ubuntu1 HP Linux Printing and Imaging System (HPLIP)
rc  hplip-base     0.9.5-2ubuntu2 HP Linux Printing and Imaging System - base
ii  hplip-data     0.9.7-4ubuntu1 HP Linux Printing and Imaging - data files
ii  hplip-ppds     0.9.7-4ubuntu1 HP Linux Printing and Imaging - PPD files

---

### Post by JackAcid on 2006-06-12
Well, I finally got tired of anylizing the situation and did what Jazzmuzik originally suggested.
That is I completely uninstalled cups using synaptics, which got rid of the config files and hplips. and then did a re-install and badda-bing badda-boom...
the printer is found and is working. Wonder if it was a glitch in the install/upgrade?

I don't know!
 Anyway Thanks everybody for your thoughts and hints and all!
Looks like I'm back in the printing mode! WooHooo!

---

