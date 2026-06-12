---
title: "Shell help"
date: 2010-05-05
forum: General Help
---

### Post by ironic.demise on 2010-05-05
This just doesn't work...
I would like to know why

I would also like to know how to add am
if command to ask wether or not to copy the backups
I would also like a way of using read to ask for user input at the shell to change or set the source destination?

Tried a lot to get this working but now I can't see what's wrong


```

cp ~/Home/Samuel/Documents/Backups/Website/2 ~/Home/Samuel/Documents/Backups/Website/3 
cp ~/Home/Samuel/Documents/Backups/Website/1 ~/Home/Samuel/Documents/Backups/Website/2 
cp ~/Home/Samuel/Documents/Source ~/Home/Samuel/Documents/Backups/Website/1

echo --------------------
echo Compiling Index.html
echo --------------------
rm ~/Home/Samuel/Desktop/Web_server/unacquainted/index.html
cat ~/Home/Samuel/Documents/Source/html.txt > ~/Home/Samuel/Desktop/Web_server/unacquainted/index.html
cat ~/Home/Samuel/Documents/Source/Head.txt >> ~/Home/Samuel/Desktop/Web_server/unacquainted/index.html
cat ~/Home/Samuel/Documents/Source/Body.txt >> ~/Home/Samuel/Desktop/Web_server/unacquainted/index.html
cat ~/Home/Samuel/Documents/Source/universal.txt >> ~/Home/Samuel/Desktop/Web_server/unacquainted/index.html
cat ~/Home/Samuel/Documents/Source/index.txt >> ~/Home/Samuel/Desktop/Web_server/unacquainted/index.html
cat ~/Home/Samuel/Documents/Source/intensedebate.txt >> ~/Home/Samuel/Desktop/Web_server/unacquainted/index.html
cat ~/Home/Samuel/Documents/Source/end.txt >> ~/Home/Samuel/Desktop/Web_server/unacquainted/index.html
 
```

---

### Post by ironic.demise on 2010-05-05
Realized I need to remove the /Home/Samuel as ~ entials it :S
still not getting the desired effect though :(

---

### Post by StuartN on 2010-05-05
> **ironic.demise said:**
> This just doesn't work...
I would like to know why

What doesn't work, i.e. what happens, what do you expect, and what is the difference? For example, I think you need the -r (recursive) option to create a duplicate of a directory structure:

```
cp **-r** ~/Home/Samuel/Documents/Backups/Website/2 ~/Home/Samuel/Documents/Backups/Website/3
```

> **ironic.demise said:**
> command to ask wether or not to copy the backups

**cp -i** is interactive copy which will copy files as usual, but ask before overwriting anything. You could also use shell read and exit if the user does not type "y" or "Y":

```
echo -n "Run the backup: (y or n): "
read CONTINUE
if [ "$CONTINUE" != "y" -a "$CONTINUE" != "Y" ] ; then exit ; fi
...<backup commands>...
```

> **ironic.demise said:**
> I would also like a way of using read to ask for user input at the shell to change or set the source destination

I would not use read as follows, because it is too easy to enter an incorrect path:

```
echo -n "Enter the backup path: "
read MY_PATH
cp x $MY_PATH
```

Instead I would use some kind of dialog generator to bring up a file selection dialog to pick a path:

```
MY_PATH=`zenity --file-selection --title="Choose a backup directory"`
if [ $? eq 0 ] ; then <backup> ; fi ;
```

(I am not certain that Zenity will pick a path, or allow the creation of a new one, but it should do).

---

### Post by ironic.demise on 2010-05-05
> **StuartN said:**
> What doesn't work, i.e. what happens, what do you expect, and what is the difference? For example, I think you need the -r (recursive) option to create a duplicate of a directory structure:

```
cp **-r** ~/Home/Samuel/Documents/Backups/Website/2 ~/Home/Samuel/Documents/Backups/Website/3
```



**cp -i** is interactive copy which will copy files as usual, but ask before overwriting anything. You could also use shell read and exit if the user does not type "y" or "Y":

```
echo -n "Run the backup: (y or n): "
read CONTINUE
if [ "$CONTINUE" != "y" -a "$CONTINUE" != "Y" ] ; then exit ; fi
...<backup commands>...
```



I would not use read as follows, because it is too easy to enter an incorrect path:

```
echo -n "Enter the backup path: "
read MY_PATH
cp x $MY_PATH
```

Instead I would use some kind of dialog generator to bring up a file selection dialog to pick a path:

```
MY_PATH=`zenity --file-selection --title="Choose a backup directory"`
if [ $? eq 0 ] ; then <backup> ; fi ;
```

(I am not certain that Zenity will pick a path, or allow the creation of a new one, but it should do).

Recursive... That helped, Seems like it wasn't copying things the way that they were laid out in the html!

Now everything is copying fine :]

I think I'll look into zenity.

before that I'll try the copy command.

Is it possible to use read to add a new file to the script itself with something like

echo enter new flie
read file
echo cp source/$file server/$file >> compilerfile

??

explain why the $continue=y has an exclamation mark and a -a? I assume fi means to end if?

it's all way more complicated than CMD @_@

---

### Post by StuartN on 2010-05-05
> **ironic.demise said:**
> explain why the $continue=y has an exclamation mark and a -a? I assume fi means to end if?

```
if [ "$CONTINUE" != "y" -a "$CONTINUE" != "Y" ] ; then exit ; fi

```

The test was if $CONTINUE is not equal (!=) to "y" and (-a) $CONTINUE is not equal to "Y", then exit the script before the commands that run the backup.

You can lay out the if command across multiple lines if you want, and you are correct that fi ends the if construct.

You can use read as you suggest to accept a new directory - you might want to check that the typed response is not blank and does not overwrite anything etc.

---

### Post by ironic.demise on 2010-05-05
Much appreciated, I think I have enough info to get everything rolling now, You've been a great help :) Just need to get into everything on Ubuntu and get used to it.

---

### Post by Old *ix Geek on 2010-05-05
You're doing GREAT since I posted in your other thread late last night. :)

> **ironic.demise said:**
> it's all way more complicated than CMD @_@Yes, it is, but THAT'S why the *nix shell is so powerful!  Once you really explore its commands and their respective arguments, you'll be blown away by what you can do.

---

### Post by ironic.demise on 2010-05-06
> **Old *ix Geek said:**
> You're doing GREAT since I posted in your other thread late last night. :)

Yes, it is, but THAT'S why the *nix shell is so powerful!  Once you really explore its commands and their respective arguments, you'll be blown away by what you can do. I'm really happy to see that you're making great progress.

Not wanting to start a war here, but I tell you what: Grab yourself a copy of a UNIX shell scripting book such as [Mastering UNIX Shell Scripting]("http://www.amazon.com/Mastering-Unix-Shell-Scripting-Administrators/dp/0470183012/ref=pd_sim_b_1") (1032 pages) or [Linux Command Line and Shell Scripting Bible]("http://www.amazon.com/Linux-Command-Shell-Scripting-Bible/dp/047025128X/ref=pd_sim_b_1") (840 pages), take a couple months to really learn their contents, and then come back and we'll see how your opinion of "Windows can do a lot through CMD" has changed, okay? :lolflag: Seriously, once you're aware of the power of the *nix shell, you'll realize just how lacking the M$ equivalent truly is.

I'll take your advice, I'll try and make a fair opinion on everything, I want to become fairly good with all the os's and I've just spent more time on windows before actually getting Ubuntu to work. I'll try and get as good with it as I can. It's just a lot different,,, I've hda to throw away most of my Windows tricks and learn everything again.

really really helps having such help from the community, never had anything like this for windows or Mac

---

