---
title: "advanced wget useage"
date: 2009-11-22
forum: General Help
---

### Post by chinaCat86 on 2009-11-22
I am downloading files from a list and have a large amount to do. can anyone help me articulate the logic better.

I have a large folder structure of 
/dir/year/date/file.m3u

I have been manually navigating to the folder and 'wget -i file.m3u'
but I do not want to do this thousands of times. is there an easy way to just recursively do this? the logic sound simple, but I am no familiar with working with linux =/ But I am trying to learn.

EDIT: it is not too important becuase of -A *.m3u but file.m3u is always a unique name and structure but extension is always .m3u

EDIT2 SOLVED:
```
 #!/bin/bash
find . -type f -iname *.m3u | while read list; do
  cd $(dirname $list)
    wget -i $(basename $list)
  cd..
done 
```BTW, I am using this to easily download live music from archive.org

---

### Post by chinaCat86 on 2009-11-22
I am not at home so I cannot try it, but alternatively would I be able to include everything in one file and after the url's simply include the dir I want the files saved too?

e.g.

wget -i playlist.m3u

where playlist.m3u:
url.mp3 -o /year/month/day
url.mp3 -o /year/month/anotherday

---

### Post by chinaCat86 on 2009-11-23
Well, adding information in the file list did not work.

Any one have any ideas. :-({|=

---

### Post by koenn on 2009-11-23
man wget

```
Directories:
  -nd, --no-directories           don't create directories.
  -x,  --force-directories        force creation of directories.
  -nH, --no-host-directories      don't create host directories.
       --protocol-directories     use protocol name in directories.
  -P,  --directory-prefix=PREFIX  save files to PREFIX/...
       --cut-dirs=NUMBER          ignore NUMBER remote directory components.
```


which one and how depends on what you're trying to do, of course

---

### Post by falconindy on 2009-11-23
start in your "root" and run this:
```
#!/bin/bash
find . -type f -iname *.m3u | while read list; do
  cd $(dirname $list)
  wget -i $(basename $list)
done
```

---

### Post by chinaCat86 on 2009-11-23
falconindy, thanks that is a great idea.
however, the script is having trouble.

For example.
If I only try to download 1 month at a time it will not goto the proper days.
/July/temp.sh
/july/01/a.m3u
/july/02/b.m3u
when the script tries to navigate to july 2nd it returns dir not found.

---

### Post by chinaCat86 on 2009-11-23
Easy fix.

thank you so much. I know this is not too advanced, but until I learn some shell scripting it is. I need to dedicate some time to that in the future. 

```
#!/bin/bash
find . -type f -iname *.m3u | while read list; do
  cd $(dirname $list)
    wget -i $(basename $list)
  cd..
done
```

---

### Post by falconindy on 2009-11-23
Ahhh right, because all the directories output by the find command are prefixed with a dot (in this case), meaning they're relative paths. Glad I could help.

Shell scripting is insanely powerful (also fun), and something that all Linux users should be comfortable with at some level. You're really missing out if you don't learn a little.

---

### Post by chinaCat86 on 2009-11-23
I know, I finally made the switch from windows about 6 months ago. I am a college student so during the semester I have very little time. I plan to read up a little on shell scripting over the break.

---

