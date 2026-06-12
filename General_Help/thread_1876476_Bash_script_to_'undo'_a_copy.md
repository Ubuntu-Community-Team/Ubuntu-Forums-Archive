---
title: "Bash script to 'undo' a copy"
date: 2011-11-06
forum: General Help
---

### Post by Bardwise on 2011-11-06
I just accidentally cp'ed a load of files into /usr/ and need a script that will read the original directory and remove those files from the corresponding locations in /usr/



For instance hello/ contains the files 1 and 2.  I used:

sudo cp -r hello/ /usr/

/usr/ now contains 1 and 2.

I need a bash script that will read the contents of hello/ recursively and delete them in /usr/

---

### Post by clrg on 2011-11-06
First of all: Next time, please be careful. If you are executing commands as root double-check before hitting enter. That simple rule has saved my life countless times.

Secondly, I am only giving you a hint. This code is not tested and I do not take responsibility if it destroys something.

Here you go:

```

find PUT_SOURCE_DIR_HERE|while read i; 
do
    echo "deleting /usr/$i"
    rm -rf "/usr/$i" >/dev/null 2>&1
done

```

A probably much safer way would be to ```
ls -ltr /usr
``` which will make a list of all files in /usr sorted by last modification time, and then deleting them manually.

---

### Post by Bardwise on 2011-11-06
Yes, for the record, the script you posted is highly destructive and recursively delees everything in any folder found, even if it isn't part of the original directory structure.

There's too much to delete by hand, so I'll be tampering around with the script myself.

---

### Post by clrg on 2011-11-06
Of course, if you copied something like bin/foo to /usr/bin/foo, my script will delete /usr/bin which would be inadvisable..

There is no way to know which directories you copied from the source need to stay in /usr (because they're needed there) solely from filenames. One could use modification times, but even that is not really safe.

---

### Post by Bardwise on 2011-11-06
I think I'll just run the script without -rf and clean up the empty directories in another way.  Deleting all empty directories in /usr/ shouldn't be a problem, should it?

---

### Post by matt_symes on 2011-11-06
Hi

I would use the find command and check the creation or modification date of each file and move them into a separate directory based on that value using the -exec switch that comes with find.

Then you can check what is in that directory.

Do _not_ rm -rf as root unless you are _totally_ sure. Anything else is just bad advice.

Kind regards

---

### Post by lswb on 2011-11-06
How about opening the /usr directory in nautilus, use a list view and sort by Date. All the files you accidentally copied will have the same date and time (time within a few seconds or so) Even with a 2 or 3 hundred files it then shouldn't be too tough to review for any that you may want to keep, and block-select the rest for deletion or moving to a different directory.

---

