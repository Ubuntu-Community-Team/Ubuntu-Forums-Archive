---
title: "Problem with command in shell"
date: 2011-01-03
forum: General Help
---

### Post by Bladtman242 on 2011-01-03
Hi, I am trying to run a command in bash, but I cant seem to get it right.

```
echo `ls | awk '{print "\""$0"\""}'`
```Output is names of all files in current dir, each file name surrounded by quotation marks.

BUT:```

rm `ls | awk '{print "\""$0"\""}'`
```returns:
```
rm: cannot remove `"jf"': No such file or directory
rm: cannot remove `"kaskl"': No such file or directory
rm: cannot remove `"new': No such file or directory
rm: cannot remove `file"': No such file or directory

```
Notice the weird ` and ' wrappings?
 
Files in dir are:
jf
kaskl
new file

I realise there are easier ways to delete all files from a folder,
but this would allow me to use awk to filter which files should be deleted :)

---

### Post by irishbreakfast on 2011-01-03
rm `ls | awk '{print ""$0""}'`

---

### Post by Bladtman242 on 2011-01-04
That gives the same (error) output as before, but without the double quotes (") around the names, which is really needed for rm to understand the white spaces correctly :/

---

### Post by sisco311 on 2011-01-04
I doubt that awk is the right tool for the job, but anyway, try something like:
```
ls | awk '{print $0}' | xargs -d '\n' **command_to_remove_the_file**
```

EDIT: it should work if the file names do not contain a newline.

---

### Post by James78 on 2011-01-04
I made an awkless one, in light of the post above.
```
ls | xargs -i command_to_remove_file_or_directory \"'{}'\"
```

---

### Post by Bladtman242 on 2011-01-05
**sisco311:** 
Thanks, hadn't occurred to me to use xargs :lolflag:
Two questions if you don't mind though : )

1. 
Why shouldn't I use awk for this?
Not trying to be a smart ***, just eager to learn : ) 

2.
How come it works without the use of qoutes?
I realise that the -d flag sets the delimiter to newline, but does xargs then automaticly pass the text between delimiters with qoutes or?
[B]
James78:[/B] 
But the entire idea was to be able to make a customized filter for the deletion/renaming/whatever

---

### Post by sisco311 on 2011-01-05
> **Bladtman242 said:**
> 
1. 
Why shouldn't I use awk for this?
Not trying to be a smart ***, just eager to learn : ) 


Well, awk is a very powerful, but I don't see any reason for using it to filter the files. In most cases globbing and/or the find command is enough. Could you post an example?

> **Bladtman242 said:**
> 
2.
How come it works without the use of qoutes?
I realise that the -d flag sets the delimiter to newline, but does xargs then automaticly pass the text between delimiters with qoutes or?


When you quote or escape a space you tell to the interpreter (bash or a command) to not to treat it as a special character (field separator or delimiter). If you set the delimiter to only a newline, then space is no longer a special character, so you don't have to escape it.

---

### Post by Bladtman242 on 2011-01-05
Ah, the quote issue makes sense : )
But how is globbing different from this?
I'm not familiar with the term and googling it I only found that it's a sort of pattern matching. Which sounds pretty similar to this awk one-liner : )

Hmm an example..
This is kind of embarrassing, I've forgotten how I wanted to implement this.
It was something like copying files from one folder to another, and then renaming duplicates without the nasty '~' at the end of the name.
Perhaps I *could* just use find for this. I'll have too look into that.
Still, learning something new is never a bad thing I suppose : )

---

### Post by sisco311 on 2011-01-05
> **Bladtman242 said:**
> Ah, the quote issue makes sense : )
But how is globbing different from this?
I'm not familiar with the term and googling it I only found that it's a sort of pattern matching. Which sounds pretty similar to this awk one-liner : )


Check out:
[http://mywiki.wooledge.org/BashGuide/Patterns](http://mywiki.wooledge.org/BashGuide/Patterns)


> **Bladtman242 said:**
> 
Hmm an example..
This is kind of embarrassing, I've forgotten how I wanted to implement this.
It was something like copying files from one folder to another, and then renaming duplicates without the nasty '~' at the end of the name.
Perhaps I *could* just use find for this. I'll have too look into that.
Still, learning something new is never a bad thing I suppose : )

I'm not sure if I understand this correctly.

So lets say you want to copy any .txt file from a directory to another. You can simply run:
```
cp -b /path/to/source/*.txt /path/to/dest
```

Now to rename any backup files from file~ to file.backup you could run:
```
for file in *~; do 
  mv -b -- "$file" "${file#~}".backup
done
```

---

### Post by James78 on 2011-01-05
> **Bladtman242 said:**
> **James78: **
But the entire idea was to be able to make a customized filter for the deletion/renaming/whatever
Simple. :) Just replace the command ls with the find command, and customize it to your liking to return what you want.
```
find . -type f -name "*.cpp" | xargs -i command_to_remove_file_or_directory \"'{}'\"
```
Which would find all files (skips directories) in the current directory, and all directories below (recursive), which are named anything with a .cpp extension, then it would remove them while quoting the filenames (in case they have spaces in them)

---

### Post by sisco311 on 2011-01-05
> **James78 said:**
> 
```
find . -type f -name "*.cpp" | xargs -i command_to_remove_file_or_directory \"'{}'\"
```

Hmmm... I would use something like:
```

cd /path/to/dir
find ./ -name '*.cpp' -type f -print0 | xargs -0 command --
```

The -name test comes before the -type test  in  order  to  avoid having to call stat(2) on every file.

And my version doesn't fails if the filename contains a newline; see:
```
man find | less +3/-print0
```

---

### Post by Bladtman242 on 2011-01-06
I really cannot remember why I wanted to use awk for this now : D
Anyway, thanks for the help both of you.
I've got the knowledge I needed now : )

---

### Post by gadolinio on 2011-01-06
> **Bladtman242 said:**
> 
```
echo `ls | awk '{print "\""$0"\""}'`
```Output is names of all files in current dir, each file name surrounded by quotation marks.

Quotes are not needed. To delete a file called "file", you can just type
rm file
and not
rm "file"

So the awk doesn't need the quotes.

---

### Post by hawkmage on 2011-01-06
If you are going to use find why not use the '-exec' option to do the 'rm'?

Like this:
```
find /path/to/dir -name \*.cpp -type f -exec rm '{}' \;
```

---

### Post by Bladtman242 on 2011-01-07
gadolinio: not if the file name contains whitespaces 

Hawkmage: I was planning on doing that :)
But I appreciate the input.

---

