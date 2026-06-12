---
title: "CUPS disappears"
date: 2009-11-24
forum: General Help
---

### Post by mike67114 on 2009-11-24
[FONT=Arial][SIZE=2]I recently upgraded to 9.10 form 9.4. I have a simple HP LaserJet 5p[/SIZE][/FONT][SIZE=2] on USB. This printer has worked reliably, and works now -- sometimes.

It appears that CUPS disappears regularly after printing. I can get a few jobs, then bang!...no CUPS.

I can reinstall CUPS and print normally for a few minutes to a few hours then it disappears again. 

Please help.[/SIZE]

---

### Post by nikgare on 2009-11-24
Have a look in the log file.
/var/log/cups/error_log

---

### Post by mike67114 on 2009-11-25
Following a blank error_log file I have six .tar.gz files that appear to represent the error logs for the last six installs of cups. Here's the latest one. The others are similar.

> E [24/Nov/2009:15:23:03 -0600] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [24/Nov/2009:15:23:03 -0600] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
W [24/Nov/2009:15:23:04 -0600] [CGI] Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect

---

### Post by Aardolan on 2009-11-25
I'm having the same issue with an HP C3140 all in one. Any news on this?

---

### Post by Soul-Sing on 2009-11-25
Is this after the recent cups-update in 9.10?

---

### Post by nikgare on 2009-11-25
You need to edit the file /etc/cups/cupsd.conf, and change the log level to debug and then have another look in the log file.

---

### Post by mike67114 on 2009-11-28
leoquant: Yes, this is after updating to 9.10

First, I've been gone for the holiday so I apologize for taking so long to reply.
I edited .../cupsd.conf as suggested. Then I tried to print a few random documents. Now I
have seven .gz error_log files and one (current?) non-gz'ped. That file is blank.

---

### Post by RJ12 on 2009-11-28
Just to make sure CUPS is disseappering can you visit [http://localhost:631](http://localhost:631) (the web based version of CUPS) then you can edit your jobs from in there also and will test to see if CUPS is still up.

---

### Post by mike67114 on 2009-11-30
Firefox cannot connect to [http://localhost:631]("http://localhost:631/")

---

### Post by mike67114 on 2009-11-30
Firefox[SIZE=2]* says it*[/SIZE] cannot connect to [http://localhost:631]("http://localhost:631/")

---

### Post by mike67114 on 2009-11-30
Further information:

I am running CUPS 1.4.1-5ubuntu2.1 .

Browsing through my startup logs I found that the cups server was not found, but the printer was recognized by the USB system.

I installed the (not previously installed) HPLIP packages (HPLIP, HPLIP-GUI, HPLIP-docs, etc.) using synaptic.  [http://localhost:631]("http://localhost:631/") then became available, and the printer was recognized. 

After a system reboot the CUPS server again is not found, and, again, no printing and no access to [http://localhost:631]("http://localhost:631/") .

Trying "system >> preferences >> default printer" raises a dialog box with the error message "CUPS schedler is not running".
_________

Am I mis-interpreting this?  Is the true problem that CUPS server is quitting and not restarting?

My 9.04 printed reliably and this old LaserJet 5p has always been super reliable.

---

### Post by mike67114 on 2009-12-04
After more (all night) poking around I have determined that CUPS is not "disappearing" but is not restarting after rebooting. I can restart Cups with the terminal command 
"sudo /etc/init.d/cups restart". I will add that line as a startup script.

I feel there should be a real _[SIZE=1]solution[/SIZE]_ for this problem not just a _[SIZE=1]work-around[/SIZE]_.

Thanks for the help.

---

### Post by John1232 on 2009-12-04
I too had problems with my HP printer when upgrading from 9.04 to 9.10. I was going to add a startup script but choose another way; install sys-rc-conf and configure CUPS from there:

     sudo apt-get install sysv-rc-conf

Then run:

     sudo sysv-rc-conf

There will be a list of services running with a "X" if it runs a a particular time during startup. Scroll down until you find "cups". Mine was checked under columns 2,3,4,& 5. Now go under the "S" column (Startup Column) and hit your space bar to put a X there. Now hit "q" on your keyboard to exit sysv-rc-conf. Restart your system. This worked perfect on my system. Hope it helps you guys.

---

### Post by mike67114 on 2009-12-07
That does seem to work. Thank you very much!

---

### Post by pranayama on 2009-12-19
I have had exactly the same problem with cups, and also boinc and virtualbox daemons not starting on boot.

sysv-rc-conf has fixed it for now.

Has anybody submitted a bug report about this yet? I can't find one on Launchpad.

---

### Post by PC_load_letter on 2009-12-23
I have the same problem now on my Karmic box (clean install 64-bit). This was not a problem before, only recently, so it might be related to a recent update. 
I totally agree with the OP that this is outrageous. There should be a proper fix.


EDIT:
I don't know why the OP marked this one as solved, and in my case I can not seem to be able to start CUPS manually!!!!? I get the following
```
~$ sudo /etc/init.d/cups force-reload
 * Reloading Common Unix Printing System: cupsd                          [fail]
```

Any idea how to fix this? I have a Samsung printer that used to work perfectly on the same computer since Feisty.

---

### Post by ipguru99 on 2009-12-30
Ugh.. HAS to be something fairly recent.. I spent 2 days trying to figure out why my OO Writer wouldn't open Templates anymore.. or they took 2 minutes, anyway... Yeah, it was CUPS!  I got all the way done with tcpdump'ing (because I thought it was a network issue.. Templates opened just fine with NO network connection up).  The only other service was CUPS... but I didn't notice it before, because it was not running (I can't believe I haven't printed anything since before 12-18-09).. neither is ssh.. what the hell happened with UPSTART?

I changed the ```
Listen localhost:631
``` to ```
Listen *:631
``` in the /etc/cups/cupsd.conf file and was able to start cups.  I still see the errors about the .hplip directory being in the /var/spool/cups/tmp folder.. but I can actually go into my System,Administration,Printers again!... Oh.. and my freakin' OO Templates open in 5 seconds again!

---

