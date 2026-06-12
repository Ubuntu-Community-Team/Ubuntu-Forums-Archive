---
title: "Cannot Access Network"
date: 2010-07-25
forum: General Help
---

### Post by Joseph Schwenker on 2010-07-25
I have been able to access computers on the network before, but recently, I have not been able to.  When I start a new session and try to access the network, I get Ubuntu's spinning white circle of doom (for lack of a better name).  After a while, an error messages displays saying

> Could not display "network:///".

Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

I am then able to open Network.  However, even though the computer I have accessed before is on, it does not appear.  I have also printed to this computer's printer before, but when I tried printing something, nothing happened.  
There are three computers and two printers on the network:

JOSEPH (my own; only public is accessible)
CINDY-PC (the only computer I have been able to access before)
MIKE-SCHWENKERS		__s Power Mac G4 (my dad's Macintosh; I have never accessed it before)
HP Deskjet F4480 (printer hooked up to CINDY-PC
HP Photosmart C4100 series (my own printer)

Only "joseph's public files on joseph" and "Windows Network" (which does nothing) show up in network.  I ran smbtree and got this output:

```
joseph@joseph:~$ smbtree
Enter joseph's password: 
WORKGROUP
	\\MIKE-SCHWENKERS		__s Power Mac G4
cli_start_connection: failed to connect to MIKE-SCHWENKERS<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\JOSEPH         		joseph server (Samba, Ubuntu)
		\\JOSEPH\public         	
		\\JOSEPH\HP-Deskjet-F4480	HP Deskjet F4480
		\\JOSEPH\Photosmart-C4100-series	HP Photosmart C4100 series
		\\JOSEPH\print$         	Printer Drivers
		\\JOSEPH\IPC$           	IPC Service (joseph server (Samba, Ubuntu))
	\\CINDY-PC       		
cli_start_connection: failed to connect to CINDY-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
joseph@joseph:~$
```

I need to be able to connect to CINDY-PC; I have done so before by double-clicking on its icon in Network, then entering the username and password of the administrator on that computer.  Mike's computer has never shown up in network, but I would like to be able to access it.  I already tried reinstalling Samba and restarting Nautilus, but that didn't help.  Can someone help me?  I am using Ubuntu 10.04 32-bit.

---

### Post by fbobraga on 2010-07-25
It seems strange, but after installing the ***ntfs-config*** package here, a issue like yours stoped...

---

### Post by Joseph Schwenker on 2010-07-25
You are the best person EVAR.  Kudos to you.  Thanks for the quick reply!  I installed the package, then noticed that, even after refreshing Network, nothing other than joseph's public files on joseph and Windows Network were visible.  I ran smbtree again, and the output was much faster, and with no errors.  Confused, I restarted Nautilus, and the two standard items were still the only ones in Network.  Out of desperation, I double-clicked on Windows Network, and was surprised that it opened.  There was a folder inside of it called "WORKGROUP".  I opened it, and noticed that not only CINDY-PC, but also MIKE-SCHWENKERS and JOSEPH were present.  This is great!  I was able to mount CINDY-PC and JOSEPH, but MIKE-SCHWENKERS appeared to be empty.  This is great, though.  Thanks for fixing this!  Now I can backup my data!

---

### Post by Joseph Schwenker on 2010-08-03
I have been unable to backup my data, as I keep getting an error that makes it seem like the computer is offline, though the computer is still turned on.  Today, when I tried to access CINDY-PC, I was unable to do so.  I accessed Network and Windows Network, though they were much slower than usual.  When I tried to access WORKGROUP, I got an error saying "Failed to retrieve share list from server."  The computer was turned on, so I ran smbtree.

```
joseph@joseph:~$ smbtree
Enter joseph's password: 
WORKGROUP
	\\JOSEPH         		joseph server (Samba, Ubuntu)
		\\JOSEPH\public         	
		\\JOSEPH\IPC$           	IPC Service (joseph server (Samba, Ubuntu))
		\\JOSEPH\print$         	Printer Drivers
	\\CINDY-PC       		
cli_start_connection: failed to connect to CINDY-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
joseph@joseph:~$ samba
The program 'samba' is currently not installed.  You can install it by typing:
sudo apt-get install samba4
joseph@joseph:~$ smbtree
Enter joseph's password: 
WORKGROUP
	\\JOSEPH         		joseph server (Samba, Ubuntu)
		\\JOSEPH\public         	
		\\JOSEPH\IPC$           	IPC Service (joseph server (Samba, Ubuntu))
		\\JOSEPH\print$         	Printer Drivers
	\\CINDY-PC       		
cli_start_connection: failed to connect to CINDY-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

```

I have been unable to entirely backup my data, as the connection stops in the middle of my backup.  Now, I can't even access CINDY-PC.

---

### Post by Joseph Schwenker on 2010-08-04
bump

---

### Post by Joseph Schwenker on 2010-08-06
bump

I purged ntfs-config, then reinstalled it.  I also installed smbfs.  Nothing works.  After I installed smbfs, MIKE-SCHWENKERS appeared, but I still got NT_STATUS_UNSUCCESSFUL.  Here is the output.

```
joseph@joseph:~$ smbtree
Enter joseph's password: 
WORKGROUP
	\\MIKE-SCHWENKERS		__s Power Mac G4
cli_start_connection: failed to connect to MIKE-SCHWENKERS<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL
	\\JOSEPH         		joseph server (Samba, Ubuntu)
		\\JOSEPH\public         	
		\\JOSEPH\IPC$           	IPC Service (joseph server (Samba, Ubuntu))
		\\JOSEPH\print$         	Printer Drivers
	\\CINDY-PC       		
cli_start_connection: failed to connect to CINDY-PC<20> (0.0.0.0). Error NT_STATUS_UNSUCCESSFUL

```

I found the address of CINDY-PC: smb://WORKGROUP/CINDY-PC/.

---

### Post by Joseph Schwenker on 2010-08-10
I tried to access the router a few days ago, but got an error.  I tried the same thing on another computer in the house and got the same result.  I reset the router, and am now able to access it to forward some ports.  I thought that this would enable me to access the network again, but it did not.  I purged ntfs-config, then ran smbtree, and now, no computers but my own appeared AT ALL.  I reinstalled it, and now CINDY-PC appears, but gives me the finger by saying NT_STATUS_UNSUCCESSFUL.

---

### Post by Joseph Schwenker on 2010-08-11
bump

---

### Post by Joseph Schwenker on 2010-08-13
bump
I REALLY need this fixed.

---

### Post by Joseph Schwenker on 2010-08-22
I'd really like to back up my data...

---

### Post by Joseph Schwenker on 2010-08-31
I just tried this from an Ubuntu 10.04.1 live CD and from my dad's Macintosh.  smbtree on his Mac says that my mom's computer exist, and can even connect to it.  smbtree on the live CD gives the same output as my 10.04 installation, NT_STATUS_UNSUCCESSFUL.  Recently, my router has been randomly disappearing.  When I type in 192.168.1.1, I sometimes get an error, and have to reset the router to access its settings.  Are there some settings I'm missing on the Windows 7 machine?  I was able to back up to it before...

---

### Post by Joseph Schwenker on 2010-08-31
I followed part two of [these instructions]("http://ubuntuforums.org/showthread.php?t=1169149"), and I think that I may be on the right track.

smbtree now outputs:

```
joseph@joseph:~$ smbtree
Enter joseph's password: 
WORKGROUP
	\\POWER-MAC-G4   		Power Mac G4
		\\POWER-MAC-G4\Stylus Photo 1400	EPSON SP 1400 Series (1)
		\\POWER-MAC-G4\iP2600 series  	Canon iP2600 series
		\\POWER-MAC-G4\ADMIN$         	IPC Service (Power Mac G4)
		\\POWER-MAC-G4\IPC$           	IPC Service (Power Mac G4)
	\\JOSEPH         		joseph server (Samba, Ubuntu)
		\\JOSEPH\public         	
		\\JOSEPH\HP-Deskjet-F4480	HP Deskjet F4480
		\\JOSEPH\Photosmart-C4100-series	HP Photosmart C4100 series
		\\JOSEPH\IPC$           	IPC Service (joseph server (Samba, Ubuntu))
		\\JOSEPH\print$         	Printer Drivers
	\\CINDY-PC       		
joseph@joseph:~$ 

```

However, browsing Network in Nautilus still gives me errors.  Maybe a restart would do?  I'll experiment a bit more.

---

### Post by Joseph Schwenker on 2010-08-31
Hmm... well, whatever I did, things seem to be working now.  It seems that smbtree started working after I did step two, though I started a new session after I finished the whole thing.  I might not have even had to do the steps after two.  Either way, the network seems to be working properly for the time being.  I'm currently backing up my data (hopefully it doesn't randomly stop like it did last time!), and I'll test the printer and some other stuff in the days to come.  If anything's up, I'll post about it.

---

### Post by Joseph Schwenker on 2010-09-01
Well, it's still working today, and most of my data was backed up last night, so all seems good.  However, when I started my computer today (this might be related to the files I edited, as instructed by part two), Ubuntu went to the boot screen and displayed a message about being unable to mount / or something.  It gave me options to fix it, wait, or manually fix it.  I chose to manually fix it, and noticed that the screen was running at the default resolution for the boot screen instead of 1680x1050, which I specified in a system file months ago.  Also, the screen was too far to the left, which I had also fixed months ago.  After a few ls's and cd's in the manual fix terminal, I discovered that, thankfully, all of my data was intact.  I tried pressing ctrl alt F8 to return to X, but nothing happened.  I then tried sudo shutdown now, and then I was taken to X.  However, the bar with the accessibility button, the keyboard layout button, and the user switching options at the login screen was at the top instead of the bottom.  I was able to login, however, and everything seems okay.  When I tried to start Chrome, it wouldn't start.  Knowing that it was a permissions issue, I ran Chrome from the terminal to see the output.  Contrary to what I expected, it was not a problem with /opt/google/chrome's permissions, but a problem with /dev/shm.  This is the output:

> joseph@joseph:/opt/google/chrome$ ./chrome
[2974:2982:416897650:FATAL:base/shared_memory_posix.cc(193)] Creating shared memory in /dev/shm/.com.google.chrome.eoxhia failed. This is frequently caused by incorrect permissions on /dev/shm.  Try 'sudo chmod 777 /dev/shm' to fix.: No such file or directory
Aborted

I ran the command, and everything worked as expected.  smbtree also works.
The disk utility reports the same data as before: one sector bad, which passes.
I'll try rebooting the computer to see if the same thing happens.  Hopefully, it won't.  Hopefully, this is a problem with the files I edited, and not with my hard drive.  You can imagine how relieved I was that I had backed up my data the previous day!

---

### Post by Joseph Schwenker on 2010-09-01
Well, my previous problem seems okay for the moment, however, I am now unable to access the network.  I was trying to finish backing up my videos folder, then to check to see that I had all of my files backed up.  I got an error message saying that the directory didn't exist.  I ran smbtree, and I got:

> failed negprot: ERRnomem
failed negprot: ERRnomem


Marvelous.  I'll try logging out then back in.  The computer is still on that I was sending the data to.  Why the hell does it keep stopping halfway through?!

Edit: Logging out then back in did nothing.  Same output.  I'll try restarting next.

---

### Post by Joseph Schwenker on 2010-09-01
Restarting didn't work either.  I'll trying restarting the remote machine.  smbtree now outputs nothing.

---

### Post by Joseph Schwenker on 2010-09-01
Well, my mom turned off her computer while mine was restarting, thus creating the blank output.  Either way, smbtree now outputs normally.

---

### Post by jrevillini on 2010-09-09
> **fbobraga said:**
> It seems strange, but after installing the ***ntfs-config*** package here, a issue like yours stoped...

HELLS TO THE YEaYAH!

I just installed Maverick Meerkat as a guest OS using virtualbox, and was getting this until I followed your advice:

[INDENT]Could not display "network:///".
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.[/INDENT]

This wasn't a problem in Lucid, I don't think.  Maybe they stuck it in there because their LTS needed ntfs support natively to make corporate clients happy.  Who knows.  

ANYWAY, you made my day!!!! Gracias, rice, and many beans to you.

---

