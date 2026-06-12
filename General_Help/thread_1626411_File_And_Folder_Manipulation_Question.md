---
title: "File And Folder Manipulation Question"
date: 2010-11-20
forum: General Help
---

### Post by alphaamanitin on 2010-11-20
Hey Guys,

I have a annoying problem I am hoping Ubuntu can solve.  I dual boot a computer from separate hard drives in Windows XP and Ubuntu 10.04.  Here is the deal:

On my windows drive I have a folder that is filled with folders inside folders packed full of files in all the folders.  There is a 100% possibility that I have multiple copies of any file in multiple locations.  Is there any nice command or program to move all the files in all the folders to one central folder and in any way get rid of the multiple copies?  Also, how do I compare to files that may or may not have the same name, but otherwise be identical to see if they are identical?

Thanks Forum Friends.

AlphaA

---

### Post by asmoore82 on 2010-11-20
You could md5sum all of the files - which calculates a 'fingerprint' of the file.
In a closed lab setting is it possible to engineer 2 different files with the same md5,
But in the wild it is mind-bogglingly, astronomically impossible for such files to exist.

You could run something like this on that folder, I'm using my "Pictures" as an example:
```
find Pictures -type f -exec md5sum {} \; | tee filelog.txt
```
^and then go out for a long Lunch! - it should take a while.

You then have "filelog.txt" in your $PWD and can find duplicates like this:
```
cat filelog.txt | cut -c-32 | sort | uniq -d
```

This isn't extremely useful so far because it will only show you
the duplicate fingerprints, not the actually filenames.

To get the filenames, you can "backfeed" the same command into a loop
that will retrieve the filenames back from the very same file..
```
cat filelog.txt | cut -c-32 | sort | uniq -d |
while read md5
do
grep "^$md5" filelog.txt
done | tee duplicates.txt
```
^note the dangling pipe on the 1st line.

And finally, you have "duplicates.txt" ~ your duplicate files.

---

### Post by alphaamanitin on 2010-11-23
Okay, but that still leaves me with the problem of migrating all these files inside folders insider folders, ad nauseum, and the issue of deleting all duplicate files.  Then I also have the problem of removing the duplicate files.  I guess that could be done by using the names in the duplicate file as a list to delete, but I don't know how to read that list into BASH and tell it to delete the files.  Also, what is $PWD?  I am not that great in BASH, I know enough to follow, not to lead.  And when you say run this on the folder, how would one go about that?

Thoughts?

AlphaA

---

### Post by nothingspecial on 2010-11-23
$PWD is your current working directory ie the folder you are in at the moment, which should be the parent folder of all the folders and files that you want to go through.

You run the first find command in that folder. find will look through all the sub folders by default.

---

### Post by alphaamanitin on 2010-11-24
Okay, that is what I thought.  But still, how do I move all the files in sub folders to the central folder?

AlphaA

---

### Post by nothingspecial on 2010-11-24
If you issue this command from the wrong directory you will completely hose your system.

Let me say that again

[SIZE=4][COLOR=Red]If you issue this command from the wrong directory you will completely hose your system.[/COLOR][/SIZE]


Ok.
```

find . -type f -exec mv '{}' ./ \;

```
This will move every file in every subdirectory of the directory you are in to $PWD

So, if you have

D1 and in that you have

D2 and D3

And in D2 you have D2A and D2B

After you issue that command, every file in any of those directories will be in D1.

I`m explaining this slowly, because this could be termed a malicious command.

If you have a lot of music, all arranged neatly in artist and album directories and you did that from ~/Music, you would have a mess.

If you did it from ~ you would have a huge mess.

If you did it from / your system would be broken beyond repair.

There are a couple of modifications you can make depending on what it is exactly that you want. From the mv man page
```

       -f, --force
              do not prompt before overwriting

       -i, --interactive
              prompt before overwrite

       -n, --no-clobber
              do not overwrite an existing file
```

put which ever option you would like after the mv bit of the original command. eg

                                                
```
find / -type f -exec mv [COLOR=Red]-i [/COLOR]'{}' ./ \;
```

Make sure you only do this from the parent directory of all your sub directories with all the files in.

---

### Post by alphaamanitin on 2010-11-24
Perfect.  This is exactly what I need to do.  Now before I actually do this process I have one last question.  Is there anyway to modify asmoore82's information so that after I find all the duplicate files (which may or may not have the same name, but contain the same info) to automatically remove or combine the files so I have only unique files left in my parent directory and all the sub directories.  

After that I want to run the command giving by nothingspecial to move all the files to the parent directory, the $PWD.  

Sorry this thread is expanding even though I have been giving GREAT responses.  I just want to make sure that I have everything theoritcially in place before I start running these commands.  I will update with results of how this worked after I try it.

Thanks guys,

AlphaA

---

### Post by alphaamanitin on 2011-03-22
> **asmoore82 said:**
> You could md5sum all of the files - which calculates a 'fingerprint' of the file.
In a closed lab setting is it possible to engineer 2 different files with the same md5,
But in the wild it is mind-bogglingly, astronomically impossible for such files to exist.

You could run something like this on that folder, I'm using my "Pictures" as an example:
```
find Pictures -type f -exec md5sum {} \; | tee filelog.txt
```^and then go out for a long Lunch! - it should take a while.

You then have "filelog.txt" in your $PWD and can find duplicates like this:
```
cat filelog.txt | cut -c-32 | sort | uniq -d
```This isn't extremely useful so far because it will only show you
the duplicate fingerprints, not the actually filenames.

To get the filenames, you can "backfeed" the same command into a loop
that will retrieve the filenames back from the very same file..
```
cat filelog.txt | cut -c-32 | sort | uniq -d |
while read md5
do
grep "^$md5" filelog.txt
done | tee duplicates.txt
```^note the dangling pipe on the 1st line.

And finally, you have "duplicates.txt" ~ your duplicate files.

-BUMP-

Okay, I want to do this this weekend.  But, after this step, and before the step of moving all the files to one directory I need to delete all the duplicate files.  Or would it be simpler to move them all over, with the -n option (not over right existing files) and then delete the duplicate files?  I would really like help with this.  Again, the problem is I have a folder containing many sub directories and files that may be the same, except for the file name, and other files that have the same file name but are not the same.  I want to remove all files that are the same and move all the files into one directory with no sub directories.  Thanks to the great answers I know how to do all but the deletion of the files, please advise.  

Thanks,

AlphaA

---

### Post by alphaamanitin on 2011-03-30
Bump

---

### Post by alphaamanitin on 2011-04-05
-BUMP-

Some one knows how, I know it.  how do I feed the file containing the name of all the duplicate files back through the command line in a loop to delete all the duplicate files? 

AlphaA

---

### Post by nothingspecial on 2011-04-05
Scrub that, it will delete both files, sorry. I'll get back to you

---

### Post by nothingspecial on 2011-04-06
As far as I can tell, and bear in mind I can't replicate your exact situation, duplicates.txt will contain a list of files with the duplicates next to each other. So to use that list you need to remove every other line (so you keep one of the duplicated files), and remove the md5 from the begining of the line.

```
IFS=$'\n'; sed  'n;d; ' duplicates.txt | sed 's/^\w*  //g' | while read f; do echo "$f"; done
```

To delete the files change echo to rm

That ought to accomplish it but you are going to have to test it. All I have done is copy a few directories into different subdirectories. That gives me the exact same files as duplicates. Like I said when I run the commands to get to duplicates.text, the duplicates are one after another. I don't know for sure that will be the same for you with different file names.

I'll say that again.
[COLOR="Red"]
DON'T DO THIS UNTILL YOU ARE SURE IT WILL WORK.[/COLOR]

I'd wait for someone who is better at this than me before you finally do it.

(Where's Sisco or DaithF when you need them?)

---

### Post by alphaamanitin on 2011-04-06
Thanks for the replies, I think I will do as you suggest and wait until I get a new response.

Thanks,

AlphaA

---

### Post by nothingspecial on 2011-04-06
Sorry to keep coming back every few hours.

The above post will only work if you only have one duplicate (ie two files the same only) it will fail if any file has more than one duplicate.

So for now you need to compare the beggining of each file in duplicates.txt.

As you want everything to end up in the same directory in the end anyway place every duplicate in one more directory. So the whole thing step by step. Asmore82's instructions to find all your duplicates.......

First of all cd into the parent directory

```
cd directory
```

Change directory for the path to your directory. This next command will identify the md5 of every file in every directory within the one you are in.

```
find Pictures -type f -exec md5sum {} \; | tee filelog.txt
```

Generate a file containing every duplicate

```
cat filelog.txt | cut -c-32 | sort | uniq -d | while read md5; do grep "^$md5" filelog.txt; done | tee duplicates.txt
```

Now we have a list of all the duplicates we'll put them in their own directory so we can't mess anything else up.


Make a directory

```
mkdir mytmp
```

move all duplicate files to mytmp

```
IFS=$'\n'; sed 's/^\w*  //g'  duplicates.txt | while read f; do mv "$f" mytmp; done
```

No we want to delete all the duplicates and leave only one copy of each file.

Compare the md5s again and make a new list with the new path to the new directory.

```
find mytmp -type f -exec md5sum {} \; | tee log.txt
```

Sort them and make a list of only one instance instance of each file so we can keep that file. Also make a folder to put them in.

```
mkdir keepers
```

```
sed 's/  .*$//g' log.txt | sort | uniq | while read f; do grep -m1 "$f" log.txt ; done | tee final.txt
```

Then move each instance of one file into the keepers folder

```
IFS=$'\n'; sed 's/^\w*  //g'  final.txt | while read f; do mv "$f" keepers; done
```
 
Then remove the leftover duplicates and all the files we have created

```
rm -r mytmp
``````

rm final.txt log.tx duplicates.txt filelog.txt

```

Then move all the files in all the directories into the one we are in. [COLOR="Red"]Remember how dangerous this is[/COLOR].
```

find . -type f -exec mv '{}' ./ \;
```

Job done :)
That should work. Someone better at bash than me could probably do it in a couple of lines, but I'm a fishmonger not a programmer :P

---

### Post by DaithiF on 2011-04-07
Hi,
just a couple of variations on the approach above.  
1. my approach would be to copy (rather than move) the unique files out of the source tree and into a destination directory.  once you're happy that you have a complete set in the destination then you can just delete the entire source directory.  And this means you can afford to get it wrong multiple times while trying things out ... just delete the destinatation contents and try again :)

2. once you have the filelog.txt with md5sums for all the files, what you really want (I think) is a single path to each unique md5sum, in order to copy that file to the destination, ignoring all the duplicates.

(this assumes that if you have two files with identical contents but with different names that you don't care which of those two files you copy (and therefore which of the two filenames you end up with in the destination.  e.g. if you have:
dir1/fileabc
dir2/filexyz
you may get either fileabc or filexyz in your destination, but you (hopefully) don't care which.

If this assumption works for you then get the md5sums into the filelog.txt as before.  then to get unique paths do you can use:
sort -k1,1 -u filelog.txt 
which says sort the file using only the first field as the key, and only return the unique instances of that key (where there are multiple instances of the key you just get the first)

To illustrate, for me, if a simplified filelog.txt contains:
```
6a5fb9ebd6c8ea7efb53d071053ef778 *./dir1/file withspace
6a5fb9ebd6c8ea7efb53d071053ef778 *./dir1/file1
2d4c27e64c3e974180f6597103ff721e *./dir1/file2
6a5fb9ebd6c8ea7efb53d071053ef778 *./dir2/file1
543234ab485ff65090fb1418a4592653 *./dir2/file2
```then sort -k1,1 -u filelog.txt gives me:
```
2d4c27e64c3e974180f6597103ff721e *./dir1/file2
543234ab485ff65090fb1418a4592653 *./dir2/file2
6a5fb9ebd6c8ea7efb53d071053ef778 *./dir1/file withspace

```once you have that, its just a case of copying those files, with the slight wrinkle that you should check if a file with the same name already exists in the destination directory, and if so, then create a new filename (e.g. with an increasing numeric suffic .0, .1, .2, etc) to avoid overwriting the existing.

so something like this:
```
dest=/path/to/destination
sort -k1,1 -u filelog.txt | while read md5 path
do
  path=${path#\*}    # strip off leading '*' character
  file=${path##*/}    # get filename 
  if [[ -e "$dest/$file" ]]; then 
     suffix=0
     while true
     do
       if [[ -e "$dest/$file.$suffix" ]]; then
         suffix=$((suffix + 1))
       else
         file="$file.$suffix"
         break
        fi
      done
   fi
   cp "$path" "$dest/$file"
done

```

---

### Post by nothingspecial on 2011-04-07
Thankyou DaithiF

---

### Post by alphaamanitin on 2011-04-13
AWESOME!  I'll give this a shot the next time I have free time.  PhD grad student so not much free time.  You are definitely right about this way allowing me multiple attempts DaithiF.  

Thanks to every one who responded, this is such a great thing to know actually.    Will mark as solved after I test it.

AlphaA

---

### Post by alphaamanitin on 2012-01-22
Well, hate to bring this thing back up.  Never got around to it because the computer crashed and I spent a long time getting it back together.  Now that it is I will give it a shot.  I'm going to move the entire directory I want to work on onto a SD card and work on that.

AlphaA

---

