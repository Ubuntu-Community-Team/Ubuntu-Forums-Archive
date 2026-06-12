---
title: "Export list of files/folders"
date: 2009-10-13
forum: General Help
---

### Post by nimajiman on 2009-10-13
Hi all,

I'm wondering if there is a simple way to export a list of the contents of a folder (be it files or folders or some combination) to a spreadsheet, or a format importable into openoffice such as csv or something.

For example, if I open my 'work documents' folder in nautilus which contains 100+ word, excel and powerpoint files, I would like to be able to see a list/spreadsheet containing these file names (and other details if possible) for quick reference and to send to colleagues for their reference also.

Another example: when I open my Home -> Music folder in nautilus, I have about 150 folders within for different artists. I would like to be able to export a list of these folder names to a spreadsheet, again for my own quick reference and also comparison with the music library on my wife's computer.

I hope this makes sense. Anyone know of how to make this possible? I will use the terminal if necessary however a simpler option would be great if there is one.

---

### Post by justleen on 2009-10-13
I'd use something like the following to create variable of the ls -la output, then echo what I need to a .csv file ```

ls -la | while read attr numitems owner group size date name
do 
    echo ${size},${date},${name} >> output.csv 
done
```

Edit: yes, you could use awk or cut to get the fields you want but I find this, in this case, more intuitive since I can "name" each column of the ls -la output.

---

### Post by nimajiman on 2009-10-14
> **justleen said:**
> I'd use something like the following to create variable of the ls -la output, then echo what I need to a .csv file ```

ls -la | while read attr numitems owner group size date name
do 
    echo ${size},${date},${name} >> output.csv 
done
```

Edit: yes, you could use awk or cut to get the fields you want but I find this, in this case, more intuitive since I can "name" each column of the ls -la output.

Thanks for the quick reply. I'm a bit of a newb when it comes to scripting. Would you be able to explain what the commands are doing above? (I know the ls -la part, just not the rest).

I tried running the above as a script and it works, however I don't *always* want date/time information, only file/folder names and sizes (in 'human readable' format if possible). Tried editing the script to change the output but didn't seem to make any progress.

---

### Post by justleen on 2009-10-14
```
 ls -la | while read attr numitems owner group size date name 
```
do a **ls -la**  |  **while read**ing every line, name the columns that are in that line (with arbitrary names..in this case I name all the columns)
```

do 
    echo ${size},${date},${name} >> output.csv 
done

```
echo the specific variables you want to a text file . the >> makes sure it appends to the file ( a single > will recreate the file on each line, leaving you with only the last line in the file)


Basicly, I loop over all the lines with a while statement, name the columns, then echo what I need to a file

The main "advantage" over naming the columns is that you can easily reuse the code (doing a cut involves rewriting the field number you wont.. not hard at all but still)

Say, if you only want the file names and their human-sizes:
```
ls -hla | while read attr numitems owner group size date name
do 
    echo ${size},${name} >> output.csv 
done

```

Offcourse, there are many ways to do this.. since folders are always a fixed size, you may not want to see those.. you could do a find to search for files and then rinse and repeat.
```

find . -type f -exec ls -lh {} \;| while read attr numitems user group size date filename 
do 
       echo $size $filename 
done
```
find in current dir all files. Execute ls -lh on found file (the {} represents the found file). after that its the same as above

---

### Post by slakkie on 2009-10-14
And what about files with spaces?

I would do something with find and stat

```

find . -exec stat -c "User:%U,Group:%G,File%n" {} +

```

Depends what you want kind of information you want to share. See man stat for more information on formatting.

---

### Post by justleen on 2009-10-14
files with spaces??? Who the hell uses files with spaces?? ;)


Files with spaces SHOULD work ok this way...Since all the unnamed columns will be parsed into the last variable name.
thus all the extra "columns" in the filename will be in $filename
( ls -la |while read everything; do echo $everything; done)
```

/media/space/musica/65DAYSOFSTATIC/Hole EP$ find . -type f -exec ls -lh {} \; | while read attr numitems user group size date time filename ; do echo $filename ; done
./01 - Hole.mp3
./02 - Wrong Side of the Tracks.mp3
./03 - The Fall of Math (65dos Remix).mp3
./04 - Betraying Chino.mp3
./05 - No Station.mp3
./06 - Retreat! Retreat! (Mothboy Remix).mp3
./07 - 4 Connection (So Close).mp3
./65dos_hole.jpg

```

Though I immediately will agree that your solution is less code!

---

### Post by slakkie on 2009-10-14
> **justleen said:**
> files with spaces??? Who the hell uses files with spaces?? ;)


Too many people. 

> 
Files with spaces SHOULD work ok this way...Since all the unnamed columns will be parsed into the last variable name.
thus all the extra "columns" in the filename will be in $filename
( ls -la |while read everything; do echo $everything; done)


That I didn't know, or maybe I did, but I hardly use read so I assumed it would break with spaces.

---

### Post by justleen on 2009-10-14
I didn't know I could use a "+" to terminate the -exec! cheers for that one...

To the OP: with all the "find" commands here, one last remark. You might want to include a "-maxdepth 1" in there, otherwise it will go trough all the subfolders it finds..

```
 find . -maxdepth 1 -exec ... 
```

---

### Post by nimajiman on 2009-10-14
Fantastic! Thanks guys, really helpful stuff there.

I have played around some more and this is what I'm using:

> #!/bin/bash
ls -hlQ --time=ctime --ignore=*.*| while read attr numitems owner group size date time name
do 
    echo ${numitems},${name},${date} >> /home/jamin/Desktop/contentslist.csv 
done

find -maxdepth 1 -type f -exec ls -hl --time=ctime {} \;| while read attr numitems owner group size date time name
do 
    echo ${name},${date},${size} >> /home/jamin/Desktop/contentslist.csv 
done

It spits out just folder names first, so I can take just the information I want (ie name and date but no size); then using the find command it looks for just files so I can take filenames, creation dates and sizes. Appends it all to the contentslist.csv file on my desktop.

It's not perfect but I use the delimiter options in openoffice to strip out any remaining information that I don't want (i.e the 'find' command gives output like ./filename1 ./filename2 etc instead of just 'filename1' 'filename2'. Don't know how to make it output file names similar to what ls command does).

I've put the .sh file in my ~/.gnome2/nautilus-scripts folder so now I can just right click inside a folder and voila!

@slakkie I haven't tried it yet in a folder with filenames that have spaces so will see what happens when I do it tomorrow.

Thanks again guys.

---

### Post by slakkie on 2009-10-14
> **justleen said:**
> I didn't know I could use a "+" to terminate the -exec! cheers for that one...

To the OP: with all the "find" commands here, one last remark. You might want to include a "-maxdepth 1" in there, otherwise it will go trough all the subfolders it finds..

```
 find . -maxdepth 1 -exec ... 
```

The exection is done differntly with \; and +

\; is like doing

```

for i in $@ ; do
  echo $i
done

```
where as 

+ is like doing
```

echo $@

```
So less calls :)

@TS

If find add ./ in front of the filename it is because you are searching in ./. 

```

find -exec stat -c "do stuff with %n" | sed -e 's/\.\///g'

```

Will fix the issue for you, another way of fixing it by looking into the whole dir:

```

find /path/to/dir -exec stat -c "do stuff with %n" 

```

Then all the files will be printed as /path/to/dir/filename

The thing you call numitems is actually number of  hard links. Each directory has 2 hardlinks (for a detailed explenation: [http://linuxgazette.net//issue35/tag/links.html](http://linuxgazette.net//issue35/tag/links.html)). The number of hardlinks just tell you how many directories are in there (total -2). It doesn't say anything about the number of files in the directory.

---

### Post by nimajiman on 2009-10-15
> If find add ./ in front of the filename it is because you are searching in ./. 

```
find -exec stat -c "do stuff with %n" | sed -e 's/\.\///g'
```

Will fix the issue for you, another way of fixing it by looking into the whole dir:

```
find /path/to/dir -exec stat -c "do stuff with %n"
```

Then all the files will be printed as /path/to/dir/filename

Ok you lost me a bit here, but again I'll try it and see if I can work out what's going on. I like to understand the commands if I can so it's a bit of a learning curve for me.

> The thing you call numitems is actually number of hard links. Each directory has 2 hardlinks (for a detailed explenation: [http://linuxgazette.net//issue35/tag/links.html](http://linuxgazette.net//issue35/tag/links.html)). The number of hardlinks just tell you how many directories are in there (total -2). It doesn't say anything about the number of files in the directory.

Because I was getting ./filenames instead of "filename" with the find command I was using the '/' as a delimiter in the csv. Therefore to make it line up with the folder-list output from the previous ls command, I just picked an arbitrary attribute (numitems) to include. I am then just hiding that column so it doesn't matter what the value is - although thanks for the explanation.

If I can understand the new find commands you mentioned to get rid of the ./ before the filenames, I'll get rid of the {numitems} as well.

At least for now I've got a workable script so thanks again both of you.

---

### Post by theangler on 2011-04-04
This is an old thread, and perhaps I'm off, but maybe we're over complicating things.  Perhaps simply a line such as:

ls -R -a [directory to list] > [output file]
example: ls -R -a /home/user > ~/output.txt

?

:guitar:

---

