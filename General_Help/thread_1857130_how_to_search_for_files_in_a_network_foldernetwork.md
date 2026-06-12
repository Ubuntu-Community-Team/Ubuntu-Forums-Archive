---
title: "how to search for files in a network folder/network share"
date: 2011-10-09
forum: General Help
---

### Post by agrayray on 2011-10-09
Hello,

Is it possible to "find files" in a mounted network share/folder?  I can not seem to be able to select them from the find screens?

Thanks in advance!

---

### Post by mikejonesey on 2011-10-09
yes of coarse... mount with samba then use ```
find . -type f -iname *somename*
```

if you want to search file contents;
```
find . -type f -exec grep -i -l "file contains..." '{}' \;
```

google the unix find command or use the manual ```
man find
``` or let us know your search criteria n i'll let you know the command...

---

### Post by agrayray on 2011-10-09
thanks for the reply..however i more need thumbnails for the search results so i am more concerned on how to this graphically...so is there is a way to do this graphically?

---

### Post by mikejonesey on 2011-10-09
hmm i'm more a command line buff, depends on the number of search results you expect, i can have them pop up in the image browser but i'll be you want them displayed in a nautilus window... hmm... best i can think of, off the top of my head would be...

```

#!/bin/bash

mkdir ~/Pictures/temp2358
nautilus ~/Pictures/temp2358
find . -type f -name *.jpg | while read filename; do
ln -s $filename ~/Pictures/temp2358/`basename $filename`
done

echo "Press enter when you've finished to remove temp dir..."
read
rm -rvf nautilus ~/Pictures/temp2358
echo "Done..."

```

---

### Post by mikejonesey on 2011-10-09
ps most scripts like this you would run the nautilus like as a background process but nautilus does not take command of console so it's ok...

just save script as my-image-search.sh
chmod u+x my-image-search.sh
and run iit, obviouly you will want to customise the find criteria though...

---

### Post by mikejonesey on 2011-10-09
ps... if anyone knows a way to do this kind of search with the standard search tool... or if there is a tool in the repos for this... please enlighten us...

---

### Post by agrayray on 2011-10-09
thanks mike..yes to be even more specific is there is a way in nautilus or the general search to do this...my options are basically 

1 - do this in ubuntu graphically
2 - use a virtual machine with xp that does this standard
3 - vpn to host and do search and then move the share

so far, I have always been doing option 2 to connect to a 500GB share full of pictures and movies so I need thumbnails to find exactly what I need as I'm mostly doing generic searches like DSC*.jpg or something and then find the files I need visually from the thumbnail.  Both options 2 and 3 are not as ideal as option 1 as i would like to do this procedure all on base computer which is ubuntu 10.10 gnome.

THANKS AGAIN!

---

### Post by mikejonesey on 2011-10-09
until someone else replies, 

I forgot 2 say what the script does if you havn't tried it out... the script above will display search results in thumbnail format in a nautilus window by generating symbolic links to them in a temp dir and displaying that dir in nautils... upon finish when you push enter it will simply remove the temp directory...

should be better than option 2, untill someone sorts option 1 for you...

---

### Post by agrayray on 2011-10-10
Thanks again mike...and for all whom this topic might prove fruitful I have found the way to do this graphically through nautilus.

The way i found to do this is to select the hidden directory where smb/network shares are mounted from a response by capscrew to a related post I made here:

[http://ubuntuforums.org/showthread.php?p=11329016#post11329016](http://ubuntuforums.org/showthread.php?p=11329016#post11329016)


The Nautilus mounted shares are in your home directory (~) at:  ~/.gvfs

Edit: that is:  /home/<your_login>/.gvfs

Edit2: You can navigate there using Nautilus after using ***Ctrl+h*** to show the hidden files.                                                                                                                                    [I]                                              Last edited by capscrew; 2 Hours Ago at 05:41 PM..

All you need to do is select "other" from the locations in the find files screen and navigate or type your .gvfs folder and then your mounted share.  This will put your network share folder in the location to search on and the rest works perfectly.

Hope this helps!

[/I]

---

