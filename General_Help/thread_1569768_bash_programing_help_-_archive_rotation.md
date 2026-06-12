---
title: "bash programing help - archive rotation"
date: 2010-09-07
forum: General Help
---

### Post by chrisbay90 on 2010-09-07
Hi,

I have put together a script to make incremental time machine like version controlled backups of my important documents based on the example by Michael Jakl [http://blog.interlinked.org/tutorials/rsync_time_machine.html](http://blog.interlinked.org/tutorials/rsync_time_machine.html)

I would like to keep old backups, but not let them increase infinitely. A compromise is to hold old backups of decreased frequency and new backups of high frequency.

Now I am trying to add a section to the end of this script, that will:
  if there are more than 100 backups
     delete every fourth* of the 40 oldest backups (10 in total)

*In this case the 2nd, 6th, 10th and so on. (as opposed to 1, 5, 9).

my script so far looks like this
```
#!/bin/sh

FILESTOBACKUP=/home/chris/Documents/Uni/all
BACKUPLOCATION=/home/chris/Documents/Uni/backups

date=`date "+%Y-%m-%dT%H:%M:%S"`

rsync -aP --link-dest=$BACKUPLOCATION/current $FILESTOBACKUP $BACKUPLOCATION/back-$date
rm -f $BACKUPLOCATION/current
ln -s back-$date $BACKUPLOCATION/current

echo "Break point 1"
if (( `ls -1 $BACKUPLOCATION | wc -l` > 100)); then
echo "Breal point 2"
  let count=0
  for folder in `ls $BACKUPLOCATION` ; do
    let count=$count+1
    if (($count < 40)) ; then
      let modulus=$count%4
      if [ $modulus -eq 2 ] ; then
        #rm -r $BACKUPLOCATION/$folder
        echo $folder
      fi
    fi
  done
fi
```

The first backup section works but the archive rotation section doesnt. I get the error.
```

Break point 1
./backup.sh: 26: 133: not found
```

however if I copy and paste the arcive rotation section straight into a terminal it echo's the desired folders. It's very puzzling to me :S
Can anyone help me at all?

---

### Post by DaithiF on 2010-09-07
Hi,
its because you're not executing the script with bash.  on ubuntu desktop /bin/sh is a symlink to the dash shell.  dash doesn't support the ((  )) construct for arithmetic expressions.

change your shebang to #!/bin/bash and you should be good.

---

### Post by chrisbay90 on 2010-09-07
> **DaithiF said:**
> Hi,
its because you're not executing the script with bash.  on ubuntu desktop /bin/sh is a symlink to the dash shell.  dash doesn't support the ((  )) construct for arithmetic expressions.

change your shebang to #!/bin/bash and you should be good.
Thanks so much for taking the time to look at my problem, I really appreciate that. Very good eye! :)

What a silly mistake :P.

Anyone have any general thoughts on my method of archive rotation.

---

### Post by DaithiF on 2010-09-07
> **chrisbay90 said:**
> Anyone have any general thoughts on my method of archive rotation.

v. quick reading of your logic, so I may be wrong, but lets say you start taking backups on 1st Jan, after a year of backups & purging/rotating with this script, wouldn't you be left with the earliest file (1st Jan) and then 99 contiguous files from late-Sept onward?  I thought you might be aiming for a more distributed distribution, so to speak.

---

### Post by chrisbay90 on 2010-09-07
> **DaithiF said:**
> v. quick reading of your logic, so I may be wrong, but lets say you start taking backups on 1st Jan, after a year of backups & purging/rotating with this script, wouldn't you be left with the earliest file (1st Jan) and then 99 contiguous files from late-Sept onward?  I thought you might be aiming for a more distributed distribution, so to speak.

Surprisingly yes you picked my logic im not sure how as I see its somewhat tangled.

Well I should probably supply the context of these backups. They are not your classical backup, for that I do a full tar off-site once a week (although only the current revision is kept). This is a same disk backup run every 15min on assignments and the likes, so that in the event i screw something up i can revert back to a checkpoint. Therefore only the backups of the last week (really only the last 24 hours) are of great importance but it would be nice to keep older backups as a reference, just incase, of decreasing frequency as you look back towords the oldest backup (and yes the oldest)

--MY INTENTION OF THE SCRIPT --
have a large number of concurrent backups from the most recent of dates.
Have some old backups but of low frequency.
Have some very old backups of very low frequency.

--WHAT I WOULD LIKE AN OPINION ON--
Do you think i will acheive that
Or can you see a flaw that may result in something undesired or even unfavourable?

This is my graphical representation of what im expecting.
'-' being existing backups
'*' being deleted backups
backups to the right of the '|' being newer than the last purge/rotate
each line representing the state of backups after a purge/rotate cycle


----------------------------------------------------------------------------------------------------
-*---*---*---*---*---*---*---*---*---*--------------------------------------------------------------|----------
-**--*-*-*--**---**--*-*-*--**---**--*-*---*---*--------------------------------------------------------------|----------
-***-*-*-**-**--***--*-***--**-*-**--***---**--*-*---*---*--------------------------------------------------------------|----------

Thank you so much again for your help DaithiF. Sorry for the long post went on a bit of a midnight rant.****

---

