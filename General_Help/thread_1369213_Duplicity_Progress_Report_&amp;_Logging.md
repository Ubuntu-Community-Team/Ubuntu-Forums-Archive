---
title: "Duplicity Progress Report &amp; Logging"
date: 2009-12-31
forum: General Help
---

### Post by NertSkull on 2009-12-31
So over the past couple of months I've slowly been figuring out Duplicity backups in my spare time.  They are really quite impressive and I would recommend it to anyone.

But I have run into a question.  When Duplicity runs, it gives very minimal output of what it is doing.  I have my backups being uploaded to a remote server and I would love to see a progress bar or at least get some sense of how much has completed.

I'm backing up many GBs and would love to have it just tell me something like 30% complete, or 35 of 3200 files complete or something along those lines.

Is there a way to do this?

I found this site

[http://duplicity.nongnu.org/epydoc/duplicity.log-module.html#Progress](http://duplicity.nongnu.org/epydoc/duplicity.log-module.html#Progress)

There is a progress entry there, but I have no idea if that has anything to do with what I want.  And even if it did, I have no idea how to go from there to a workable solution.

Any ideas?

---

### Post by tlroche on 2010-12-03
> **NertSkull said:**
> So over the past couple of months I've slowly been figuring out Duplicity backups in my spare time. They are really quite impressive and I would recommend it to anyone.

Me too.

> **NertSkull said:**
> When Duplicity runs, it gives very minimal output of what it is doing. I have my backups being uploaded to a remote server and I would love to see a progress bar or at least get some sense of how much has completed.

Ditto. The {simple,kludgey} way I'm currently getting feedback is with the option 

```
--verbosity info
```

the syntax for which is

> [http://duplicity.nongnu.org/duplicity.1.html#sect5](http://duplicity.nongnu.org/duplicity.1.html#sect5)
> -vverb, --verbosity verb
> Specify verbosity level (0 is total silent, 4 is the default, and 9 is noisiest).
> Verbosity may also be one of: character ewnid, or 
> word error, warning, notice, info, debug. The default is 4 (Notice).
> The options -v4, -vn, and -vnotice are functionally equivalent, as are 
> the mixed/upper-case versions, -vN, -vNotice, and -vNOTICE. 

I can then use that in scripts like

```
  LOGGING_OPTIONS="--verbosity info" # default==notice, "verbosity [may] be one of[:] error, warning, notice, info, debug"
  BACKUP_OPTIONS="--full-if-older-than ${FULL_OLDER_THAN}"
...
  DUPLICITY_BACKUP_CMD="duplicity ${LOGGING_OPTIONS} ${BACKUP_OPTIONS} ${SOURCE_DIR} ${DUPLICITY_TARGET_DIR}"
...
function backup {
  for CMD in \
    "${DUPLICITY_BACKUP_CMD}" \
    "${DUPLICITY_PRUNE_CMD} \
   ; do
    if [[ -z "${CMD}" ]] ; then
      continue
    fi
    echo -e "${CMD}" | tee -a "${LOCAL_LOGFILE_PATH}"
    if [[ "${EVAL}" -eq "${DO_EVAL}" ]] ; then
      eval "${CMD}" 2>&1 >> "${LOCAL_LOGFILE_PATH}"
    fi
  done
}
```

That seems to be basically passing along the rsync messages, e.g. recording which files/folders are examined. It produces logfile lines like (excerpt)

> A .
A Google
A Google/GECommonSettings.conf
A Google/GoogleEarthPlus.conf
A TouchFreeze.conf
A Trolltech.conf
A autostart
A autostart/bluetooth-applet.desktop
A autostart/deja-dup-monitor.desktop
A autostart/evolution-alarm-notify.desktop
A autostart/gnome-terminal.desktop


I can then tail the log while duplicity is running to see where duplicity is in the file tree: better than nothing.

> **NertSkull said:**
> would love to have it just tell me something like 30% complete, or 35 of 3200 files complete or something along those lines.

Me too.

> **NertSkull said:**
> [http://duplicity.nongnu.org/epydoc/duplicity.log-module.html#Progress](http://duplicity.nongnu.org/epydoc/duplicity.log-module.html#Progress) [has] a progress entry there, but I have no idea if that has anything to do with what I want.

That module looks like it's providing the --verbosity functionality above, but that's not really what you want.

---

### Post by NertSkull on 2010-12-19
Thanks, that was a half decent start.  I upped the logging level and I can at least get an idea now of how far it has progressed as I log that to a file.

Better than nothing.  Thanks

---

### Post by tlroche on 2010-12-19
> **NertSkull said:**
> Better than nothing.

Yeah, but not much. If you find something better, please post to this thread.

---

### Post by jsfour on 2010-12-23
Perhaps there is a way to count all of the items to be backed up and compare that with the total backed up. I'm not sure if you could execute this with a shell script, but here is the process that what i was thinking:
-store the total number of files to be backed up into an array
-store the files from the -v output into an array
-count the two arrays and compare the difference
-print the difference to the screen

Looks simple enough... Does anyone know if you can write something like this (I'm at work otherwise i would give it a stab)

---

### Post by blujay on 2011-05-01
One way that might work would be to run Duplicity with --dry-run and log all of the A and M lines, then have another script call Duplicity and read the A and M lines, compare them to the dry run, and display progress based on that.  I haven't tried --dry-run before, so I don't know if it would take too long to do that.

Anyway, it seems like something that could probably be integrated into Deja Dup.  Or has it already?  I haven't used Deja Dup, so I'm not sure.

---

