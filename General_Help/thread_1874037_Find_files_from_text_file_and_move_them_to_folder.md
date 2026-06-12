---
title: "Find files from text file and move them to folder"
date: 2011-11-02
forum: General Help
---

### Post by KLStringer on 2011-11-02
I have a text file of about 1000 recordings that I need to find & make a copy of. I know I can use the find command and pass it a cp command I just don't know how to pass find the list of file names from the text file.

```
find /home/*****/recordings/%file_list.txt% -execdir cp {} /home/temp \;
```

Any help is much appreciated, thanks in advance.

---

### Post by KLStringer on 2011-11-02
I know the code above isn't right I think I need to do something like:

```
find < /home/*****/recordings/%file_list.txt% /home/*****/recordings/* -execdir cp {} /home/temp \;
```

---

### Post by Vaphell on 2011-11-02
does that file consists of file names or full paths?

try this
if you have full paths in that file
```
while read file do; cp "$file" /home/temp; done < /home/whatever/recordings/%file_list.txt%
```

names only
```
while read file do; find /home/whatever/recordings -name "*$file" -exec cp "{}" /home/temp \; ; done < /home/whatever/recordings/%file_list.txt%
```

---

### Post by KLStringer on 2011-11-02
The file only has the file names no pathing as there are multiple sub-directories under recordings that the files could be in. When I try the second line of code for just file names I get:

```
 -bash: syntax error near unexpected token 'done'
```

---

### Post by KLStringer on 2011-11-02
I changed 
```

while read file do; find /home/whatever/recordings -name "*$file" -exec cp "{}" /home/temp \; ; done < /home/whatever/recordings/%file_list.txt%
```

to

```

while read file do; find /home/whatever/recordings -name "*$file" -exec  cp "{}" /home/temp \; done <  /home/whatever/recordings/%file_list.txt%
```

and I don't get the syntax error it puts me at a > prompt and just sits there.

---

### Post by Vaphell on 2011-11-02
crap, ; should be before do, not after :)

```
while <stuff>; do <cmd>; <cmd2>; ... done < input_file
```

---

### Post by KLStringer on 2011-11-02
Still the same result returns me to a > prompt

---

### Post by Vaphell on 2011-11-02
but did you restore that additional ;?
\; is for exec part, you need another to end find as a whole.
alternatively you can write a multiline script with that stuff and avoid semicolons altogether.

```
#!/bin/bash
while read file
do
  echo "$file"
  find ...
done < input.file
```

---

### Post by KLStringer on 2011-11-02
Added it back in and it runs, nothing was copied but that could be because the files aren't there going ot add in a file name that I know is there and run it again.


EDIT: added the names of 3 files that I know are in the recordings folder and they still were not copied to /home/temp

---

### Post by Vaphell on 2011-11-02
go with the multiline script, add few echo commands here and there to print out value of $file or whatever, so you can track the problem down.

edit:
exec cp is a secondary issue here, does the find command without exec part print out the names of these files?

```
find <dir> -name "*name.ext"
```

---

### Post by KLStringer on 2011-11-02
OK made a copy.txt script in it I have 

```

while read file
do 
echo "$file"
find /home/**/recordings -name "*$file" -exec cp "{}" /home/temp 
done < /home/**/recordings/missing_files.txt

```

and it reads the file and for each file name it gives an error and nothing is copied, even the files that I know are there.
```
find: missing argument to '-exec'
```

---

### Post by Vaphell on 2011-11-02
while multiline script removes the need to separate the commands with ;, you still need that \; for exec - it tells find where exec part ends

---

### Post by KLStringer on 2011-11-02
Ok added the \; back in and it prints all the file names on the screen but nothing is copied over to temp

```

while read file
do 
echo "$file"
find /home/**/recordings -name "*$file" -exec cp "{}" /home/temp \;
done < /home/**/recordings/missing_files.txt

```I changed the echo "$file" line to echo "$file" > /home/temp/echo.txt as it was scrolling off the screen to fast to read what it was saying. When I check the file all it has in it is the name of the last file in the missing_files.txt file.


EDIT: I may not have saved the script after commenting out the -exec part because now it doesn't print anything to the screen, it creates the echo.txt file but still nothing is copied over.

EDIT2: It stopped printing to the screen because I changed the echo line to output to a file, still doesn't copy any files over

---

### Post by Vaphell on 2011-11-02
when you redirect output to file you can either overwrite it with > or append to it with >>
you used > so each loop iteration overwrote your test output file.

add -v parameter (verbose) to cp command so you get a visual clue in case something is being copied (cp -v "{}" /home/temp)

---

### Post by KLStringer on 2011-11-02
*Homer* 
D'OH!
*/Homer*

I forgot that the /home/**/recordings "folder" is a link to a different location and I don't think find was following the link so I've changed the pathing and rerunning, fingers crossed that solved the problem.

---

### Post by KLStringer on 2011-11-03
I let it run over night and it only read 2 file names out of 4351 in the file, there is a lot of recordings to search through though (about 6.5TB) but can't imagine it would only make it through 2 in 24 hours.

```

while read file
 do
  echo "$file" >> /home/temp/echo.txt
         find /media/recordings -name "*$file" -exec cp -v "{}" /home/temp \;
  done < /media/recordings/HarpUMGMissing.txt

```

---

### Post by KLStringer on 2011-11-11
Is there anyway to speed up this process? It's been running or about a week now and has only made it through 365/4351 and I have another list of 475 recordings to find.


EDIT: How does find treat * in a file name? Does it treat it as a wildcard or as a * character? I ask because I'm only given the part of the file name that's unique to the recordings I need.

---

### Post by KLStringer on 2011-11-11
Somethings not working correctly it's moving files that are not in the file of recordings to copy.

[code]
while read file
 do
  echo "$file" >> /home/temp/echo.txt
         find /home/**/recordings -name "*$file" -exec cp "{}" /home/temp \;
  done < /media/recordings/Move.txt
[code]

---

### Post by matt_symes on 2011-11-11
Hi

> Somethings not working correctly it's moving files that are not in the file of recordings to copy.

```

while read file
 do
  echo "$file" >> /home/temp/echo.txt
         find /home/**/recordings -name "*$file" -exec cp "{}" /home/temp \;
  done < /media/recordings/Move.txt
```

Remove the * before $FILE. That may be the cause of your problem.

```

while read file
 do
  echo "$file" >> /home/temp/echo.txt
         find /home/**/recordings -name **"$file"** -exec cp "{}" /home/temp \;
  done < /media/recordings/Move.txt
```

/home/**/recordings/. This may also be a problem depending on your directory structure.

Kind regards

---

### Post by KLStringer on 2011-11-11
Thanks for tip, I'll take the * out and re-run it, I censored the /home/**/recordings I have the full path in the script.

---

### Post by KLStringer on 2011-11-14
OK this is what I have

```

while read file
do
find /home/**/recordings/ -name "$file" exec cp "{}" /home/temp \;
done < /media/recordings/move.txt

```


move.txt contains the 10 digit unique # from a recording filename that I need to pull

/home/**/recordings contains station/year/month/day/ sub-folders. Files in day are named in the following format: unique10digi# @ who_recorded_it @ HH-MM-SS.wav

After 2 weeks I'm still not pulling the recordings that I need, I would like to understand why this isn't working and get it working.

Thanks for all the help, its really appreciated.

---

### Post by KLStringer on 2011-11-14
I added the full path and file name of a file that I 100% know is in /home/**/recordings to the move.txt and still find does nothing.

---

### Post by KLStringer on 2011-11-14
```

find "/home/**/recordings/" -name "9858700743 by jrutherford@censored @ 1_56_54 PM.wav" -exec cp "{}" /home/temp/ \;

```

Running the above from the cli works, running it from the script file doesn't....

---

### Post by KLStringer on 2011-11-14
```

find "/home/**/recordings/" -name "9858700743"* -exec cp "{}" /home/temp/ \;

```

Works from the cli and moves 2 files over, running from script it doesn't work. It's like the Move.txt file is being read but not passed to find if that makes any sense.

---

### Post by KLStringer on 2011-11-15
This isn't working can anyone suggest something else?

---

### Post by Vaphell on 2011-11-15
you have to pass your pattern to find in the form of string to prevent shell from expanding it before find can lay its hands on it. Leaving it at the surface for shell to see is asking for trouble

```
$ find . -name **'pro*'**
./proxy1.txt
./proxy.txt
./proxy.sh
./prob.py
$ find . -name **pro***
find: paths must precede expression: proxy.sh
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

```

in the latter case find in reality looks like this:
```
find . -name prob.py proxy.sh proxy.txt proxy1.txt
```
shell expanded pro* and now find is confused by the unexpected parameters.

either way print out some info to get some clues where things go wrong, for example:
```
find -name .... -print -exec ....
```
**-print** forces find to list the names of found files. If you get something in terminal window you can look at -exec mv part

l2debug :D

care to show your current script? some sample data for tests would be nice too.

---

### Post by KLStringer on 2011-11-15
> **Vaphell said:**
> you have to pass your pattern to find in the form of string to prevent shell from expanding it before find can lay its hands on it. Leaving it at the surface for shell to see is asking for trouble

```
$ find . -name **'pro*'**
./proxy1.txt
./proxy.txt
./proxy.sh
./prob.py
$ find . -name **pro***
find: paths must precede expression: proxy.sh
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

```in the latter case find in reality looks like this:
```
find . -name prob.py proxy.sh proxy.txt proxy1.txt
```shell expanded pro* and now find is confused by the unexpected parameters.

l2debug :D

care to show your current script? some sample data for tests would be nice too.


Current script:
```

while read file
do
find "/home/**/recordings/" -name "$file*" -exec cp "{}" /home/temp \;
echo "$file" >> /home/temp/move_11_15_2011.txt
done < /media/recordings/find_me.txt

```find_me has about 10k 10 digit #'s that match the 10 digit number that's part of the actual file name.

example file name
```

1234567890 @ KLStringer @ 11_41_34 AM.wav

```There maybe multiple files that have the same 10 digit ID number, I need all of them that match

> 
either way print out some info to get some clues where things go wrong, for example:
```
find -name .... -print -exec ....
```**-print** forces find to list the names of found files. If you get something in terminal window you can look at -exec mv part
I don't really follow this, how would I add this into my current script?

Thank you for all the help, works to busy to teach myself and there's no one here to learn from.

---

### Post by KLStringer on 2011-11-15
I added -print in as below and nothing gets printed to the screen

```

while read file 
do 
find "/home/**/recordings/" -name "$file*" -print -exec cp "{}" /home/temp \; 
echo "$file" >> /home/temp/move_11_15_2011.txt
done < /media/recordings/find_me.txt

```Does this confirm my suspicion that find isn't really reading the file of file names and if so how do I get it to read the file?

---

### Post by erind on 2011-11-15
> **KLStringer said:**
> ...

find_me has about 10k 10 digit #'s that match the 10 digit number that's part of the actual file name.

example file name
```

1234567890 @ KLStringer @ 11_41_34 AM.wav

```There maybe multiple files that have the same 10 digit ID number, I need all of them that match

...

If you type:

```
find /home/*/recordings/  \( -name "*1234567890*" -o -name "*2323155555*" \) -type f -print
```does it show anything ? How long does it take ? Do the file names contain spaces (as shown) ? Replace the numbers above with actual numbers that you know they exist in the recordings and post its output here.

---

### Post by KLStringer on 2011-11-15
```

find /home/*/recordings/  \( -name "*1234567890*" -o -name "*2323155555*" \) -type f -print

```

Yes file names have spaces, takes about 5 sec's to run, nothing gets shown

---

### Post by erind on 2011-11-15
> **KLStringer said:**
> Running this returns nothing

```

find /home/*/recordings/  \( -name "*1234567890*" -o -name "*2323155555*" \) -type f -print

```

Before I posted:
 
> Replace the numbers above with **actual numbers that you know they exist in the recordings **and post its output here.

---

### Post by Vaphell on 2011-11-15
```
#!/bin/bash

recs="$HOME/recordings/"
flist="$HOME/recordings/file_list.txt"
report="$HOME/recordings/move_$(date +%d_%m_%Y).txt"
destdir="/tmp"

echo recordings: "$recs"
echo input list: "$flist"
echo report file: "$report"
echo destination: "$destdir"

while read file
do
  echo "looking for \"$file\""
  find "$recs" -name "$file" -print -exec cp "{}" "$destdir" \;
  echo "$file" >> "$report"
done < "$flist"
```

output:
```
**$ ./find.sh **
recordings: /home/me/recordings/
input list: /home/me/recordings/file_list.txt
report file: /home/me/recordings/move_15_11_2011.txt
destination: /tmp
looking for "1234567890 @ KLStringer @ 11_41_34 AM.wav"
/home/me/recordings/whatever/omgwtf/1234567890 @ KLStringer @ 11_41_34 AM.wav
**$ cat move_15_11_2011.txt** 
1234567890 @ KLStringer @ 11_41_34 AM.wav
**$ ls /tmp/*.wav**
/tmp/1234567890 @ KLStringer @ 11_41_34 AM.wav


```

i parametrized everything, so tweak variables at the top to suit your needs

EDIT: i forgot to look for other items with numeric prefix, brb

---

### Post by KLStringer on 2011-11-15
> **erind said:**
> Before I posted: Replace the numbers above with **actual numbers that you know they exist in the recordings **and post its output here

Yes, I replaced them with numbers I know are there, still gave same results.

---

### Post by Vaphell on 2011-11-15
```
#!/bin/bash

recs="$HOME/recordings/"
list="$HOME/recordings/list.txt"
report="$HOME/recordings/move_$(date +%d_%m_%Y).txt"
destdir="/tmp"

echo recordings: "$recs"
echo input list: "$list"
echo report file: "$report"
echo destination: "$destdir"

while read id
do
  echo "looking for \"$id\""
  echo "$id:" >> "$report"
  find "$recs" -name "$id*" -type f -print -exec cp "{}" "$destdir" \; | tee -a "$report"
done < "$list"
```

test output:
```
$ ./find.sh 
recordings: /home/me/recordings/
input list: /home/me/recordings/list.txt
report file: /home/me/recordings/move_15_11_2011.txt
destination: /tmp
looking for "1234567890"
/home/me/recordings/whatever/omgwtf/1234567890 @@@@@.wav
looking for "9999999999"
/home/me/recordings/whatever/omgwtf/9999999999 @ KLStringer @ 11_41_34 AM.wav
looking for "1111111111"
/home/me/recordings/whatever/omgwtf/1111111111 @ something.wav

```
log file move_15_11_2011.txt:
```
1234567890:
/home/me/recordings/whatever/omgwtf/1234567890 @@@@@.wav
9999999999:
/home/me/recordings/whatever/omgwtf/9999999999 @ KLStringer @ 11_41_34 AM.wav
1111111111:
/home/me/recordings/whatever/omgwtf/1111111111 @ something.wav
```
destination dir:
```
$ ls /tmp/*.wav
/tmp/1111111111 @ something.wav  /tmp/1234567890 @@@@@.wav  /tmp/9999999999 @ KLStringer @ 11_41_34 AM.wav

```

---

### Post by KLStringer on 2011-11-15
> **Vaphell said:**
> ```
#!/bin/bash

recs="$HOME/recordings/"
flist="$HOME/recordings/file_list.txt"
report="$HOME/recordings/move_$(date +%d_%m_%Y).txt"
destdir="/tmp"

echo recordings: "$recs"
echo input list: "$flist"
echo report file: "$report"
echo destination: "$destdir"

while read file
do
  echo "looking for \"$file\""
  find "$recs" -name "$file" -print -exec cp "{}" "$destdir" \;
  echo "$file" >> "$report"
done < "$flist"
```output:
```
**$ ./find.sh **
recordings: /home/me/recordings/
input list: /home/me/recordings/file_list.txt
report file: /home/me/recordings/move_15_11_2011.txt
destination: /tmp
looking for "1234567890 @ KLStringer @ 11_41_34 AM.wav"
/home/me/recordings/whatever/omgwtf/1234567890 @ KLStringer @ 11_41_34 AM.wav
**$ cat move_15_11_2011.txt** 
1234567890 @ KLStringer @ 11_41_34 AM.wav
**$ ls /tmp/*.wav**
/tmp/1234567890 @ KLStringer @ 11_41_34 AM.wav


```i parametrized everything, so tweak variables at the top to suit your needs

EDIT: i forgot to look for other items with numeric prefix, brb


Ok tried this and I get
 ```

...snip...
"ooking for "972247765
...snip...

``` printed to the screen for every file its looking for and still nothing gets copied over, even files I 100% know are there.
report file also isn't being created

---

### Post by Vaphell on 2011-11-15
i updated the script, because i checked for whole names not numeric prefixes in names.

what do the full paths of your files look like? i'll recreate them in the exact spot and try to use my script.

---

### Post by KLStringer on 2011-11-15
> **Vaphell said:**
> i updated the script, because i checked for whole names not numeric prefixes in names.

what do the full paths of your files look like? i'll recreate them in the exact spot and try to use my script.


The paths differ once you get down passed /home/**/recordings, after that level there are about 100 different campaign folders and in each one of them are year/month/day folders and finally the files them selves. Some campaigns have multiple years in them.

Let me go back and check your modified script and see if it works or not.

Some of the older campaign names also have spaces in them 

Sample Path: 
```

/home/**/recordings/Make_my_*****_bigger_pill/2010/1/2
/home/**/recordings/Make_my_*****_bigger_pill/2011/1/2
/home/**/recordings/Weight Loss 2000/2009/12/31

```Folder names changed to protect my ***

---

### Post by KLStringer on 2011-11-15
> I updated the script, because I checked for whole names not numeric prefixes in names.

Changed the script and now it prints

```

Looking for ""

```

on the screen report file is created, no files are copied over

---

### Post by Vaphell on 2011-11-15
that would mean that variable that is inside the quotes is null - it's not set anywhere. Most likely you dont have the same variable used 

```
while read **VARIABLE**
do
  echo "looking for \"$**VARIABLE**\""
```
did you modify your script to match mine or reconfigure mine (from #34) while leaving the body intact? (i changed the name of it from file to id)

my version works just fine with your dirs and some junk files
output 
```
$ ./find.sh 
recordings: /home/me/recordings/
input list: /home/me/recordings/list.txt
report file: /home/me/recordings/move_15_11_2011.txt
destination: /tmp
looking for "1234567890"
/home/me/recordings/Weight Loss 2000/2009/12/31/1234567890 @@@@@.wav
/home/me/recordings/Make_my_something_bigger_pill/2010/1/2/1234567890 @@@@@.wav
/home/me/recordings/Make_my_something_bigger_pill/2011/1/2/1234567890 @@@@@.wav
looking for "9999999999"
/home/me/recordings/Weight Loss 2000/2009/12/31/9999999999 @ KLStringer @ 11_41_34 AM.wav
/home/me/recordings/Make_my_something_bigger_pill/2010/1/2/9999999999 @ KLStringer @ 11_41_34 AM.wav
/home/me/recordings/Make_my_something_bigger_pill/2011/1/2/9999999999 @ KLStringer @ 11_41_34 AM.wav
looking for "1111111111"
/home/me/recordings/Weight Loss 2000/2009/12/31/1111111111 @ something.wav
/home/me/recordings/Make_my_something_bigger_pill/2010/1/2/1111111111 @ something.wav
/home/me/recordings/Make_my_something_bigger_pill/2011/1/2/1111111111 @ something.wav

```

---

### Post by KLStringer on 2011-11-15
Yep your right forgot to change $file to $id in the looking for line, all the rest was good although nothing is copied over still.

Not sure if it's related but before I changed $file to $id the screen output would display 
```

Looking for: ""

```Now it outputs:
```

"ooking for: 1234567890
```Its replacing the 'L' with a double quote and dropping the last double quote


Thank you for all the help, I'm heading home for the night will pick it back up tomorrow morning. Have a good night

---

### Post by Vaphell on 2011-11-15
So do you get some proper file names printed to terminal now (from find **-print**)? do you have -v switch after cp to have some visual feedback from the copy command itself?

> Its replacing the 'L' with a double quote and dropping the last double quote
this is something that i cannot explain at all o.O

---

### Post by KLStringer on 2011-11-16
> do you get some proper file names printed to terminal now

No, it just prints out the partial file names in the text file.

> do you have -v switch after cp to have some visual feedback from the copy command itself

Yes, there's no feedback from copy

---

### Post by Vaphell on 2011-11-16
i got an idea - have you edited the file with identifiers in windows?
does your file with numbers have only 10digit id in line? no spaces, weirdo characters?

do this on your file with IDs
```
while read line; do echo ${#line}; done < list.txt
```
if you get all 10s everything is ok with the file (unfortunately)
if not then go further:
```
sed 's/\r/*** CARRIAGE RETURN ***/' list.txt
sed 's/[^0-9]/*** NON-DIGIT ***/g' list.txt
```
if you get those nice warnings in output go with ```
sed -i 's/\r//' list.txt 
``` to wipe \r out or **'s/[^0-9]//g'** to wipe all non-digit characters altogether

\r at the end of line would cause failure of find command.
```

**$ id=$'1111111111'; find . -name $id'*' -type f**
./Weight Loss 2000/2009/12/31/1111111111 @ something.wav
./Make_my_something_bigger_pill/2010/1/2/1111111111 @ something.wav
./Make_my_something_bigger_pill/2011/1/2/1111111111 @ something.wav
[B]$ id=$'1111111111\r'; find . -name $id'*' -type f
$[/B]


```

---

### Post by KLStringer on 2011-11-16
Yep there were carriage returns in the file, ran the sed command and cleaned it up, re-running now, will let you know how it goes.

[-o<

---

### Post by KLStringer on 2011-11-16
Still didn't copy anything over and the log file only has the partial file names in it. So close yet still no joy :( though I think we're getting close.

EDIT: Maybe I spoke to soon looks like its starting to copy files over

---

### Post by KLStringer on 2011-11-16
It's looking good so far, only thing is I need to limit it to finding only files 24 hours old or newer.

---

### Post by KLStringer on 2011-11-18
Got everything working now its just tweaking the date range it searches.

```

sed -i 's/\r//' move.txt
sed -i 's/.wav//' move.txt 

while read file
do
find "home/**/recordings/" -name "$file*" -ctime -2 -print -exec cp "{}" /home/temp \;
echo "$file" >> /home/temp/moved_$(date +%d_%m_%y).txt
done < /media/recordings/move.txt

```

Thank you so much for all the help everyone, especially Vaphell I owe you a beer.

---

### Post by KLStringer on 2011-11-21
I need cp to also copy the folder a recording is in, currently it just copies the file over to /home/temp directory. I need it to copy them to /home/temp/campaign/MM_DD_YY/recording depending on what campaign/MM_DD_YY folder the files were found in.

How do I change it to do the above?

---

