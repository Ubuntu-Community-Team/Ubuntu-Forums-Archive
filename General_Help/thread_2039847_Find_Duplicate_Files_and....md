---
title: "Find Duplicate Files and..."
date: 2012-08-09
forum: General Help
---

### Post by rhss6-2011 on 2012-08-09
Hello everyone,
I'm starting to really get into shell/bash coding... Some of them are great, some of them not so much. No matter what though when I run into a problem, I usually come here so...

I've been working on a batch of scripts and this new one has me a little stumped. **I would like to use** "**find** /main/path/of/files **-type f**" **to find** any/all **files** that I have on a certain drive/partition.

**While searching** for files would I would like to do is have it **check if** that **file** (name) **has already been found**. Assuming that it does, I want it to **either delete** one **or** if possible, **delete the file** **with** the **lowest** file **size**.

I know that I can find any files with this part of my script:
```
read -p "Please type the path to your backups for de-duplication: " backup_dir
find $backup_dir type -f
```

If I want to find the files and compare it to something else
```
read -p "Please type the path to your backups for de-duplication: " backup_dir
x=$( find $backup_dir -type f )
for y in ´find $backup_dir -type f ´ ;
do
if [ -f $x !== $y ] ;
then
echo "File $x is nothing like file $y
```

But I don't know **how to** make it **search for a file** (name) **that has already been found, and delete the smaller file**.


Any help with this one guys?

---

### Post by Vaphell on 2012-08-09
try this, it sorts the files alphabetically by name and numerically by size (in descending order)
if the file has the same name as the previous one, that means it is equal-or-smaller and is marked for deletion. Test it well before running commented rm.
```
ln=''
dup=0
while IFS=$'\t' read -r -d $'\0' name size path
do
  # print files and mark candidates for deletion with !
  if [ "$ln" = "$name" ]
  then
    del='!'
    ((dup++))
    # uncomment to print rm commands just to be sure, remove echo to perform rm
    # **echo** rm "$path"
  else
    del=' '
  fi
  echo "$del $name | $size | $path"
  ln="$name"
done < <( find "$backup_dir" -type f -printf "%f\t%s\t%p\0" | sort -z -t $'\t' -k1,1 -k2rn,2 )
echo "$dup duplicates found"

```



besides, shouldn't you use some dedicated backup tool like rsync?

---

### Post by rhss6-2011 on 2012-08-10
During a break in school, I wrote this on a sketch pad and I think it will work - I would like to make sure first though.

```
#Make list of files in HOME directory
find /path/to/backup -type f | sort > $HOME/BACKUPS.txt
#Look for Existing entry name of re-found file
z=$( find /path/to/backup -type f | sort )
x=$( grep $HOME/BACKUPS.txt ´basename $z´ )
#Compare file to entry and delete if it exists already
if [ $x == ´basename $z´ ]
then
rm -ok $x
done
fi
```

Do you think that would work? BTW thank you for your coding, I'll try that later, or tomorrow if I get caught up in school work.

---

### Post by Vaphell on 2012-08-10
not really, don't have any *rm* near that script until you debug it, unless you like pain ;-)
```
z=$( find /path/to/backup -type f | sort )
```
z contains the whole output of find, sorted. Echo $z to see. What is supposed the basename of $(find|sort) do?

```
rm -ok $x
```
unquoted variables with potential whitespace inside = breakage.

---

