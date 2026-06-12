---
title: "Avoid duplicates when copying renamed files?"
date: 2011-11-21
forum: General Help
---

### Post by Boytruc on 2011-11-21
Hello everybody

I'm looking to do something.

         I have to get pictures from a folder &#8211; with subfolders which are updated automatically &#8211; with their extensions. 
  These files have to be copied in a folder where a website based  on PHP will edit them (by renaming and creating an XML file) to be  downloadable and integrated in an XML feed.
  Because of the rename function of the script, when I perform the copy again, **all the files are duplicated**, because the script has renamed the original ones already.
  I've tried a few things with rsync but I'm looking for something more powerful because I can't copy files with an external "history".

  > #!/bin/bash find  '/home/name/picture' -name '*.jpg' | while read FILE ; do rsync --backup  --backup-dir=incremental --suffix=.old  "$FILE" /var/www/media ; done wget --spider 'http://myscript.php' ;  #exit 0 

PS: As a little addition, I'd like to replace '.' with a 'space' just after the *.jpeg copy. My PHP script has some problem to define files with comma because of the extension. I'm finking about a command with find &#8211; like I did before &#8211; with a sed function? Is that a good idea?
      

Thanks in advance for your help.

---

