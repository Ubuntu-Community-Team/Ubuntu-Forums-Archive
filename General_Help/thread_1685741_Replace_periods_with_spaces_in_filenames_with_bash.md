---
title: "Replace periods with spaces in filenames with bash"
date: 2011-02-11
forum: General Help
---

### Post by kainalu on 2011-02-11
Hello Community,

I was looking at this thread :

[http://ubuntuforums.org/showthread.php?t=1285062](http://ubuntuforums.org/showthread.php?t=1285062)

and would like to build a shell script that would quickly accomplish this. I would like all the periods except the file extension period to be replaced with spaces. I know sed can do it but I haven't figured out how.


Thank you

---

### Post by DaithiF on 2011-02-11
the solution in that thread was to use the perl **rename** command.  why not use that?

---

### Post by sisco311 on 2011-02-11
If you really want to use bash, then you need something like:
```

# exit if the directory doesn't exist
DIRECTORY="/path/to/dir"
cd "$DIRECTORY" || exit 1

# enable nullglob
shopt -s nullglob

for file in *.*.ext; do
  # remove the extention
  newfile="${file%.ext}"
  # replace the periods
  newfile="${newfile//./ }"
  # rename the file
  mv --backup=numbered -- "$file" "${newfile}.ext"
done
```

For details, check out a good bash guide:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by kainalu on 2011-02-11
DaithiF,

The reason I didn't use that command is because, to the best I can tell, has to be told file type in the command (IE JPG) and I wanted to make this into a universal script for all file types, or even mixed file types.

sisco311,

I notice that the script uses ext for extension. Does this have to be changed to the extension desired to work (variable) or is it fine leaving it as it is?

Thank you both!

---

### Post by sisco311 on 2011-02-11
Yes, you have to replace .ext with the actual extention (e.g .jpg) or with a glob .??? 

If you want to make your script universal, you will have to deal with more cases: 
[list]
[*]files whitout an extention, 
[*]files with one or more character long extentions (.c, .ac, .txt, .jpeg ...) and
[*]files with two (or more) extentions (.tar.gz, .tar.bz2 ....)
[/list]

---

### Post by kainalu on 2011-02-11
Cool,

Thank you both!

---

