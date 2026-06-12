---
title: "unzip / untar one specific file or folder"
date: 2011-09-21
forum: General Help
---

### Post by dragonetti on 2011-09-21
I have an ubuntu VPS which only has terminal SSH connection. I just started linux (ubuntu) and I am even writing scripts now.
 
But now I am hitting a wall again on the un-TAR and un-ZIP subject.
Normal unzip/untar actions go in the correct way, but this is when everything needs to be extracted.
 
But when I only want to extract only 1 specific file or folder (or subfolder) I always end up extracting all the content in it's original path. (which is normal behaviour if the archive is created with full path settings). I read all the man pages about "unzip" and "TAR" I only got to this command, which seemed to work:
 
```

tar -x modsecurity-crs_2.2.1/util/rules-updater.pl -zf modsecurity-crs_2.2.1.tar - C [COLOR=red]/root/somedir/modsec-tar/[/COLOR] --strip-components=2

```
 
But the part in [COLOR=red]red[/COLOR] is a directory that does not exist and even than the command seems to work, this is not correct behaviour. And I could not get any info about "--strip-components".
I could replace ".../util/rules-updater.pl" with the following: ".../util/*" which would extract everything under "util".
 
If someone could provide an example for extracting 1 single specific directory from a TAR and ZIP to a specified folder, that would mean a lot to me.
 
edit: is it possible to use a GREP in combination with unzip/untar, something like this
```

unzip [filename] | grep [filter the files you want /don't want]

```
 
I read something about the -p switch in unzip but I could not get more info about that.

---

### Post by staticd on 2011-09-21
Will look into the tar thingy and tell you if i get any thing. However, grep is not to go. You would use grep to get a single filename from a list of filenames but not to get a single file from a list of files.
Goodluck.

---

### Post by dragonetti on 2011-09-21
ah men, staticd...you're a hero...!
(and thanks for the GREP heads up, I was about spend some time on that one)

---

### Post by dragonetti on 2011-09-21
@staticd
 
I found the awnser here:
[http://www.linuxquestions.org/questions/linux-newbie-8/unzip-untar-one-specific-file-or-sub-folder-904168/#post4477961](http://www.linuxquestions.org/questions/linux-newbie-8/unzip-untar-one-specific-file-or-sub-folder-904168/#post4477961)
 
For unzip:
 
```

unzip modsecurity-crs_2.2.1.zip util/* -d /root/scripttest/test2

```

If you find the correct TAR method, than that's welcome too

---

