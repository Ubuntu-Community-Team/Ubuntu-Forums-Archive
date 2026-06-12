---
title: "Timed Shutdowns"
date: 2006-04-24
forum: General Help
---

### Post by Rios on 2006-04-24
Hope this isn't too daft a question!  ;) 

My broadband ISP has peak cap limits, but an 8 hour window of off-peak unlimited downloading.  Is there a facility in Ubuntu that will allow my PC to switch off at a certain time, therefore shutting down my internet activity and keeping me under my cap?

I know this is possible in Windows, either via the command prompt or via free utilities, but would prefer the stability and better security of Linux while downloading.

Many Thanks

---

### Post by cilynx on 2006-04-24
Look into the scheduler "cron" and the program start/stop system "start-stop-daemon".

---

### Post by Sutekh on 2006-04-24
Use the command **shutdown**.  For some more complete instructions use the man page
```
man shutdown
```
To shut down your computer at a certain time use
```
sudo shutdown -h 09:00
```
To halt your PC at 9AM.

Cron jobs are useful too, so you can shutdown certain applications before shutting down, it makes them happeier when they restart.

A cron job is easy to create using **crontab**.  Start by creating a new file, I will use a crontab that I use with Azureus.
```
export EDITOR=nano;
nano azureus.cron
```
This specifies the default editor to nano (you can use whatever you wish) and opens a new file azureus.cron, a simple cron job that I use to start Azureus when my off-peak starts and close it when it finishes
```

00 02 * * * export DISPLAY=:0 && /usr/bin/azureus
00 09 * * * export DISPLAY=:0 && killall -SIGHUP java
```
The first part of the line contains the time at which the command is to be executed in minutes and hours, eg 00 02 - 02:00

The second part of the line specifies the day of the month, month and day of the week. * * * means every day.

The last part of each line is the command that is executed at the correct time, the first line open azureus (using the full path) on the main screen.  The second line sends a command to kill java and azureus, I found this command on the Azureus wiki.

You can save the .cron file using Ctrl+O and exit using Ctrl+X.

To load the cron job use **crontab**
```
crontab azureus.cron
```
to edit the crontab (when loaded) use
```
crontab -e
```
to check on the crontab use
```
crontab -l
```
to remove the crontab use
```
crontab -r
```

---

### Post by John64 on 2006-04-24
if you are ok with running Wine,  uTorrent has this functionality built in.  Wine shouldnt be too much overhead if all you are doing is running a couple torrents, especially because utorrent has no shared/dynamic libraries and is self contained and extremely low cpu/memory.

If you need the winehq repository, i can post it

Also, while downloading one file, i use 0% cpu, 4mb of ram for the whole wine/utorrent.

---

