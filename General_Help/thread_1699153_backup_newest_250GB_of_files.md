---
title: "backup newest 250GB of files"
date: 2011-03-03
forum: General Help
---

### Post by aeiah on 2011-03-03
so i have a spare 250GB hdd and about 480GB of films on a 1.5TB HDD. all my important data is backed up elsewhere, but it'd be nice to have the most recent 250GB of films backed up to this extra HDD. 

im thinking that once i determine the newest 250GB of files i can pass that as an include list to 'rsync --delete '. any tips on how i might do this?

---

### Post by seawolf167 on 2011-03-03
The --delete option will delete any files on the destination that are not on the source, so unless you want to mirror the directories you probably don't want this option.

```
rsync -ruvni /source /destination
```

will recursively update the source to the destination and list the changes that will be made, then if that is ok, just drop the -ni to preform the real run

---

### Post by aeiah on 2011-03-03
since i want the newest 250GB of files to be archived to destination, i do actually want to delete any files on destination that aren't on source any more. if i dont, my 250GB backup drive will fill up. think of source not as a full directory, but a list of the 250GB-worth of newest files.

im asking if anyone has any suggestions for generating a list of the newest 250GB of files that i can then pass to rsync, as an include list. this is the rsync line i had envisaged, after id gotten the list generated:
```

rsync -a --exclude '*' --include-from <list of the most recent 250GB of files> --delete source/ destination/
```

if my media drive dies, im sure ill find the will to carry on, even though half of my video files will be lost. all files that are actually important are archived incrementally in a proper fashion - this is just so dont lose *all* my entertainment

---

### Post by seawolf167 on 2011-03-03
You could do something like:

```
ls -R /source > srccontents
ls -R /destination > dstcontents
diff srccontents dstcontents > difflist
```

then pass that list to rsync with (add in your extra options & src/dest)

```
rsync --files-from=difflist
```

---

### Post by aeiah on 2011-03-03
im sorry, i really don't know how to phrase what i want any other way. i have 480GB of files, and i want to copy the newest 250GB to a different drive.

ls -R just recursively lists the contends of directories

---

### Post by seawolf167 on 2011-03-03
> **aeiah said:**
> ls -R just recursively lists the contends of directories

What I was thinking was that since your external drive is 250gb, and you have 480gb of files, the difference between the backed-up files vs. the source files is (480-250=230gb), so you could simply transfer the difference between the backed-up files and the source files to you newly blanked external drive via the ls & diff commands (i.e. list each directory contents, run through diff to create a list of diff. files, then use that file as an rsync argument to only transfer those files)

If you wanted to find differences by date, you could do the same general procedure, though I don't know how you'd set the total size cut off via a command (I think you could just let it transfer the differences by date and have it run out of space at the end of the transfer, then just delete the last incomplete file). This would sort each directory by date, compare the directory contents, give a list of differences, then calculate the total size difference, then you could start that transfer or edit your list (difflist) and delete the last X number of files to get it to 250gb.

```
ls -Rlth /source > srccontents
ls -Rlth /destination > dstcontents
diff srccontents dstcontents > difflist

du --files0-from=difflist

rsync --files-from=difflist
```

---

### Post by aeiah on 2011-03-04
i decided to write a python script for what i wanted in the end. thanks for your help. i dont think your method would work though... 


lets call the oldest data Set A - this only exists on the source device
lets call the newest 250GB Set B - this exists on both.

i then add new files (Set C) to the source drive. if i run your method, the diff between the source and destination will be Set A + Set C - which includes the oldest files and then a small amount of new ones.

anyway, here's my python script. sorry i wasted your time seawolf - i was hoping for an elegant bash solution ill make do with my python script

i decided to use an exclude list instead of an include list, so i could use the rsync flag --delete-excluded to remove data from the destination that is now considered too old. this python code would look a lot neater if i didnt fill it with a shitload of comments, but someone may find it useful.

```

#! /usr/bin/env python
#
# a script to sync the newest x bytes from one directory to another,
# removing old data from the destination where appropriate
#
# 


# destination root, with trailing slash (source directory will be created)
destination = '/media/video_bk/'

#our size limit, in bytes
limit = 225000000

import os, sys, time
from subprocess import *

def issue(cmd):
        global issueError
        p = Popen(cmd, shell=True, stdout=PIPE, stderr=PIPE)
        output = p.communicate()
        return output[0]
        
if len(sys.argv) < 2:
        print 'argument required to be used as source directory'
        sys.exit()

source = sys.argv[1]

#remove trailing slash so we dont wipe the disk out...
if source[-1] == '/':
        source = source[:-1]



# this lists by ctime (time of last modification of file status information)
# see man ls for sorting by modification, creation etc
list = issue('ls -cs '+source)
list = list.split('\n')


totalSize = 0

# list of names to be excluded
names = []

# for each line of the ls -cs command, ignoring the first (total) and last (blank)
for line in list[1:-1]:
        #strip whitespace and split on first space (so size and names are different elements)
        line = line.strip().split(' ',1)
        
        #add to total size
        totalSize = totalSize+int(line[0])

        # if we're over the size limit, we'll add it to the exclusion list
        if limit < totalSize:
                names.append(line[1])


# construct the rsync exclude list
excludeFile = '/tmp/exclude.list'
exclude = open(excludeFile, 'w')
for name in names:
	if '[' in name:
		name = name.replace('[','\[').replace(']','\]')
	exclude.write(name+'\n')

exclude.close()

        
# rsync
cmd = 'rsync -a --progress --exclude-from '+excludeFile+' --delete-excluded '+source+' '+destination
time.sleep(1)
os.system(cmd)


```

---

