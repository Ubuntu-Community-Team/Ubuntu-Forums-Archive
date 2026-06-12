---
title: "Run Cron job at shutdown or just before"
date: 2006-04-26
forum: General Help
---

### Post by abs on 2006-04-26
hello all,

I have a simple scrip to back-up my folders to my second drive, however, I would like
this to happen when i shut down the computer, any idea on how to trigger this job
just before shutdown,

this would be ideal as it would back up my 3D work everytime i shutdown my computer,

any ideas all,

would really appreciate it.

thanks



--

---

### Post by GTvulse on 2006-04-26
Run a shutdown script (placed in /etc/init.d) at runlevels 0 and 6. 

Read the documentation files in /usr/share/doc/sysv-rc, the man page of update-rc.d and maybe the relevant section of the [Debian Policy Manual]("http://www.debian.org/doc/debian-policy/#contents").

---

### Post by lmierzej on 2006-04-26
[QUOTE=abs]
this to happen when i shut down the computer, any idea on how to trigger this job
just before shutdown
[/QUOTE]

When your system is halting it switches to runlevel 0. There are files under /etc/rc0.d. These files are being executed (these are not files exactly these are links to files, do: ls -all) when you make a shutdown. Look for example at S40unmountfs - this script is unmounting your partitions. Add your own script there :)

lmierzej

---

### Post by abs on 2006-04-27
thanks for the replies, I had a playaround for a little bit, but i thought id leave it alone for now, 

insted i just put a small icon in bottom right corner that calls the script, i have also got it in crontab,

---

### Post by justleen on 2006-04-27
if you want it very badly in crontab, you could always add a shutdown -h now at the end of your script, then add it to crontab.

That way it ll look like its executed by crontab just before shutdown! 


:rolleyes:   :cool:

---

### Post by abs on 2006-04-27
do you mean adding 

shutdown -h in my .cron job or in my .sh script

a quick question, whats a file ending with ~  mean, is it a temp file or backup.

on windows such files are made as temps when working in office or so.

---

### Post by justleen on 2006-04-27
[QUOTE=abs]do you mean adding 

shutdown -h in my .cron job or in my .sh script

a quick question, whats a file ending with ~  mean, is it a temp file or backup.

on windows such files are made as temps when working in office or so.[/QUOTE]


adding it to your .sh script..
i was only joking.. 
since if you do that, and you add it to crontab to run @ 24.00, it would run your script and then shut down.. I pretty sure thats not what you want:  imagine working late one day.. @24.00h *poef* system goes down and leaving you shouting "oi! i still had to save that!" :)

~files are backups in

---

### Post by abs on 2006-04-27
:)...... to bew honest i was thinking that,

hence why i was asking if it should be put it in the .sh,

I was thinking if it went in cron, and then it would just shutdown, intresting way to end the day, prob start thinking that my Ubuntu is haunted by M$ ghost of somesort, bamn it BIll...... go away...... ;)

--

crontab slapBILL$.cron

every 1 sec, a monkey comes and slaps M$ in and shouts oyyyyyyyy, no more
ms crap, the world has already too mush shit in it and dont need you adding to it
....

---

