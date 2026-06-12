---
title: "Backup Evolution from command line?"
date: 2011-03-11
forum: General Help
---

### Post by Seeked on 2011-03-11
Hello all,

Sadly I am unable to login to a particular user via the GUI, but that is another thread ( [http://ubuntuforums.org/showthread.php?t=1704303](http://ubuntuforums.org/showthread.php?t=1704303) ).

I know that you can create a single backup file of all your emails and settings when you have access to the GUI in Evolution.  Since I am unable to login to gnome (or KDE) but I am able to login to the command line by su to the user I would like to create a that evolution backup file.  I will be reinstalling Ubuntu.

Anybody know how this can be done?

Thank You

---

### Post by Seeked on 2011-03-11
bump

---

### Post by kennedyjch on 2011-05-05
Would be interested in this answer too - after a failed upgrade to 11.04 and losing all my e-mails (only 2 months worth), I would like a programmed CRON job that will backup on weekly basis.

---

### Post by dcstar on 2011-05-06
> **kennedyjch said:**
> Would be interested in this answer too - after a failed upgrade to 11.04 and losing all my e-mails (only 2 months worth), I would like a programmed CRON job that will backup on weekly basis.
Try:
```

/usr/lib/evolution/**2.28**/evolution-backup --backup evolution-backup.tar.gz --gui
```

The **2.28** is the version of Evolution that you are using (that is what my 10.04 system uses), change to suit.

evolution-backup seems to have the following options:

--backup *filename*
--restore *filename*
--check *filename*
--restart  (Restarts Evolution after the backup is finished)
--gui      (Displays the progress box - needed to make sure the program exits)

Set the "DISPLAY" variable in any cron job to allow the gui option to function.

---

