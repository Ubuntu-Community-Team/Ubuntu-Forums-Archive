---
title: "Move Files Script"
date: 2012-01-13
forum: General Help
---

### Post by OverDarkTM on 2012-01-13
Hey Guys!

I'm new here and I have a problem.

I have DropBox installed on my Ubuntu machine and my iPad. When I'm out of the house I usually upload things from my iPad to my DropBox and my DropBox from Ubuntu automatically downloads the files.

Because I have the basic 2GB DropBox account and it's almost full, I need a script that would check every X seconds if the DropBox folder (default /home/myuser/Dropbox) has files, and if it has, to move all the files to a Y folder and delete those from the DropBox folder.

I don't want to filter any files.
I want it simple. If there are files in the Dropbox folder, move all of them to another folder and delete them from the Dropbox folder.

Any piece of code? :confused: Any chance that someone could teach me how to set that bash script to run at startup of the machine?

Cheers!

---

### Post by OverDarkTM on 2012-01-14
I've tried a lots of things and I created this code myself at the end:

```
#!/bin/bash
Dropbox="/home/youruser/Dropbox"
Directory="/home/youruser/newfiles"

if [ "$(ls $Dropbox)" ]; then
     echo "Found files in $Dropbox!"
     echo "Moving..."
     cd $Dropbox
     mv * $Directory
     echo "Everything done!"
else
    echo "$Dropbox is Empty!"
    echo "Nothing to move."
fi
```

This will check the "Dropbox" folder for files. If there are any, they will be copied to "Directory".

Now I'm searching for a way to make this run every 15 minutes...

---

