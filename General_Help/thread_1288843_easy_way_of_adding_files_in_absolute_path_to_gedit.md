---
title: "easy way of adding files in absolute path to gedit in bash"
date: 2009-10-11
forum: General Help
---

### Post by of_darkness on 2009-10-11
As i want to spare my self the trouble of having to cd to the directory where i have the files i want to edit whit say gedit or kate or if i want to browse several subdirectories in a path whit nautilus or konqueror i now have to add the the full path to the actual file/directory several times over for each one of the files or directory's.
 
 Therefore i wonder if there is any way of copying the last path entered before space in a row in bash?
 
 ex:
 
 /home/user name/abc/def/gde/test-file1 /home/username/abc/def/gde/not-the-first-test-file /home/username/abc/def/gde/but-yet-another-file-whit-an different name.
 
 and here i wonder if i could make bash remember the /home/username/abc/def/gde/ path so that i only need to specify the file?
 
I know that i can cd to the directory and the just use the filenames as arguments, but that is what i don't want to have to do. and yea i could also just copy the path but no i want bash to do it for me more or less.

Is this possible? or is it possible whit some bash.rc editing or am i out of luck here?

---

### Post by kerry_s on 2009-10-11
in gedit there is a browser plugin, just click away. :)
and that is a full browser, you have right click options & if you click the current folder dropdown you can access to the bookmarks.

---

### Post by of_darkness on 2009-10-12
Na im loking for doing it from cli as the directory path may differ from time to time and most of the time and most of the time i nead super user perms.

Thats why i almoust always starts kate,gedit,konqueror,nautilus from cli as i can use the tab autocompleting in bash as it gives less kestrockes.

---

### Post by t0p on 2009-10-12
The only things I can think of that may help you with this are autocompletion by pressing <Tab>, and highlighting text with the mouse and copy-pasting.  But you're probably aware of these options already.

In cli, you can drop a sub-directory (eg from /home/user/Pictures/Paris/November to /home/user/Pictures/Paris) with the command

```
cd ..
```but if you don't want to change directories that isn't going to be much use.

Sorry.

---

### Post by vttay03 on 2009-10-12
In my .bashrc file, I have a line similar to the following

```

alias cdb='cd ~/bin' 

```

which allows me to just type 'cdb' at the bash prompt and end up in my personal bin directory.  Not sure if this is what you were looking for or not....

---

### Post by vttay03 on 2009-10-12
I guess I didn't really explain...I meant to say that you could add something like the following:

```

alias blah='cd /home/username/abc/def/gde'

```

That way, you could just type 'blah' at the bash prompt.

---

### Post by diesch on 2009-10-12
I'm not quite sure if I understand what you want, but maybe it's 
```
gedit '/home/user name/abc/def/gde/'{test-file1,not-the-first-test-file,'but-yet-another-file-whit-an different name'}
```

---

### Post by lswb on 2009-10-12
Not an answer for your original question, but possibly of interest, pressing <Alt .>
(Alt key and period . key) at the same time will repeat the arg1 from the previous bash command.

Another thing you might try is making a symbolic link to your deeply nested directory so you don't have to type as much:

ln -s /path/to/your/deep/directory shortpath

Then you could just type gedit shortpath/file1 shortpath/file2 shortpath/etc

---

### Post by mechro on 2009-10-12
Is this any good?...

> **history**: print a listing of most recent commands the user has entered. You can then
repeat a command using the !. For instance !110 will repeat the command with the
label 110 from the history listing.

---

### Post by lensman3 on 2009-10-12
Look at the "pushd", "popd", "dirs" commands in bash.  

Also look at the bash environment variable called "CDPATH".

---

### Post by of_darkness on 2009-10-12
> **lensman3 said:**
> Look at the "pushd", "popd", "dirs" commands in bash.  

Also look at the bash environment variable called "CDPATH".

well not bad but still not easier for me in most cases.

---

### Post by of_darkness on 2009-10-12
> **mechro said:**
> Is this any good?...

Nupp, as i want to reapeat the last directory path string i typed on the same row. 

i type gedit first then comes the part that i want to auto copy /etc/grub.d/-file- then here i want to paste the /etc/grub.d path that i typed before on the same row.

/etc/grub.d /etc/grub.d /etc/grub.d
 first entry   1st copy     second copy

and i want to autocomplete so that i dont have to type so mouch.

---

### Post by of_darkness on 2009-10-12
> **lswb said:**
> Not an answer for your original question, but possibly of interest, pressing <Alt .>
(Alt key and period . key) at the same time will repeat the arg1 from the previous bash command.

Another thing you might try is making a symbolic link to your deeply nested directory so you don't have to type as much:

ln -s /path/to/your/deep/directory shortpath

Then you could just type gedit shortpath/file1 shortpath/file2 shortpath/etc
  Well try not to use so many symbolic likns and espcialy not in my /home path so that i dont delate stuff by misstake and some other not screwing upp my sys more then nececery reasons.(well i do it alot anyway but :P)

---

### Post by of_darkness on 2009-10-12
> **diesch said:**
> I'm not quite sure if I understand what you want, but maybe it's 
```
gedit '/home/user name/abc/def/gde/'{test-file1,not-the-first-test-file,'but-yet-another-file-whit-an different name'}
```
  It would have been if i could autocomplete the filenes in {}, but without it, it is pointless as i nead to know and spell the filenames correctly, and manuly spelling is the worst way of doing somthing:/

---

### Post by of_darkness on 2009-10-12
> **vttay03 said:**
> I guess I didn't really explain...I meant to say that you could add something like the following:

```

alias blah='cd /home/username/abc/def/gde'

```That way, you could just type 'blah' at the bash prompt.

Well the point is that i dont want to change wd., and aliases is not realy a good sollution for anything realy i found out because most commands dont understand them.

---

### Post by diesch on 2009-10-12
> **of_darkness said:**
> It would have been if i could autocomplete the filenes in {}, but without it, it is pointless as i nead to know and spell the filenames correctly, and manuly spelling is the worst way of doing somthing:/

zsh can autocomplete there.

---

### Post by of_darkness on 2009-10-15
> **diesch said:**
> zsh can autocomplete there.
  Well zsh is a huge project to get it smoth enough to have as defaul shell.. i would gess for me it would be about a year:s worth of tangeling n testing before it could be an solution for me..:/

---

### Post by lswb on 2009-10-15
Use this sequence:

$ DIR=/path/to/deeply/nested/directory

$ gedit $DIR/file1 $DIR/file2 $DIR/file3

---

