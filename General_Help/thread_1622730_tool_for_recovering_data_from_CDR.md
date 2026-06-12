---
title: "tool for recovering data from CDR"
date: 2010-11-15
forum: General Help
---

### Post by saphil on 2010-11-15
Is there any tool you know of for recovering data from a CDR that has been written, but which shows no files when opened in nautilus?

```

wolf@Night-Flyer:~$ sudo ddrescue /media/cdrom0 /home/wolf/kingsley/ocd
[sudo] password for wolf: 
Press Ctrl-C to interrupt
rescued:         0 B,  errsize:    4096 B,  current rate:        0 B/s
   ipos:      3072 B,   errors:       1,    average rate:        0 B/s
   opos:      3072 B,     time from last successful read:       0 s
Finished  

wolf@Night-Flyer:~$ sudo ddrescue /media/cdrom0/ /home/wolf/kingsley/ocd /home/wolf/kingsley/ocdlog
Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:         0 B,  errsize:       0 B,  errors:       0
Current status
rescued:         0 B,  errsize:    4096 B,  current rate:        0 B/s
   ipos:      3072 B,   errors:       1,    average rate:        0 B/s
   opos:      3072 B,     time from last successful read:       0 s
Finished                   
wolf@Night-Flyer:~$ cat /home/wolf/kingsley/ocdlog
# Rescue Logfile. Created by GNU ddrescue version 1.11
# current_pos  current_status
0x00000C00     +
#      pos        size  status
0x00000000  0x00001000  -
                 

```

---

### Post by JustinR on 2010-11-15
PhotoRec

```

sudo apt-get install testdisk

```

---

### Post by saphil on 2010-11-16
Thanks.
I tried it but still got nothing at all.  The disk shows blank in the file system.  :-(
There was a package on the deft distro (I think), or maybe Backtrak, that had a really interesting recovery program.  Have to get copies of those, I guess to see if I can pull content off the disk.

---

