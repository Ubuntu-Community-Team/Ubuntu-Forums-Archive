---
title: "/var/log files are huge; mounting large hard drives"
date: 2010-10-09
forum: General Help
---

### Post by flamefury on 2010-10-09
syslog, messages and kern.log are incredibly huge files that are taking up a lot of space on my hard drive. Is it safe to remove them and/or to reduce logging so it doesn't take such an enormous amount of hard disk memory? If so, how can I reduce the logging so it doesn't produce logs that are 10s of GB in size?

Also, mounting a drive places it into the folder /media. Will it become problematic if the size of the mounted drive exceeds the amount of free space available on my Ubuntu partition?

---

### Post by dcstar on 2010-10-09
> **flamefury said:**
> syslog, messages and kern.log are incredibly huge files that are taking up a lot of space on my hard drive. Is it safe to remove them and/or to reduce logging so it doesn't take such an enormous amount of hard disk memory? If so, how can I reduce the logging so it doesn't produce logs that are 10s of GB in size?
........

Find the problem causing the large log files.

---

### Post by flamefury on 2010-10-09
It probably has something to do with external media, but I wasn't really successful in confirming since the log files were 4 GB, 12 GB and 23 GB respectively and gedit had far too much trouble loading enough lines for me to do an extensive check.

I grabbed the tails and placed them into a new file to conserve on space for now and it's doing all right.


But about the hard drive mounting...what would happen if the mounted drive's contents exceed the available space of the Ubuntu drive?

---

### Post by SeijiSensei on 2010-10-09
Do you have logrotate installed?  (dpkg -s logrotate for the answer).  It seems to be installed by default in both the server and client versions of Ubuntu.  It will automatically rotate the standard log files on a weekly basis.  You can have it compress the logs after rotation as well.  If it's not on your system, "sudo apt-get install logrotate" will do the trick.

If the root partition is full, some types of programs will cease to function.  I've had mail servers stop accepting messages when there's no room left in /var/spool/mail, for instance.

I agree with the posters above that say you need to determine why the logs are filling.  Is this an Internet-facing machine with a firewall?  Perhaps you're being bombarded with external probes that are filling the kernel logs?

Just run "tail -f /var/log/syslog", "tail -f /var/log/messages" and "tail -f /var/log/syslog" in separate terminal windows.  You should see the source of your problem pretty quickly if the logs are filling as fast as you report.

---

### Post by flamefury on 2010-10-18
There's nothing in there that looks out of the ordinary since I cut them down, and the logs haven't been filling up at the exponential rate they did before.

I can go grab what they look like right now since they're considerably smaller, but I'm on Windows so that'll have to wait.

If I were to make a guess, one of my external drives or maybe even the USB stick caused the problem. Can't confirm at the moment.

---

