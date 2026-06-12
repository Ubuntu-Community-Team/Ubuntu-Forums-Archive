---
title: "Printer driver package cannot be reinstalled. Synapse blocked"
date: 2011-02-11
forum: General Help
---

### Post by kimbatour on 2011-02-11
Hi, 
I want to explain how this problem has happened.
I am new with Ubuntu and the problem is when I try to select a device in printing options (Open office) only the GENERIC PRINTER appears.
Then I tried to reinstall the printer driver and downloaded it from **[here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-9070")**


When opened Ubuntu software center the driver was displayed as installed and I clicked Reinstall.
Then my problems have started.
Firstly I've got the error 
[FONT=Courier New][SIZE=2][COLOR=Black]E: I wasn't able to locate file for the mfc9070lpr package. This might mean you need to manually fix this package.[/COLOR][/SIZE][/FONT]

The my update manager started showing blocked icon saying:
[FONT=Arial Black]It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.[/FONT]

I tried the command but I get this:
[FONT=Courier New][SIZE=2][COLOR=Black]E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/COLOR][/SIZE][/FONT]

I have followed the instructions from **[this thread]("http://ubuntuforums.org/showthread.php?t=455541")**
and when I ran the 3 commands:
sudo aptitude clean sudo aptitude update sudo aptitude upgrade
on the last i've got:

[FONT=Courier New][SIZE=2]270 packages upgraded, 5 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 203MB will be used.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the mfc9070lpr package. This might mean you need to manually fix this package.
E: I wasn't able to locate file for the mfc9070lpr package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download[/SIZE][/FONT]

The error that concerns me the most is:
[FONT=Arial Black]Software index is broken...[/FONT]
Please HELP!

---

### Post by kimbatour on 2011-02-14
I haven't solved my problem, please help!

Thanks!

---

### Post by jerrrys on 2011-02-14
two things i do:

#1 use 'synaptic package manager' like it suggest and 
#2 try a different download site

---

