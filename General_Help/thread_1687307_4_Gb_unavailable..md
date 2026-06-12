---
title: "4 Gb unavailable."
date: 2011-02-13
forum: General Help
---

### Post by Tha Tawa'S on 2011-02-13
Hi all,

My Ubuntu 10.10 system told me that / has only (around) 480Mb available.
So I ve looked for my biggest files.
They are all in /var/log. they are kern.log, messages.log, ufw.log and syslog.log.
I know that is totally anormal that those 4 files reached 4Gb, but this is not the aim today, I will search later why; but even if I delete those files, I do not get more free space. I ve already restarted my laptop several times whithout succes.

Does someone knows why? and, of course, how to solve it ?
many thanks.

---

### Post by oldfred on 2011-02-13
Normally when you delete something it goes into trash & you have to empty trash.

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by SaintDanBert on 2011-02-13
Remember, too, that you may ask for file space of "nnn,nnn,nnn bytes" and the file system will give you that space in a chunk that is some number of whole sectors ("clusters" are also used).  For example, a 50-byte file would take 512 bytes if your sector is 512 bytes.  It would need 1024 bytes if the sector was 1024 bytes.

The FAT and FAT32 file systems from the win-dose world might use a 4096-byte "cluster" making small files very disk space wasteful.

~~~ 0;-Dan

---

### Post by Tha Tawa'S on 2011-02-13
Many thanks !!!
My very big files were in /root/.local/share/Trash

---

### Post by srs5694 on 2011-02-13
More generally, files in /var/log are usually kept in check by a procedure known as *log file rotation*, which is handled automatically. If you have excessively large log files, then that means that either your log file rotation isn't working or something is causing the log files to grow unusually quickly (maybe a server keeps crashing and re-launching, or something's generating excessive error messages). Try doing a Web search on "Ubuntu log file rotation" to learn more about the process of managing your log files.

---

