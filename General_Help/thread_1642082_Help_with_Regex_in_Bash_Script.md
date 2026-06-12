---
title: "Help with Regex in Bash Script"
date: 2010-12-09
forum: General Help
---

### Post by jfluckey on 2010-12-09
I am writing a bash script to rename groups of files (anime primarily).  An example file name is "[SGGK]_Bleach_-_279_(1280x720_h264_AAC)_[E8976D84].mkv" and I would like the script to name it "Bleach - 279.mkv".  The script is to dissect the file name and reconstruct it. Once the results of the "echo" produce the correct file name, I will replace the "echo" line with a "mv" line.

My problem is in the definition of "Strip".  I want to pull out the "279" in the example file name above, but I can't guarantee that the location won't change from file to file and that there will always be (3) numbers (e.g. 83 instead of 279).  I was trying to use the preceding and ending "_" as a boundary, but I don't know how to do it.  If anyone can tell me what needs to replace '.*_\([0-9]+\)_' to get my desired result, I would greatly appreciate it.

```
#! /bin/bash
echo "Enter the name of the show: "
read Name

Files=`ls -p | grep -v "/" | grep -v "\.sh"`  # ls -p appends a "/" to end of directories, grep -v "/" excludes names with /.

  for count in $Files
    do
      Ext=`expr match "$count" '.*\(...\)'`
      Strip=`expr match "$count" '.*_\([0-9]+\)_'`
    echo "$Strip"
        if [ "$Strip" == "" ]; then
          echo "$count is not going to be renamed"
        else
          echo "$count is going to be renamed "$Name - $Strip.$Ext""
        fi
    done

```

---

### Post by papibe on 2010-12-11
Did you solve your problem?

Having faced similar rename-challenging script, I would recommend using a "renamer" program. Look into the repositories. I use and recommend pyRenamer.

Nevertheless, you can also use sed to rename files:
```
...
for file in $list
do
    newfile=`echo "$file" | sed 'regular expression'`
    mv "$file" "$newfile"
done
...
``` 
Regards.

---

### Post by katykat on 2010-12-12
This is probably best done in Perl with the Split command.
Not being an expert, I would recommend this question on perhaps the newbie section of the Perlmonks forum....

---

### Post by Crusty Old Fart on 2010-12-14
> **jfluckey said:**
> I am writing a bash script to rename groups of files (anime primarily).  An example file name is "[SGGK]_Bleach_-_279_(1280x720_h264_AAC)_[E8976D84].mkv" and I would like the script to name it "Bleach - 279.mkv".  The script is to dissect the file name and reconstruct it. Once the results of the "echo" produce the correct file name, I will replace the "echo" line with a "mv" line.

My problem is in the definition of "Strip".  I want to pull out the "279" in the example file name above, but I can't guarantee that the location won't change from file to file and that there will always be (3) numbers (e.g. 83 instead of 279).  I was trying to use the preceding and ending "_" as a boundary, but I don't know how to do it.  If anyone can tell me what needs to replace '.*_\([0-9]+\)_' to get my desired result, I would greatly appreciate it.

```
#! /bin/bash
echo "Enter the name of the show: "
read Name

Files=`ls -p | grep -v "/" | grep -v "\.sh"`  # ls -p appends a "/" to end of directories, grep -v "/" excludes names with /.

  for count in $Files
    do
      Ext=`expr match "$count" '.*\(...\)'`
      Strip=`expr match "$count" '.*_\([0-9]+\)_'`
    echo "$Strip"
        if [ "$Strip" == "" ]; then
          echo "$count is not going to be renamed"
        else
          echo "$count is going to be renamed "$Name - $Strip.$Ext""
        fi
    done

```

Oh man! ... You were so close. In order for the plus sign (+) to work the way you intended within an expr statement, it must be escaped using a backslash (\).
```

[SIZE=4]**[COLOR=Red]~~~ change this: ~~~[/COLOR]**
Strip=`expr match "$count" '.*_\([0-9]**[COLOR=Red]+[/COLOR]**\)_'`

**[COLOR=Green]~~~ to this: ~~~[/COLOR]**[/SIZE]  [SIZE=4]
Strip=`expr match "$count" '.*_\([0-9]**[COLOR=Green]\+[/COLOR]**\)_'`[/SIZE]

```

---

### Post by tkoco on 2010-12-14
Great script. Thank you!  And to "Crusty Old Fart", thanks for the fix to the script.

> **jfluckey said:**
> I am writing a bash script to rename groups of files (anime primarily).  An example file name is "[SGGK]_Bleach_-_279_(1280x720_h264_AAC)_[E8976D84].mkv" and I would like the script to name it "Bleach - 279.mkv".  The script is to dissect the file name and reconstruct it. Once the results of the "echo" produce the correct file name, I will replace the "echo" line with a "mv" line.

My problem is in the definition of "Strip".  I want to pull out the "279" in the example file name above, but I can't guarantee that the location won't change from file to file and that there will always be (3) numbers (e.g. 83 instead of 279).  I was trying to use the preceding and ending "_" as a boundary, but I don't know how to do it.  If anyone can tell me what needs to replace '.*_\([0-9]+\)_' to get my desired result, I would greatly appreciate it.

```
#! /bin/bash
echo "Enter the name of the show: "
read Name

Files=`ls -p | grep -v "/" | grep -v "\.sh"`  # ls -p appends a "/" to end of directories, grep -v "/" excludes names with /.

  for count in $Files
    do
      Ext=`expr match "$count" '.*\(...\)'`
      Strip=`expr match "$count" '.*_\([0-9]+\)_'`
    echo "$Strip"
        if [ "$Strip" == "" ]; then
          echo "$count is not going to be renamed"
        else
          echo "$count is going to be renamed "$Name - $Strip.$Ext""
        fi
    done

```

---

### Post by Crusty Old Fart on 2010-12-14
> **tkoco said:**
> Great script. Thank you!  And to "Crusty Old Fart", thanks for the fix to the script.

Ahhhh...Thank you for the thanks...makes me feel good...appreciate it.

---

### Post by jfluckey on 2010-12-25
Crusty: Thanks so much for this!!!!!

Sorry it took me a while to respond, I haven't checked this thread in a while.  It works great now.  Below is my full code.  It asks if the user for name of the show and the type of naming configuration (TV shows follow the seasonal naming convention ...S01E01... and anime follows the continual convention ...001...).  Then it renames all files based on those inputs ignoring subdirectories and certain extensions of files.   All of the files in your your working directory must be of the same show!

```
#! /bin/bash


echo "Enter the name of the show: "
read Name

echo "Is this a season or continual type series [s,c]?"
read Type


Files=`ls -p | grep -v "/" | grep -v "\.sh"`  # ls -p appends a "/" to end of directories, grep -v "/" excludes names with /.


if [ "$Type" == "s" ]; then
  for count in $Files
    do
      Ext=`expr match "$count" '.*\(...\)'`  
      Strip=`expr match "$count" '.*\([Ss][0-9][0-9][Ee][0-9][0-9]*\)'`
      Strip2=`echo $Strip | tr '[a-z]' '[A-Z]'`
        if [ "$Strip" == "" ]; then
          echo "$count is not going to be renamed"
        else
          echo "$count will be renamed to "$Name - $Strip2.$Ext""
          #mv $count "$Name - $Strip2.$Ext"   #Remove comment to actually rename file.  Leave comment in to test so files don't mistakenly get renamed or overwriten.
        fi
    done
else 
  for count in $Files
    do
      Ext=`expr match "$count" '.*\(...\)'`
      Strip=`expr match "$count" '.*_\([0-9]\+\)_'`
    echo "$Strip"
        if [ "$Strip" == "" ]; then
      echo "$count is not going to be renamed"
        else
      echo "$count is going to be renamed "$Name - $Strip.$Ext""
      #mv $count "$Name - $Strip.$Ext"   #Remove comment to actually rename file.  Leave comment in to test so files don't mistakenly get renamed or overwriten.
        fi
    done
fi


#rm rename.sh  # Remove the script from the directory when finished 
```

---

### Post by Crusty Old Fart on 2010-12-25
> **jfluckey said:**
> Crusty: Thanks so much for this!!!!!

Sorry it took me a while to respond, I haven't checked this thread in a while.  It works great now...
You're mighty welcome. Please don't forget to mark this thread as [SOLVED]. Only you, as the original poster (OP) can do it (see the link in my signature below).

Merry Christmas,

Crusty

---

