---
title: "find command - sending only the filename to exec?"
date: 2012-07-01
forum: General Help
---

### Post by Riothamus on 2012-07-01
Is there a way to send only the filename to exec, rather than the entire path?

```

find . -name "*.txt" -exec echo {} \'

```This only lists the entire path, but not the filename by itself.

I'm aware of the -print option, but I don't want to use it because I'm not actually trying to run echo with find. I'm trying to create a command line order to get all the files in a bunch of different directories, and then check if that file is in a different directory, and if it is, delete the file it found. So my final command-line will be something like:

```

find . -name "*.txt" -exec if [[ -f TXT/{} ]] : then rm {}; fi \;

```But I can't figure out how to get just the filename in {} and not the whole path.

---

### Post by Vaphell on 2012-07-01
how about

```
while read file
do
  name="${file##*/}"
  echo "$name"
  # do stuff here
done < <( find . -iname '*.txt' )
```

find would be used to list files, but the actual logic would be in a loop.

---

### Post by matt_symes on 2012-07-01
Hi

If you want just the filename you can use the basename argument.

```
find ./ -type f -exec basename {} \;
```You can try to modify that, however you may find it easier to do what you want in bash, using a script or a function.

EDIT: Just like Vaphell has shown :) 

Kind regards

---

### Post by Riothamus on 2012-07-01
Thanks for the quick replies.

Unfortunately, I'm still learning Linux, and I don't know how to create scripts yet. Would I just put that code in a .pl file or something?

Is there a way to use the value basename returns as an argument on the commandline? When I do:

```

find .  -type f -exec basename {} \;

```

it displays the filename, just like if I'd echoed it. But when I do

```

find . -type -f -exec echo basename {} \;

```

it echoes "basename" and then the filename with the full path.

The problem is I need both the full path and just the filename in two different places in the code I posted in my first post. I need just the filename in the if [[ -f {} ]] part, and I need the full path in the rm {} part.

---

### Post by matt_symes on 2012-07-01
Hi

basename is a command in itself just like find.

From ```
man basename
```> BASENAME(1)                                                                    User Commands                                                                    BASENAME(1)

NAME
       basename - strip directory and suffix from filenames
The problem you have is you want to delete a file based on a condition.

I'm not sure if find is really geared up for that (although i will do some research for you). 

You may fiind it easier to call a bash script or function after -exec and get that to do the checking and deletion for you.

I would still suggest using a bash script for the entire job though.

Kind regards

---

### Post by Riothamus on 2012-07-01
Thanks again for the reply.

Unfortunately, it turns out creating a script isn't an option because I'm completely out of space on my computer, which is why I'm trying to delete these files.

What happened is I was using photorec to recover some files that were accidentally lost during an upgrade. But unfortunately, the script that I got off their webpage for organizing the files after they're recovered copied the files rather than moving them, so now I'm all out of space. It won't even let me save a simple script with only a few lines in it. I just tried.

So basically, if there's a way to run this from the command-line, I'd like to do that. I'd prefer not to delete the files and then run the organizer too again, because first I don't know how to modify it to move the files instead of copying them, and second, I've never used it before, so I don't want to take any chances that maybe I don't know what's going on and some of the files were moved and I won't be able to recover them, and so on.

---

### Post by Vaphell on 2012-07-01
i typed the one-liner version of the while loop i posted earlier but decided to edit it out.

warning: It appears that you have TXT inside the dir you are trying to run find from. You risk losing files inside TXT if you do your stuff carelessly.
- files inside TXT get listed
- if test confirms there exists the TXT/file version (well duh)
- rm happens.



can you move the TXT dir away from the location you run find in? If not, it would be necessary to program around this problem.

easy case with TXT outside would be like this:
```
while read file
do
  name="${file##*/}"
  if [ -f "/path/to/TXT/$name" ]
  then
    **echo** rm "$file"
  fi
done < <( find . -iname '*.txt' )
```

if you copy-paste this whole code block (highlight here, middleclick-paste in terminal/ctrl+c, ctrl+shift+v in terminal), it should run just fine.
I used echo to print "rm <file>" instead of running it, to make sure it gets the right files.
Otherwise you can write a proper one-liner in the form of 

```
while read file; do ...; ...; ...; if [ ... ]; then ...; ...; else ...; ...; fi; done < <( ... )
```


case with TXT inside could be fixed with grep (-v skips lines that match the pattern)
```
...
done < <( find -iname '*.txt' | grep -v '[.]/TXT' )
```
find supports -prune option that can be used to skip things, but the logic behind the syntax of option can appear not too obvious so i ignored it.

---

### Post by steeldriver on 2012-07-01
How about explicitly testing that the found file and the TXT/file are not the same?

```
find . -iname '*.txt' -exec sh -c 'if [ -f TXT/$(basename {}) ] && ! [ {} -ef TXT/$(basename {}) ]; then echo rm {}; fi' \;
```or (possibly safer for arbitrary filenames / many files) using xargs

```
find . -iname '*.txt' -print0 | xargs -0I {} sh -c 'if [ -f TXT/$(basename {}) ] && ! [ {} -ef TXT/$(basename {}) ]; then echo rm {}; fi' \;
```The '&&' is a shortcut I think i.e. it should only get evaluated for cases that *do* match TXT/file

EDIT: or could we just prune the TXT/ path? 

```
find . -path '*TXT/*' -prune -o -iname '*.txt' -print0 | xargs -0I {} sh -c 'if [ -f TXT/$(basename {}) ] ; then echo rm {}; fi' \;
```

---

### Post by Riothamus on 2012-07-01
```

find . -iname '*.txt' -exec sh -c 'if [ -f TXT/$(basename {}) ] && ! [ {} -ef TXT/$(basename {}) ]; then echo rm {}; fi' \;

```When I do that, it just sits there and I can't tell if it's doing anything. I'm not sure what the sh-c does, but when I remove it, it says 

```

find: `if [ -f TXT/$(basename ./recup_dir.2627/f407404552.txt) ] && ! [ ./recup_dir.2627/f407404552.txt -ef TXT/$(basename ./recup_dir.2627/f407404552.txt) ]; then echo rm ./recup_dir.2627/f407404552.txt; fi': No such file or directory

```Removing the quotes from the if statement gives:

```

bash: syntax error near unexpected token `then'

```
When I do

```

find . -path '*TXT/*' -prune -o -iname '*.txt' -print0 | xargs -0I {} sh -c 'if [ -f TXT/$(basename {}) ] ; then echo rm {}; fi' \;

```It also stays quiet and I can't see if it's doing anything. Removing sh -c gives:
```

find . -path '*TXT/*' -prune -o -iname '*.txt' -print0 | xargs -0I {} sh -c 'if [ -f TXT/$(basename {}) ] ; then echo rm {}; fi' \;

```Removing the single quotes from the if statement again gives the bash syntax error.

I also tried copying the while loop on a single line, but I'm not clear on where the semicolons need to go, and I don't understand where the loop ends and begins. I would think I should put brackets at the beginning and the end?

---

### Post by Vaphell on 2012-07-01
while loop starts its block with **do** end ends with **done**
```
while read variable
do
  cmd1
  cmd2
done
```
is equivalent to 
```
while read variable; do cmd1; cmd2; done;
```

if you want to pass the output of some command to while read x you need to add < <( command ) after done.
```
while read x; do ....; done < <( command )
```
or use pipe
```
command | while read x; do ...; done
```

similar thing with if, then/else start logical blocks, fi ends the whole thing

```
if <condition>
then
  cmd1
  cmd2
else
  cmd3
  cmd4
fi
```

```
if <condition>; then cmd1; cmd2; else cmd3; cmd4; fi;
```

in general all lines require ; unless it's a keyword that begins a block ( while/for ... **do** ... done, if ... **then** ... **else** ... fi) - it will complain if its followed by ;

---

### Post by Riothamus on 2012-07-02
Thanks for the explanation. Okay, here's what I have:

```

while read file do name="${file##/}"; if [ -f "TXT/$name" ] then echo rm "$file" fi; done < <(find . -iname '*.txt' | grep -v '[.]/TXT' )

```

And it's giving the error
```

bash: syntax error near unexpected token `done'

```

Seems like I have something slightly off.

---

### Post by Vaphell on 2012-07-02
conditions and loop descriptions are ended by ; too
```
while read file[COLOR="Red"];[/COLOR] do name="${file##[COLOR="Red"]*[/COLOR]/}"; if [ -f "TXT/$name" ][COLOR="Red"];[/COLOR] then echo rm "$file"[COLOR="Red"];[/COLOR] fi; done < <(find . -iname '*.txt' | grep -v '[.]/TXT' )
```

---

### Post by Riothamus on 2012-07-02
```

while read file do name="${file##/}"; if [ -f "TXT/$name" ]; then echo rm "$file"; fi; done < <(find . -iname '*.txt' | grep -v '[.]/TXT' )

bash: syntax error near unexpected token `fi'

```

EDIT: Sorry, didn't see your last edit. Trying that now...

---

### Post by Vaphell on 2012-07-02
also this needs fixing:
```
name="${file##[COLOR="Red"]*[/COLOR]/}";
```

##*/ means take the $file variable and remove the longest possible string from the left (##) that matches <any char sequence>+'/'
without * the pattern won't match a thing.

---

### Post by Riothamus on 2012-07-02
Thanks! Now it's working.

One thing, though. A lot of files were deleted, so I expected it to free up some space. But it's still giving me a "No space on device" error whenever I try to create a new file, even if it's just a few lines long. Any idea what could be causing the problem?

---

### Post by Vaphell on 2012-07-02
just checking: did you remove *echo* from the one-liner to actually run rm commands?

you may want to reduce the amount of reserved space that defaults to 5% of capacity (it's done to make sure root has the room to operate which is not possible when disk writes can't happen, of course 5% is a lot of space considering partition sizes today and it can be toned down to a more reasonable 1% or something like that).
[http://linuxaria.com/pills/free-reserved-ext3-ext4-filesystems](http://linuxaria.com/pills/free-reserved-ext3-ext4-filesystems)

---

### Post by Riothamus on 2012-07-02
Thanks for the info about the 5% of space. That ended up being it. I freed up some more files and I can save stuff again.

Thanks to the two of you for all the help.

---

