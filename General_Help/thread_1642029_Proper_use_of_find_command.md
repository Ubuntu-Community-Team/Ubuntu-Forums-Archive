---
title: "Proper use of find command"
date: 2010-12-09
forum: General Help
---

### Post by bdemers on 2010-12-09
After reading the doc on find command I'd like to know how to use it!

All I want to be able to do most of the time is find instances of a file/directory name. Say I have a file called rpc, which exists btw.  So I write a command find / 'rpc'.  This doesn't work.  I get a stream of every file in the universe followed by a statement that my file doesn't exist.

Very obvious, I don't know what I'm doing.  The docs didn't work for me either.  So how do I get a list of only the files that have rpc in the file name?

Oh, ya, Please don't tell me to use the "Search for Files" in the gui.  I don't have a gui, only a command line.

Thanks for letting me look so stupid

---

### Post by cbraxton on 2010-12-09
> **bdemers said:**
> After reading the doc on find command I'd like to know how to use it!

The 'find' command is one of those things that comes to us from ancient Unix. The syntax can be a bit confusing, but it's not that bad really. (I guess it helps if you've been using it for the last 30 years!) 

A simple example, let's say you want to list all of the files with "abc" in their name under the directory "/usr/local" - you would issue the command:

```

find /usr/local -name \*abc\* -print

```

Notice that the asterisk wildcards are escaped with backslashes to keep them from being expanded by the shell.

The version in Ubuntu has an option for doing case-insensitive searches by using the option '-iname' intead of '-name' as shown above.

There are a lot more options of course but this is the basic way to find and list files.

---

### Post by bdemers on 2010-12-10
You'll notice in my example the slash, meaning of course, root.  Typically not a clue where it is.  As I mentioned this spawns a flood of files onto the screen followed by a "no file found" message.  On the rare occasion one hit on the desired file may be seen in the still displayed list just above that message.  In addition to iname, a whole series of other options are out there.  So is pattern which allows for an "exam" ple of what to search for.  But all I typically want to do is find some file somewhere with some specified name (iname is good switch) WITHOUT all the accompanying garbage, or, at least, the found files at the bottom of the list.

---

### Post by bouncingwilf on 2010-12-10
I remember struggling with it in the eighties! It never was a very intuitive command but whater you do, don't forget the -print option or else you'll patiently wait for a convoluted search to execute only to have it exit silently with no output! Very annoying!


Bouncingwilf

---

### Post by nothingspecial on 2010-12-10
This works for me

```
ns@ace:~/music$ find ./ -type f -iname \*cheese\*
./flac/Primus/Sailing the Seas of Cheese/Seas of Cheese.flac
ns@ace:~/music$
```

---

### Post by nothingspecial on 2010-12-10
> **bouncingwilf said:**
> I remember struggling with it in the eighties! It never was a very intuitive command but whater you do, don't forget the -print option or else you'll patiently wait for a convoluted search to execute only to have it exit silently with no output! Very annoying!


Bouncingwilf

It defaults to -print these days :)

---

### Post by bdemers on 2010-12-10
OK, here I want ONLY file named rpc.  I think that if I wanted files that had rpc as part of name I would have added a wildcard (*rpc*)

My unsuccessful try:

find ./ -print -iname 'rpc'

---

### Post by nothingspecial on 2010-12-10
First forget the print bit, it does that anyway.

Second ./ is diferent from /

./ means the current directory

/ means the root directory

To search the entire filesystem for a file named exactly rpc

```
find / -type f -iname 'rpc'
```

That will not find rpc.txt or rpc.jpg only a file named rpc

Also, you are talking about a file rather than a directory (folder), because if it is a directory change the f after -type to d.

---

### Post by bdemers on 2010-12-10
So I should have said 

find /  -iname 'rpc*'

This would give both file and directory? Should I have said -type f -type d?  Also * would show file with extension, but also any file with rpc as leading?

---

### Post by nothingspecial on 2010-12-10
You don`t have to specify both f and d, find does that if you don`t use -type. It`s just useful to narrow down as much as possible.

---

### Post by jim_deadlock on 2010-12-10
Have you considered using the locate command instead?

```
sudo updatedb
```This takes a few minutes to create a list of all files on your computer. Then you search that list like this:

```
sudo locate filename
sudo locate part/of/a/path
sudo locate partofafilename
```

---

### Post by bdemers on 2010-12-10
Thanks for the mini tutorial!!!!!!!!!!!!!

---

### Post by nothingspecial on 2010-12-10
I take it rpc has been well and truly found :p

---

### Post by Habitual on 2010-12-10
Once you get used to it (as with all things Linux) find is a gem.
I use `pwd` instead of -print and have setup an easy alias to use it easily...

alias find='find /home/jj -name'

So typing find *123* spits out this result:
```
/home/jj/Pictures/01232_lazydaysii_1280x1024.jpg
/home/jj/.Skype/my-kungfu/chatsync/12/123b150be87c9302.dat
/home/jj/.mozilla/firefox/oumkz0pb.default/Cache/93A123CFd01
/home/jj/.config/ubuntu-tweak/sourcecenter/sourcecenter/logo/matthaeus123-mrw-gimp-svn-logo.png
/home/jj/.thumbnails/normal/76123a8ba85b3f0f9e865a8daa3791c9.png
/home/jj/.thumbnails/normal/6fdd0d1acd1450f5eb27c94123cb03fd.png
/home/jj/.thumbnails/normal/8ea71648db18cb0123bf8806bda251bc.png

```

Easy cheesey, no?

Just another possible option to consider.

HTH.

---

### Post by bdemers on 2010-12-10
OMG, locate is outrageous!

Thanks for all the time you people have given me.  Great.

---

### Post by jim_deadlock on 2010-12-10
It is, isn't it :)  The only thing to watch out for is if you're trying to locate recently-created files, always remember to run updatedb first, otherwise the new files won't be found.

You could mark this thread as SOLVED too.

---

### Post by bdemers on 2010-12-10
Thanks for the headup with updatedb.

I'll mark as solved

---

