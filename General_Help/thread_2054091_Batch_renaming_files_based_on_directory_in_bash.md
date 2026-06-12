---
title: "Batch renaming files based on directory in bash"
date: 2012-09-06
forum: General Help
---

### Post by drmrgd on 2012-09-06
Being a still learning, complete bash newbie, I'm finding myself stuck with what I thought should be a simple task.  Maybe one of the experts here can lend a quick hand?

I have a structure similar to this on my fs:

```
/main_directory/
   /directory1/
      /file.txt
   /directory2/
      /file.txt
   /directory3/
      /file.txt
```

This goes on for quite a while.  What I'd like to do is to rename each 'file.txt' (a static name that does not change) to 'directory1.txt'.  Since there are a number of subdirectories in which I can find file.txt, I though a find / exec method would be best, along with a string expansion.  As a test, from main_directory, if I run:

```
find . -name "file.txt" -exec bash -c 'mv $1 "${1/file/`basename $PWD`}"' -- {} \;
```

I can successfully rename each as main_directory.txt, which is not what I want.  However, I can't seem to figure out what to replace $PWD with.  I know the find results look like:

```
./directory1/file.txt
./directory2/file.txt
.
.
.

```

So, I'm trying to trim out the 'directory*' part, but I can't quite get it as I don't know how to trim out only what I need from the string and pass that along.  How can I use 'cut' in that mv command?  

Maybe I'm going about this all wrong.  What would be the best strategy here to get the result I'm looking for?

---

### Post by sisco311 on 2012-09-06
```

#!/bin/bash

cd main_dir || exit 1
shopt -s nullglob

for file in */file.txt
do
    dir="${file%/*}"
    echo mv -b -- "$file" "${dir}/${dir}.txt"
done
```

[http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

---

### Post by drmrgd on 2012-09-06
Wow!  That was fast!

I think I see some of my pitfalls here.  In general I think I was trying to do too much with a one liner, and should have just made a  script.  I was trying to use (although very poorly!!!!) parameter expansion, but didn't know the name.  The script you wrote works beautifully!  Next time I'll try to not bite off so much.

A quick question if you don't mind: What are you doing with the 'shopt -s nullglob' statement.  I don't know what it means, and even after reading the man page on shopt, I'm still a little unclear on what it does.

Anyway, thanks again for the help!

---

### Post by sisco311 on 2012-09-06
```

[sisco@acme foo]$ shopt -u nullglob 
[sisco@acme foo]$ for file in no_such_file_*; do echo $file; done
no_such_file_*
[sisco@acme foo]$ shopt -s nullglob 
[sisco@acme foo]$ for file in no_such_file_*; do echo $file; done
[sisco@acme foo]$ 

```

As you can see in the above code, if the nullglob option is not set and the pattern (no_such_file_*) does not match any file name, then the word is left unchanged. The variable file is set to the word (no_such_file_*) and the body of the for loop is executed.

If nullglob is set and no matches are found, the word is removed. In this case the body of the for loop is not executed.

---

### Post by drmrgd on 2012-09-06
Oh, now I understand what's happening here.  That's a very good idea!  I had no idea about that command.  I can see that's a useful tool to use.  Thank you very much for the help and education!

---

### Post by sisco311 on 2012-09-06
You are welcome!

---

