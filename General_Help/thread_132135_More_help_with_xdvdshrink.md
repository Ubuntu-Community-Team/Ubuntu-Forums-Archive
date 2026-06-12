---
title: "More help with xdvdshrink"
date: 2006-02-17
forum: General Help
---

### Post by psilo357 on 2006-02-17
everytime i start to rip a movie, i get the following output, anyone know what is the problem?

thanks

 DVDShrink 2.6.1 - Aug 26, 2005
   Rick Saunders (ozzzy1@gmail.com)
________________________________________________________

   INFORMATION

   Project:                                  1FRIDAY
   File cleanup?                             Yes
   Auto-burn?                                Yes, prompt
   Save ISO with burn?                       No
   DVD Title:                                1
   Audio channel:                            0
   Subtitle channel:                         None

   PROGRESS   Rip started at 17:26:08

   DVDSHrink Function                        Status    Elapsed

   Reading the chapter list                  Done!    [00:00:00]
   Ripping Title                             Working!Error!
tcextract: no process killed

   DVDShrink has failed!
   Error:
      -> tccat reported an error copying title!
   Command run:
      -> nice -n +19 tccat -i /dev/cdrom1 -T 1,-1 -L 2> /media/my_storage/dvdtemp/1FRIDAY/tccatdebug.txt | tee /media/my_storage/dvdtemp/1FRIDAY/1FRIDAY.vfifo /media/my_storage/dvdtemp/1FRIDAY/1FRIDAY.afifo >/dev/null 2> /dev/null

   Check all your files etc. If it appears that the problem is
   ephemeral restart the script with 'dvdshrink --restart'

   End of command output
   ---------------------------------------

libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/cdrom1 with libdvdcss.
libdvdread: Can't open /dev/cdrom1 for reading
[tccat] (pid=10236) failed to open DVD /dev/cdrom1

   See the log file at /home/randy/1FRIDAY.log for more information.
   Exiting!


   Thank you for using OzWare!


Hit any key to close terminal and exit!

---

### Post by psilo357 on 2006-02-18
bump for today

---

### Post by psilo357 on 2006-02-19
bump again, or another link i can get support for this program.....

---

### Post by psilo357 on 2006-02-23
up the list again, on like page 15 now

---

### Post by psilo357 on 2006-03-01
bump^^^^^

---

### Post by BLTicklemonster on 2006-12-17
... wow. clap clap clap great support. Hope you resolved your problem.

---

### Post by maxcugnet on 2007-06-06
Hi everybody,

I've got exactly the same error. Has anyone an idea to fix it?

Thank's

Max

---

