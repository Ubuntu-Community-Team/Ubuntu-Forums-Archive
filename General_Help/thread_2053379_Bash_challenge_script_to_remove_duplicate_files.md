---
title: "Bash challenge: script to remove duplicate files"
date: 2012-09-05
forum: General Help
---

### Post by Statia on 2012-09-05
I used the excellent tool fdupes to find duplicate photos and wrote its output to a file:

```
fdupes -r /home/statia/Pictures > ~/duplicates.txt

```Lines in this file look like this:

```
/home/statia/Pictures/Nevis 2009/img_1789.jpg
/home/statia/Pictures/Unsorted/Canon A520 372.jpg

/home/statia/Pictures/Nevis 2009/img_1853.jpg
/home/statia/Pictures/Unsorted/Canon A520 374.jpg
```I have about 550 duplicates, but my girlfriend more than 10.000, so I'd like to automate the task of removing the duplicates, with a smart script.
The script should take duplicates.txt as input and remove one of each duplicate.
Files can be removed from directories with names like "Unsorted", "backup" and "recovered". Probably easiest to set those names in an variable like $REMOVE_DIR.
Duplicate pairs not in one of those directories can be left untouched for manual removal.
Unfortunately, I am not that great with bash, could anyone give me a hand?

---

### Post by Statia on 2012-09-05
Something like this:

```
#!/bin/bash
# Use a text file with lines of duplicate files to remove one of the duplicates,
# based on the directory the file is in.
# If there is no matching directory, leave duplicate set untouched

$INPUT=~/duplicates.txt
$RM_DIR=~/Pictures/Unsorted
$RM_DIR=~/Pictures/recovered

for i in $INPUT, do 
```But of course, the real magic still has to be put in :-)

---

### Post by dozdozez on 2012-09-05
All right, I have made one script that makes what i think you want.

I haven't tested it properly so you should make some tests before actually using it.

And another advice:  If you have a picture duplicated, in a folder */Unsorted/* and  in a folder */backup/*, this script will remove both pictures, cause it doesn't check anything.

Actually this script doesn't remove anything, instead it creates another script so you can check that everything is ok before procced. This second script won't remove anything either, it will move the duplicated files in a path were you can have them easly removed or recovered.

Before removing your files remember to check that they are the files you really want to remove.

Here is the script:

```

#!/bin/bash
# Use a text file with lines of duplicate files to remove one of the duplicates,
# based on the directory the file is in.
# If there is no matching directory, leave duplicate set untouched
INPUT=duplicates.txt
DIR_BASE="Duplicated_Pictures"
RM_DIR="/Unsorted/|/backup/|/recovered/"
TMP_SCRIPT=remove_dup.tmp.sh
if ! test -f $INPUT ; then 
        echo ERROR!: $INPUT does not exist
        exit;
fi

cat duplicates.txt |gawk -v DIR_BASE="$DIR_BASE" -v RM_DIR="$RM_DIR" \
'
{ 
        if ( match ($0, RM_DIR ) ) {
                DIRECTORIO=$0;
                sub(/[^\/]*$/,"", DIRECTORIO );
                printf ("mkdir -p \"%s%s\" 2>/dev/null;\n", DIR_BASE, DIRECTORIO )
                printf ("mv \"%s\" \"%s%s\" \n",$0, DIR_BASE, $0); 
        } 
} ' > $TMP_SCRIPT              
chmod +x  $TMP_SCRIPT


```

---

### Post by Vaphell on 2012-09-05
i see few minor problems:

avoid all caps names, otherwise you risk overriding some env var - they are allcaps by convention (yes, i have seen someone overwrite PATH and wonder why nothing works in a script)

```
cat file | gawk ... '...'
```
why?
```
gawk ... '...' file
```

```
gawk -v DIR_BASE=$DIR_BASE -v RM_DIR=$RM_DIR
```
changing dir_base or rm_dir to any string containing spaces will blow the script up. Always quote variables.

---

### Post by dozdozez on 2012-09-05
You are right [Vaphell]("http://ubuntuforums.org/member.php?u=347382")

Thanks for advice. I have edited my last post and fixed the quotes issue.

There is no reason for writing cat before awk. I did it just cause i'm used to use awk with the output of other commands...

I will avoid caps names from now on.

---

### Post by steeldriver on 2012-09-05
maybe I'm misunderstanding the duplicates.txt file, but couldn't you just loop over the file, reading pairs of lines (skipping empty lines) and deleting one of them (after double checking that the other exists)? something like

```
#!/bin/bash

while read -r file1; do 
  if [ "$file1" == "" ]; then
    continue
  fi
  while read -r file2; do
    if [ "$file2" == "" ]; then
      continue
    fi
    if [ -f "$file1" ]; then
      echo rm "$file2"
    fi
    break
  done
done < "~/duplicates.txt"

```

---

### Post by dozdozez on 2012-09-05
[steeldriver]("http://ubuntuforums.org/member.php?u=1627500"). Maybe I'm wrong, but I think that your script does not work properly cause:

a) Some files may be repeated more than once, in that case you will have 3 lines. 
b) If a file is repeated, he wants to remove the one in a subdir called "Unsorted", "backup" or "recovered, not just the second. 
For example in this situation:

/home/statia/Pictures/Backup/Canon A520 372.jpg
/home/statia/Pictures/Nevis 2009/img_1789.jpg /home/statia/Pictures/Unsorted/Canon A520 372.jpg

[Statia]("http://ubuntuforums.org/member.php?u=1710023") would like to keep /home/statia/Pictures/Nevis 2009/img_1789.jpg and remove the other two. Your script wolud keep the first one, remove the second, keep the third, remove the next file....

and in a situation like this: 

/home/statia/Pictures/Backup/Canon A520 372.jpg
/home/statia/Pictures/Nevis 2009/img_1789.jpg

Your script would remove the second file, instead of  the first one.

My script would fail in a situation like this one:

/home/statia/Pictures/Backup/Canon A520 372.jpg
/home/statia/Pictures/Unsorted/Canon A520 372.jpg

because it would delete both files. I'm not sure if this is a possibility. So i warned Statia.

---

### Post by Vaphell on 2012-09-05
awk has one feature that could prove useful - one can define RS as "\n\n" so these blocks become records with lines as fields and it would be rather easy to navigate using i in 1..NF range ($i)

```
$ echo $'a\nb\n\nc\nd\ne'
a
b

c
d
e
$ echo $'a\nb\n\nc\nd\ne' | awk 'BEGIN { RS="\n\n";}
                                       { $1=$1; printf( "[%s] ", NF); for(i=1;i<NF;i++) printf("%d:%s ",i,$i); printf("%d:%s\n",NF,$NF); }'
[2] 1:a 2:b
[3] 1:c 2:d 3:e

```

i don't think that bash can use arbitrary string as a record separator but similar effect of blocks separated by empty lines can be achieved
```
do_something_with_array()
{
  for(( i=0; i<${#f[@]}; i++))
  do
    echo $i ${f[$i]}
  done
  echo "--------";
}

f=()
while read l
do
  if [ -z "$l" ]
  then
    do_something_with_array
    f=()
  else
    f+=( "$l" )
  fi
done <<< $'a\nb\n\nc\nd\ne'
do_something_with_array


output:
0 a
1 b
--------
0 c
1 d
2 e
--------

```

---

### Post by Statia on 2012-09-09
Hey guys,

I just got back from a short trip and see that in my absence you have been busting your brains over my question (shameless request). Thanks a lot!
Tomorrow I'm going to read it with full attention and experiment with it. I'll keep you posted and appreciated the effort!

---

### Post by Scooby-2 on 2012-09-28
Hi Statia,

Be careful! I am in a similar situation to you with around 8,500 photos for which I used unreliable software to synchronize to an external disk/NAS server. Realizing this, I used to make ad hoc copies of everything, resulting in multiple copies of all but the most recent files, thinking I'll sort it out one day. That day arrived a week or so ago...

I used fdupes to test the finding of duplicates and it reported hundreds of false matches. (Maybe my version? I'm on version 1.50-PR2 of fdupes on Ubuntu 10.04LTS.) The reason for the false "duplicates" was because I use Picasa to tag pictures and the tags are embedded in the jpg file itself. I had spent hours tagging photos in one of my backups using Picasa but fdupes unfortunately doesn't see the changes in the file or the difference in the date of last access. I proved this by doing an MD5 sum on the files - which showed the differences. If I'd relied on fdupes I risked wasting hours of tagging time. So I decided to write my own script.

My approach is to have a 'master copy' of the photos which is the one on which the Picasa tagging was done and also where my camera saves photos - in a directory called Canon in sub-directories named after each day in the format YY_MM_DD.

A copy of photos to be checked can reside anywhere in the file system and the script runs from there, and creates its log files there. The concept is as follows:


[LIST=1]
[*]Read all the files in the master directory and run md5sum against each one. Create a list of the file names and their corresponding md5 hash value.
[*]Delete all ZbThumbnail.info, picasa.ini and Thumbs.db files (as the master directory has these - they will be updated when the appropriate program is run and changes are made anyway).
[*]Read all files down from the current, local (to be checked) directory and check each file name to see if it exists in the master list.
[*]If a match is found it runs md5sum against the local file.
[*]Compare this md5 with that stored against the one in the master list. If it matches, the script deletes the local file and logs the action in a log of deleted files. Exit the loop immediately and go to the next file.
[*]If the local md5 does not match the master md5 it leaves it but adds and entry to a log of duplicate names found (but the file is different) for later processing.
[*]If step 3 did not find a match it adds an entry to a "no-match-found" log.
[*]Loop to step 3.
[*]Extract the md5 hash for each file for which no matching file name was found. Matches are deleted, adding an entry to the log of deleted files.
[*]Run a similar check on files in the log of files which can be deleted (see below).
[*]Delete all empty directories.
[*]Parse each entry in the log of matching file names but where the files have a different checksum and display each copy side by side using the maximum width allowable by my screen (512px as my max res is 1024 x 768 px ).
[*]For each pair, offer to delete the local file, overwrite the master file or skip and move on to the next pair. Appropriate log files are updated. This is important when deleting, as if the same file is encountered again, a check can be run against the deleted files' md5 hash so it can be deleted without the need for prompting again (see step 10). for this I use a log called selected_for_deletion.log,
[/LIST]
I have almost finished my script writing using this concept, I have tested my scripts for steps 1 to 11 and 12 is in progress. At the moment my "script" is in three parts!

When the script is running through steps 3 to 8 it first prints the number of files it found in the current directory, what file it's currently processing and how many are left so you know where it is. On my prehistoric AMD Sempron laptop it took about 70 minutes to process a backup of 5100 photos and videos but these were all on an external USB hard drive.

With this approach there are pros:

[LIST=1]
[*]My camera creates JPG, MOV and THM files and all of these are checked.
[*]It's extremely accurate as the matching is done using md5 hashes.
[*]It tells you where it's up to.
[/LIST]
and cons:

[LIST=1]
[*]My script does not cater for more than one duplicate of any file, but in my situation this is not an issue. (However, it can always be run again on the same backup....)
[*]It's not fast.
[/LIST]
The bottom line is not to trust fdupes; carefully plan your requirements and thoroughly test what you are planning to implement on copies (of copies) first!

Hope this helps.

---

### Post by Statia on 2012-09-28
Wow! Sounds really impressive and useful! I hope you will share your script with us when you have it finished. Thanks for your input!

---

### Post by Scooby-2 on 2012-09-30
> I hope you will share your script with us when you have it finished.

Will do... lots of testing is the order of the day for me right now.... :neutral:

---

### Post by Scooby-2 on 2012-11-28
I haven't forgotten about this. I have had little time lately, but I still do have thousands of duplicates to sort out. I only have 2 PCs but an OS upgrade and a disk failure have kept me busy. When I finally sort out my own duplicate photos I will post the script(s) back here.

---

### Post by Statia on 2012-11-29
Thanks for not forgetting! I haven't come round to sorting out my duplicates either, but it is still on my TO-DO list.

---

### Post by Rebelli0us on 2013-01-31
Dangerous, I wouldn't do it.  Duplicates can be, file, File, file(1), _file, etc, and still have different content.

You can use an image viewer app like xnview, search & find all image files in a partition and then sort them alphabetically. Duplicate names will show up together.

---

### Post by Impavidus on 2013-01-31
What about writing a few bash lines to iterate over all files, calculate a hash sum for each of them and generating a table with lines like```
<hash> /path/to/file
```Next use **sort** to sort according to hash value and pipe the result into **uniq -d -w<some number>**. This will give you a list of the duplicates. Iterate through that list and use **rm** to delete the duplicates. **read** will read the file one line at a time and put each line in a bash variable, delete the hash from the line and give the result to rm.

(If some files are present three times you have to do this again, as this will only remove one duplicate. The only risk is a hash collision, but you may want to check the duplicates list first.)

---

### Post by prodigy_ on 2013-01-31
Not thoroughly tested but seems to work:
```

#!/urs/bin/env python

import os
import hashlib

# More advanced version of this function here:
# http://www.joelverhagen.com/blog/2011/02/md5-hash-of-file-in-python/
def md5Checksum(file_path):
    with open(file_path, 'rb') as open_file:
        file_data = open_file.read()
        check_sum = hashlib.md5(file_data)
    return check_sum.hexdigest()

# Working folder. Can be defined by a command line parameter,
# e.g: root_dir = argv[1]
root_dir = '/home'

all_files = {}
uniq_files = {}

# Loop through all files in the working folder and its subfolders:
for root, folders, files in os.walk(root_dir):
    for file_name in files:
        # Get absolute path:
        file_path = os.path.join(root, file_name)
        # Exclude symlinks:
        if not os.path.islink(file_path):
            # Calculate md5 hash:
            file_md5 = md5Checksum(file_path)
            # Get file size:
            file_size = os.stat(file_path).st_size
            # This dictionary will contain all files:
            all_files[file_path] = file_md5, file_size
            # This dictionary will contain all unique files,
            # including those that have duplicates:
            uniq_files[file_md5, file_size] = file_path

# Redundant files = all files - unique files:
dup_files = set(all_files.keys()) - set(uniq_files.values())
for file_path in dup_files:
    print file_path

```

Outputs the list of redundant files while preserving **all** uniques. E.g. if there are two identical files (same size AND same hash), only one of them will be in the output.

---

