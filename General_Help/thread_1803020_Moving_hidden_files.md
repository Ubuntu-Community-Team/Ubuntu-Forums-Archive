---
title: "Moving hidden files"
date: 2011-07-12
forum: General Help
---

### Post by holadebob on 2011-07-12
Can I change the destination for hidden files that are in the Home Directory? I'd like to put all the hidden files in my Home directory into a seperate folder inside of Home. (10.04)
Thank you

---

### Post by jerrrys on 2011-07-12
if you change the path of the hidden files, your system will no longer be able to locate them.  is there a reason you need to do this?

---

### Post by WorMzy on 2011-07-12
```
mv ~/.* [COLOR="Red"]/path/to/destination[/COLOR]
```

Note that this will move directories too. If you jsut want to move files, try this:

```
find ~ -maxdepth 1 -type f -iname ".*" -exec mv {} [COLOR="Red"]/path/to/destination[/COLOR] \;
```

---

### Post by seawolf167 on 2011-07-12
> **jerrrys said:**
> if you change the path of the hidden files, your system will no longer be able to locate them.  is there a reason you need to do this?

+1 

The programs/packages/calls to the static hidden files will not be able to find them and those configurations, etc. won't be used...

---

### Post by ajgreeny on 2011-07-12
This is not quite what you asked about, to which the simple answer is "No", but it is possible to separate all the config files and folders, (which **must** be in your /home partition or folder to work), from all your data files and folders by making a separate /data partition and mounting it at boot time with a simple edit of /etc/fstab.

This is especially useful if you have a dual boot with windows because the /data partition can be formatted to NTFS, then all the files and folders will be available to both OSs.

---

### Post by holadebob on 2011-07-12
I guess it isn't possible to just redirect the system to another folder for the hidden files.

My reason is to keep my Home folder a bit better organized. Scrolling down the long list of hidden folders to get to my files is no big deal, just requires a little more blurry eye time.

Thanks for the try.

---

### Post by jerrrys on 2011-07-12
move your hidden files into a separate home folder

---

### Post by seawolf167 on 2011-07-12
> **holadebob said:**
> My reason is to keep my Home folder a bit better organized. Scrolling down the long list of hidden folders to get to my files is no big deal, just requires a little more blurry eye time.

Why not just turn of the displaying of hidden files and folders?

---

### Post by doas777 on 2011-07-12
> **holadebob said:**
> I guess it isn't possible to just redirect the system to another folder for the hidden files.

My reason is to keep my Home folder a bit better organized. Scrolling down the long list of hidden folders to get to my files is no big deal, just requires a little more blurry eye time.

Thanks for the try.

just to clarify, there IS in fact a do link locations together: [Links]("http://en.wikipedia.org/wiki/Symbolic_link"). 
They probably aren't quite right for what you want to do, since a link to a folder is like having the folder there. as such, your folders would be moved, but they are replaced by links to folders. if you are doing this to clear them out of your home, then that approach is not for you. if you are trying to host them on more reliable media however, then that might work. 
to link a folder to a your home directory, use this command:
```
ln -s /path/to/new/location/of/folder ~
```

I'm sure you can work it into the script above.

---

### Post by jerrrys on 2011-07-12
reducing clutter by using links sounds counter productive

---

### Post by mikewhatever on 2011-07-12
> **WorMzy said:**
> ```
mv ~/.* [COLOR="Red"]/path/to/destination[/COLOR]
```



Actually, that would move everything. 
[http://beginnerlinuxtutorial.com/help-tutorial/basic-linux-commands/cp-linux-copy-command/](http://beginnerlinuxtutorial.com/help-tutorial/basic-linux-commands/cp-linux-copy-command/)

Edit: Scratch that.

---

### Post by holadebob on 2011-07-12
Seawolf, that's of course pretty easy to do, it would just require switching to view and checking or unchecking the box each time I were to look at a hidden file or one of my Home files. If the solution isn't obvious, I can live with it, was just curious.

---

### Post by doas777 on 2011-07-12
> **jerrrys said:**
> reducing clutter by using links sounds counter productive
my thought exactly. thats why I said as much.

---

### Post by jerrrys on 2011-07-12
well, did not sound that destructive to me.  when i said his .files, i meant his personal files

---

### Post by seawolf167 on 2011-07-12
> **holadebob said:**
> Seawolf, that's of course pretty easy to do, it would just require switching to view and checking or unchecking the box each time I were to look at a hidden file or one of my Home files. If the solution isn't obvious, I can live with it, was just curious.

What about using the default keyboard shortcut instead of clicking through the menus? I think it is [CTRL][H]

---

### Post by doas777 on 2011-07-12
> **jerrrys said:**
> well, did not sound that destructive to me.  when i said his .files, i meant his personal files
fair enough, a misunderstanding. to me the .Files are the hidden application config files that he wants to move. I agree, instead of moving his config out of his profile, separating the user files is a much better approach.

---

### Post by jerrrys on 2011-07-12
> **doas777 said:**
> fair enough, a misunderstanding. to me the .Files are the hidden application config files that he wants to move. I agree, instead of moving his config out of his profile, separating the user files is a much better approach.

yep, looks like seawolf has an idea

---

### Post by WorMzy on 2011-07-12
> **mikewhatever said:**
> Actually, that would move everything. 
[http://beginnerlinuxtutorial.com/help-tutorial/basic-linux-commands/cp-linux-copy-command/](http://beginnerlinuxtutorial.com/help-tutorial/basic-linux-commands/cp-linux-copy-command/)

I think that article is somewhat out of date.

Also, I used the mv command, not cp. ;)

EDIT:

```
wormzy@sakura[pts/3]:~/test$ ll -a
total 24
drwxr-xr-x  6 wormzy users 4096 Jul 13 01:12 ./
drwx------ 40 wormzy users 4096 Jul 13 01:15 ../
-rw-r--r--  1 wormzy users    0 Jul 13 00:09 1
-rw-r--r--  1 wormzy users    0 Jul 13 00:09 .2
-rw-r--r--  1 wormzy users    0 Jul 13 00:09 .3
-rw-r--r--  1 wormzy users    0 Jul 13 00:09 .4
-rw-r--r--  1 wormzy users    0 Jul 13 00:09 .5
drwxr-xr-x  2 wormzy users 4096 Jul 13 00:09 .6/
drwxr-xr-x  2 wormzy users 4096 Jul 13 00:09 .7/
drwxr-xr-x  2 wormzy users 4096 Jul 13 00:09 8/
drwxr-xr-x  2 wormzy users 4096 Jul 13 01:20 test2/
wormzy@sakura[pts/3]:~/test$ ll -a test2 
total 8
drwxr-xr-x 2 wormzy users 4096 Jul 13 01:20 ./
drwxr-xr-x 6 wormzy users 4096 Jul 13 01:12 ../
wormzy@sakura[pts/3]:~/test$ cp -r .* test2 
wormzy@sakura[pts/3]:~/test$ ll -a test2   
total 16
drwxr-xr-x 4 wormzy users 4096 Jul 13 01:20 ./
drwxr-xr-x 6 wormzy users 4096 Jul 13 01:12 ../
-rw-r--r-- 1 wormzy users    0 Jul 13 01:20 .2
-rw-r--r-- 1 wormzy users    0 Jul 13 01:20 .3
-rw-r--r-- 1 wormzy users    0 Jul 13 01:20 .4
-rw-r--r-- 1 wormzy users    0 Jul 13 01:20 .5
drwxr-xr-x 2 wormzy users 4096 Jul 13 01:20 .6/
drwxr-xr-x 2 wormzy users 4096 Jul 13 01:20 .7/
```

---

### Post by holadebob on 2011-07-12
Sounds like a workable solution to me, thank you!

---

### Post by mikewhatever on 2011-07-13
@WorMzy
Yes, you are right. Thanks for clarifying that.O:)

---

