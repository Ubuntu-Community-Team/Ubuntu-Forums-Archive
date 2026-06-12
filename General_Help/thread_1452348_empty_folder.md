---
title: "empty folder"
date: 2010-04-11
forum: General Help
---

### Post by catlover2 on 2010-04-11
i would like to make a copy of a folder with  all its sub-folders but without any of the  files that are in it.
thanks!

---

### Post by catlover2 on 2010-04-12
bump

---

### Post by catlover2 on 2010-04-19
> **catlover2 said:**
> bump
bump

---

### Post by chris.jericho on 2010-04-19
never heard of something like this before

---

### Post by His on 2010-04-19
copy the folder recursively, then remove the files

---

### Post by kaibob on 2010-04-19
I have used the first method suggested in the following FAQ, and it worked fine:

[http://mywiki.wooledge.org/BashFAQ/010](http://mywiki.wooledge.org/BashFAQ/010)

---

### Post by catlover2 on 2010-04-19
> **His said:**
> copy the folder recursively, then remove the files


we are talking about maybe 50-75 sub-folders here, so that seems like it'd be tedious!

---

### Post by catlover2 on 2010-04-19
> **kaibob said:**
> I have used the first method suggested in the following FAQ, and it worked fine:

[http://mywiki.wooledge.org/BashFAQ/010](http://mywiki.wooledge.org/BashFAQ/010)

and, I'm a _complete _beginner at Linux, so the terms used there don't make much sense to me.

---

### Post by kaibob on 2010-04-19
> **catlover2 said:**
> and, I'm a _complete _beginner at Linux, so the terms used there don't make much sense to me.

Do the following:

1) Open a terminal window and change to the directory that contains the directories that you want to copy.

2) Enter the following command in the terminal window. You have to change /home/kaibob/temp to whatever you want to use as the target directory. Make double sure that you are in the correct source directory before running the command. After running the command, some directory information will be output to the terminal window. Just ignore that. 

```
find . -type d -print | cpio -pdumv /home/kaibob/temp
```

I just did the above, and it worked fine.

---

### Post by catlover2 on 2010-04-20
> **kaibob said:**
> Do the following:

1) Open a terminal window and change to the directory that contains the directories that you want to copy.

2) Enter the following command in the terminal window. You have to change /home/kaibob/temp to whatever you want to use as the target directory. Make double sure that you are in the correct source directory before running the command. After running the command, some directory information will be output to the terminal window. Just ignore that. 

```
find . -type d -print | cpio -pdumv /home/kaibob/temp
```I just did the above, and it worked fine.


dang, it won't cd for some reason.
```
reed@reeds-laptop:~$ cd Reeds Pictures5
bash: cd: Reeds: No such file or directory
reed@reeds-laptop:~$ 
```

---

### Post by nothingspecial on 2010-04-20
A couple of pointers.

First, linux is case sensetive - Reeds and reeds are 2 different things.

Second, the ~ before the $ indicates that you are already in reeds

```
cd Pictures5
``` maybe?

---

### Post by catlover2 on 2010-04-21
> **nothingspecial said:**
> A couple of pointers.

First, linux is case sensetive - Reeds and reeds are 2 different things.

Second, the ~ before the $ indicates that you are already in reeds

```
cd Pictures5
``` maybe?


yes, but Reeds Pictures5 is on a external HD, and "Reeds Pictures5" is 1 folder.

---

### Post by loriamanta on 2010-04-21
[COLOR=#000000][FONT=Times New Roman][COLOR=#333333][FONT=arial]After completing an email and pressing send, a message pops up saying, "this message cannot be sent due to an empty folder." 

[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by nothingspecial on 2010-04-21
> **catlover2 said:**
> yes, but Reeds Pictures5 is on a external HD, and "Reeds Pictures5" is 1 folder.

In that case you need to specify the full path and escape the space

```
cd /media/name_of_external_drive/Reeds\ Pictures5
```

---

### Post by catlover2 on 2010-04-21
> **nothingspecial said:**
> In that case you need to specify the full path and escape the space

```
cd /media/name_of_external_drive/Reeds\ Pictures5
```

```
reed@reeds-laptop:~$ cd /media/Reeds Pics 2/Reeds\ Pictures5
bash: cd: /media/Reeds: No such file or directory
reed@reeds-laptop:~$ cd /media/Reeds_Pics_2/Reeds\ Pictures5
bash: cd: /media/Reeds_Pics_2/Reeds Pictures5: No such file or directory
reed@reeds-laptop:~$ cd /media/Reeds Pics 2_/Reeds\ Pictures5
bash: cd: /media/Reeds: No such file or directory
reed@reeds-laptop:~$ cd /media/A611-2EA3/Reeds\ Pictures5
bash: cd: /media/A611-2EA3/Reeds Pictures5: Permission denied
reed@reeds-laptop:~$ sudo cd /media/A611-2EA3/Reeds\ Pictures5
[sudo] password for reed: 
sudo: cd: command not found
reed@reeds-laptop:~$ 

```



not sure why it still won't do it.

---

### Post by nothingspecial on 2010-04-21
> **catlover2 said:**
> ```
reed@reeds-laptop:~$ cd /media/Reeds Pics 2/Reeds\ Pictures5
 

```



not sure why it still won't do it.

Bash does not like spaces in file names, in that, it interprets a space as the end of what you want to do (sort of)

If you type ```
cd Reeds Pics 2
```

Bash will look for Reeds, it will look at the bit after the space to see if it is an option etc and if it doesn`t recognise it, it will try to do the first thing you told it to do.

Which, as far as bash is concerned is ```
cd Reeds
```

You need to escape spaces (all of them) in bash.

You can do this in a number of ways.

Use slashes (bash`s escape character)

```
cd Reeds\ Pics\ 2
```

every time bash sees a \ it will treat the space literally instead of a special character.

Or you could
```

cd "Reeds Pics 2"
```

Bash will interpret everything inside the quote literally.

I`ve kind of over simplified this (a lot), but I hope you see what I mean.

---

### Post by catlover2 on 2010-04-23
```

reed@reeds-laptop:~$ cd "Reeds Pictures5"
bash: cd: Reeds Pictures5: No such file or directory
reed@reeds-laptop:~$ reed@reeds-laptop:~$ cd /media/Reeds Pics 2/"Reeds Pictures5"
reed@reeds-laptop:~$: command not found
reed@reeds-laptop:~$ cd /media/Reeds Pics 2/"Reeds Pictures5"bash: cd: /media/Reeds: No such file or directory
reed@reeds-laptop:~$ 

```what now?:redface:

---

### Post by nothingspecial on 2010-04-24
> **catlover2 said:**
> ```

reed@reeds-laptop:~$ cd "Reeds Pictures5"
bash: cd: Reeds Pictures5: No such file or directory
reed@reeds-laptop:~$ reed@reeds-laptop:~$ cd /media/[COLOR="Red"]Reeds\ Pics [/COLOR]2/"Reeds Pictures5"
reed@reeds-laptop:~$: command not found
reed@reeds-laptop:~$ cd /media/[COLOR="Red"]"Reeds Pics 2"[/COLOR]/"Reeds Pictures5"bash: cd: /media/Reeds: No such file or directory
reed@reeds-laptop:~$ 

```what now?:redface:

You have to escape ALL the spaces.

---

### Post by KdotJ on 2010-04-24
To make this simple, just put the path in quotation marks

```
cd "/media/Reeds Pics 2/Reeds Pictures5"
```

Providing of course that the "Reeds Pics 2" is successfully mounted.

---

### Post by catlover2 on 2010-04-26
> **KdotJ said:**
> To make this simple, just put the path in quotation marks

```
cd "/media/Reeds Pics 2/Reeds Pictures5"
```Providing of course that the "Reeds Pics 2" is successfully mounted.

```
reed@reeds-laptop:~$ cd "/media/Reeds Pics 2/Reeds Pictures5"bash: cd: /media/Reeds Pics 2/Reeds Pictures5: Permission denied
reed@reeds-laptop:~$ sudo cd "/media/Reeds Pics 2/Reeds Pictures5"
sudo: cd: command not found
reed@reeds-laptop:~$ 

```


"Permission denied"

what's that about?

---

### Post by overlordchin on 2010-04-26
Ok so try this instead...

go to the parent dir of the one you want to copy. If you wanted to copy the subcontents of firefox you would want to be in the firefox directory or pics 5 or whatever you want to copy.

next type the following:

tree -dfli > /home/username/listodirs

sed 's/\ /\\\ /g' /home/username/listodirs > changes; mv changes /home/username/listodirs

for file in `cat listodirs`; do mkdir -p ~/targetdir/$file; done

This should recursively create the entire directory structure minus the files line by line. You might need to install tree by "sudo apt-get install tree" Also note that on the for loop I am using a backtick (the char next to the 1 on your keyboard) and not a single quote.


What this does is first caps a list of dirs to a file which you then do a search and replace on for white spaces with escape characters. Then you iterate through the file and create a dir with the -p flag which will attempt to create every directory in the path name. So if any folder in the path doesnt exist yet it will create it. IF any do already it ignores them and creates the rest.



NOTES ABOUT THIS POST

* the paths in the commands above contain /home/username where username should be your actual username on the machine. IE if you logon as catlover it would be "/home/catlover"

*the path that contains targetdir should be the path you want to copy everything to. Replace "targetdir" with the directory name you are copying things to. Just remember if it has spaces to escape them (Pics from the wedding) would be (Pics\ from\ the\ wedding)

* you can cut and past the commands above one line at a time after making the changes notes above.

---

### Post by overlordchin on 2010-04-26
Also note in response to your earlier post you can not 
"sudo cd"

If you want to be in a dir as root you need to be root first by "sudo su -"

That is sort of dangerous though and you should probably just add readwrite permissions to the folders you are using


chmod -R +rw directorytochange

this will recursively add permissions to the folders / files you are messing with. If it is on an external drive then you will need to mount it with read write permissions instead of using chmod.

---

### Post by nothingspecial on 2010-04-26
> **overlordchin said:**
> Ok so try this instead...

go to the parent dir of the one you want to copy. If you wanted to copy the subcontents of firefox you would want to be in the firefox directory or pics 5 or whatever you want to copy.

next type the following:

tree -dfli > /home/username/listodirs

next 

sed 's/\ /\\\ /g' /home/username/listodirs > changes; mv changes /home/username/listodirs

for file in `cat listodirs`; do mkdir -p ~/targetdir/$file; done

This should recursively create the entire directory structure minus the files line by line. You might need to install tree by "sudo apt-get install tree" Also note that on the for loop I am using a backtick (the char next to the 1 on your keyboard) and not a single quote.


What this does is first caps a list of dirs to a file which you then do a search and replace on for white spaces with escape characters. Then you iterate through the file and create a dir with the -p flag which will attempt to create every directory in the path name. So if any folder in the path doesnt exist yet it will create it. IF any do already it ignores them and creates the rest.

I`m not wishing to be rude to you, or Reeds - the cat lover.

But if he/she has not yet understood the way you navigate the linux file system, your posts, in this thread are way too advanced .....


..... it took me 2 or 3 reads.

---

### Post by overlordchin on 2010-04-26
> **nothingspecial said:**
> I`m not wishing to be rude to you, or Reeds - the cat lover.

But if he/she has not yet understood the way you navigate the linux file system, your posts, in this thread are way too advanced .....


..... it took me 2 or 3 reads.

If I have to dumb it down I will but perhaps you should let them read it and ask any questions if they have them. The commands are set up in a way that they can be cut and pasted into the command line. As long as he/she is in the appropriate place it should work.

---

### Post by nothingspecial on 2010-04-26
> **catlover2 said:**
> [CODE]]


"Permission denied"

what's that about?

Well the fact you are denied permission means you are accessing the folder you want. You have to change the ownership of it it to you.

---

### Post by catlover2 on 2010-04-26
> **overlordchin said:**
> ...If I have to dumb it down I will...

yes, thatsounds like a good idea:redface:

---

### Post by overlordchin on 2010-04-26
> **catlover2 said:**
> yes, thatsounds like a good idea:redface:

ok lets try this again: cut and paste each command one at a time

**step one**: - install tree -

from a command line type 

```
sudo apt-get install tree
```

say yes if it asks for confirmation


**step two**: 

change directories to the dir you want to copy.

```
cd /media/dirnamehere
``` if you start to type the directory you can press "Tab" on your keyboard and it will auto-complete directory names.


**step three**: 

Run a recursive tree with the following command

```
tree -dfli > /home/username/listodirs
```

where username = reed or whatever name you logon your computer with. listofdirs is a temporary file we are creating


**Step four**:

clean up tree output. Tree leaves white spaces in the file we made so we need to remove them by running the following command cut and paste this into the command line

```
sed 's/\ /\\\ /g' /home/username/listodirs > changes; mv changes /home/username/listodirs
```

IF you get a permission denied here then you do not have write permissions on the external drive. You can fix the error by putting /home/username in front of changes in both places in the previous command. So it should be /home/username/changes.


**Step five**:

Make a for loop to process the whole thing. Run the following command replacing the path "/targetdir" with the name of the folder you are copying your stuff to. So it would be like "/home/reed/mybackuppics"

Cut and paste everything below in the block it is one giant command

```
for file in `cat /home/reed/listodirs`; do mkdir -p /targetdir/$file; done;
```

****** Make sure that after you change target dir you leave the "$file" there. So if you are copying this to a dir in your home directory called mybackups the targetdir part would look "/home/reed/mybackups/$file"** ****

This should recursively create the entire directory structure minus the files line by line. If you cut and paste everything it should work for you.

**NOTES ABOUT THIS POST**

* the paths in the commands above contain /home/username where username should be your actual username on the machine. IE if you logon as catlover it would be "/home/catlover"

*the path that contains targetdir should be the path you want to copy everything to. Replace "targetdir" with the directory name you are copying things to. Just remember if it has spaces to escape them (Pics from the wedding) would be (Pics\ from\ the\ wedding)

---

### Post by catlover2 on 2010-04-27
> **overlordchin said:**
> ...```
for file in `cat /home/reed/listodirs`; do mkdir -p /targetdir/$file; done;
```...
   

i got all [COLOR=Red]this![/COLOR]```
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
reed@reeds-laptop:~$ 


```

---

### Post by overlordchin on 2010-04-27
> **catlover2 said:**
> i got all [COLOR=Red]this![/COLOR]```
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
mkdir: cannot create directory `/picghost': Permission denied
reed@reeds-laptop:~$ 


```


ok the problem is /picghost is in the folder "/" which is like the C:\ for windows. You do not own "/". If you put the word "sudo" in front of the mkdir it will ask you for your password and then execute the loop as root thus fixing the permission error.

so change the last part to this:

```
for file in `cat /home/reed/listodirs`; do sudo mkdir -p /targetdir/$file; done;
```


hope that helps

---

### Post by overlordchin on 2010-04-29
Did that solve your issue Catlover?

---

### Post by catlover2 on 2010-04-29
> **overlordchin said:**
> Did that solve your issue Catlover?

no, so picghost is now there, but,
i do not see all of the folders that were in the external HD i was making
the folders out of, plus, 
there are also some ones i don't recognize, like:
->\ and Donut\ ect.

thanks all! 

catlover.

---

### Post by catlover2 on 2010-05-02
bump

---

