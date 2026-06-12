---
title: "Problem with symbolic link"
date: 2012-08-08
forum: General Help
---

### Post by dannyvanderzande on 2012-08-08
I'm writing a bash rsync backup script which has to create a symbolic link at some point during the script. I have set variables for the destination, host, year, month, day, hour and minute.

This is where I want it to link to
```
/home/USER/backup/HOSTNAME/2012/08/08/17:xx/

```
This is where I want the link itsself to be:
```
/home/USER/backup/HOSTNAME/

```
I tried the following command in my script:
```

cd /home/USER/backup/HOSTNAME
ln -s "$DESTINATION/$HOST/$YEAR/$MONTH/$DAY/$HOUR:$MINUTE" current
```

I do get a symlink when I open this it points to:
```
/home/USER/backup/HOSTNAME/2012/08/08/

```and there's a folder in the called ```
17:xx
```

How do I get my symlink to point to this subdir directly instead of to it's parent?

Sorry for the confusing message. I'm not sure how I can explain this better

---

### Post by hackTHEgibson on 2012-08-08
**ln --help**
Usage: ln [OPTION]... [-T] TARGET LINK_NAME   (1st form)
  or:  ln [OPTION]... TARGET                  (2nd form)
  or:  ln [OPTION]... TARGET... DIRECTORY     (3rd form)
  or:  ln [OPTION]... -t DIRECTORY TARGET...  (4th form)
In the 1st form, create a link to TARGET with the name LINK_NAME.
**In the 2nd form, create a link to TARGET in the current directory.**
In the 3rd and 4th forms, create links to each TARGET in DIRECTORY.
Create hard links by default, symbolic links with --symbolic.
When creating hard links, each TARGET must exist.  Symbolic links
can hold arbitrary text; if later resolved, a relative link is
interpreted in relation to its parent directory.

---

### Post by dannyvanderzande on 2012-08-08
I had to read this at least 10 times but I understand now.

I managed to create a symlink called hh:mm and renamed it to current! Thanks a lot for sending me in the right direction.

As they say:
[I]The true delight is in the finding out rather than in the knowing.
-- Isaac Asimov[/I]

---

