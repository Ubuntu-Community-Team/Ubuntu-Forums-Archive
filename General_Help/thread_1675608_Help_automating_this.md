---
title: "Help automating this"
date: 2011-01-25
forum: General Help
---

### Post by primetime34 on 2011-01-25
I am currently trying to learn how to write scripts (any suggestions of good resources/where to start?).  However, I am not ready to figure this out yet.  I have a situation where it would be really nice to automate this process.

I have 130 sub-directories under the directory "wallpaper".  Here is the structure

~/wallpaper/aba/gallery/images/
~/wallpaper/accra/gallery/images/

Now, there are additional folders and files that I would like to delete.  Using the above folders

~/wallpaper/aba/gallery/slideshow/
~/wallpaper/aba/gallery/submit/
for each of the 130 directories under wallpaper.

Inside the main images folder
~/wallpaper/aba/gallery/images
there are thumbnail images I would like to delete.  They all have the word thumb in them.

I would like to delete the folder /slideshow/ and /submit/ and all the images with the word "thumb" in them inside the /images folder.

Any way to automate this, or do I need to go through all 130+ folders doing the work manually? 

Thanks in advance.

---

### Post by Cheesehead on 2011-01-25
Of course you can script it. And this is a great place to start learning shell commands...which are the first step in scripting.

**Tip: This is not be undo-able if you make a mistake. A backup before you begin is a *really* good idea, else a mistake may permanently lose some of your data!


First, you need to know the shell command to delete a directory.
It's 'rm'.  Take a look at the manual for rm with the command 'man rm'

**Warning: rm is unforgiving. If you make a mistake, rm won't care. So check twice before you hit Enter! And backup before you start!

Let's do the first directory manually:```

rm -iv ~/wallpaper/aba/gallery/thumb*
rm -riv ~/wallpaper/aba/gallery/slideshow
rm -riv ~/wallpaper/aba/gallery/submit

```

What do the -iv and -riv flags mean? Well, take a look at the man page. The -i and -v flags are there to protect you.

Do a couple directories manually until you are bored with it. Then you are ready for the next step of scripting

Second step - basic scripting:

Open a text editor (like gedit or mousepad or whatever) and save a file that looks like this. Call it something like testremove.sh:
```
#!/bin/sh
directory="~/wallpaper/aba/gallery"   # Since you already deleted this directory, substitute one that still exists
rm -v $directory/thumb*
rm -rv $directory/slideshow
rm -rv $directory/submit

```

Now on the command line, try:
```
sh testremove.sh
```
Congratulations...you are scripting!


Third step, more advanced scripting:
**DO NOT JUMP TO THIS STEP. Do the earlier steps first! Diving straight into this kind of scripting without understanding it puts you at veryh high risk for data loss!

The 'ls' command will give you a list of all the files and subdirectories in a directory. Take a look at 'man ls'.

You can take the result of 'ls' and use it to feed the script.
For example:
```
#!/bin/sh
directories=$(ls -x ~/wallpaper/)     # Get the list of all wallpaper subdirectories
for directory in $directories             # Do the followin in EACH subdirectory
do
    rm -v ~/wallpaper/$directory/thumb*
    rm -rv ~/wallpaper/$directory/slideshow
    rm -rv ~/wallpaper/$directory/submit
done

```

---

### Post by primetime34 on 2011-01-26
That is a huge help.  Thank you so much.

Any suggestions where to start to learn the syntax of scripting?  I can figure out most of the linux commands, but I don't know where to start with regards to the language...the syntax of it all.  Thanks again for your help!

---

### Post by uyulala on 2011-01-26
Hi!

As a reference resource on scripting syntax,  I use "man bash" a lot. 

There are many bash scriptin guides out there, check out 

[http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html) and [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Regards,

---

### Post by asmoore82 on 2011-01-26
**[COLOR="Red"][SIZE="3"]Be very careful![/SIZE][/COLOR]**

> **Cheesehead said:**
> 
```
#!/bin/sh
directory="~/wallpaper/aba/gallery"   # Since you already deleted this directory, substitute one that still exists
rm -v $directory/thumb*
rm -rv $directory/slideshow
rm -rv $directory/submit

```

**Always** quote variable references in BASH unless you have a very, very
good reason to intentionally not do so. And even if/when you do skimp on quotes,
you should comment in the nearby code explaining why you are on such thin ice.

[COLOR="Red"]If you have a folder with a space in the name, such as "/home/mark/Important Thumbnails"
and you somehow successfully get this name stored in a variable,
but then attempt to delete it **without** quoting it...[/COLOR]
```
[COLOR="Red"]#NEVER RUN THIS![/COLOR]
folder="/home/mark/Important Thumbnails"
rm -rf $folder
```
^what does this become??
```
[COLOR="Red"]#NEVER DO THIS![/COLOR]
rm -rf /home/mark/Important Thumbnails
```
[COLOR="Red"]^`rm` will destroy "Important" before it gets around to complain that "Thumbnails" isn't there!![/COLOR]

You should also avoid the "~" Home shortcut in straight scripting -
it has different special meanings in different contexts.
Sticking to the plain old $HOME environment variable will be more stable.

For example, try this:
```
echo $HOME [COLOR="Blue"]#bad[/COLOR]
echo "$HOME" [COLOR="Blue"]#better[/COLOR]
echo ~ [COLOR="Blue"]#worse[/COLOR]
echo "~" [COLOR="Blue"]#worst[/COLOR]
```

> **Cheesehead said:**
> ```
#!/bin/sh
directories=$(ls -x ~/wallpaper/)
for directory in $directories
```
[COLOR="Red"]^Never do anything like this!
This breaks very, very badly with any files that have any remotely interesting characters in them, even spaces![/COLOR]

And again we have more unquoted variable references - more breakages.

The proper, safer and **much faster** way to accomplish the above is like this:
```
for object in "$HOME/wallpaper/"*
do
    if [ -f "$object" ]
    then
        [COLOR="Blue"]#object is a plain file, process it[/COLOR]
        echo "$object ... Done"
    fi
    if [ -d "$object" ]
    then
        [COLOR="Blue"]#object is a directory, likely to skip it[/COLOR]
        echo "$object ... Skipped"
    fi
    [COLOR="Blue"]#object could be none of the above...
    #  a fifo or maybe a socket, oh my!
    #  safely do nothing.[/COLOR]
done
```^note that the `*` wildcard on the very first line must be outside of the quotations.
The wildcard is basically doing the `ls` work for you. Except that it does so with
internal shell code that is specifically built to handle all possible cases.
This does **not** even break if filenames have multiple lines!! Which is legal on UNIX systems.

---

