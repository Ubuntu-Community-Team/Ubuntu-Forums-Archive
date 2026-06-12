---
title: "rm help"
date: 2010-04-21
forum: General Help
---

### Post by Loves SSH on 2010-04-21
Hi folks,

I'm a relative cli noob, and I need some help before I screw something up. I want to remove some files by extension only, going down several folders, while leaving everything else be. I think this might be the the right command / syntax, can someone confirm:

```
rm -rf *.exe *.ini *.!ut /path/
```

---

### Post by klemes on 2010-04-21
No this script won't certainly do what you intend it to do and please simply do not use
it.
I think you will need a more complex command line or small bash script using find and rm commands together withh right options.
I would like to help more but not exactly a bash expert.Better wait for someone more knowledgeable  in these matters suggest the correct command syntax.

---

### Post by patchwork on 2010-04-21
You can use the find command with options for depth and the delete action.  See the man page ```
man find
```

---

### Post by dwarfolo on 2010-04-21
klemens is rigth.
That command is going to destroy any files matching *.exe *.ini *.lut AND the entire /path/ directory.
You had better to use find.
Try this
```
find /path -depth \( -name '*.exe' -o -name '*.ini' -o -name '*.lut' \) -exec rm -f {} \;

```
EDIT: beware of the white space at the end of the coomand line, just before \;

---

### Post by klemes on 2010-04-21
From the find manual page:

```
find /tmp -name core -type f -print | xargs /bin/rm -f

       Find  files  named  core in or below the directory /tmp and delete them.  Note that this
       will work incorrectly if there are any filenames containing newlines, single  or  double
       quotes, or spaces.

```so something like :

find /PATH -name *.ini -type f -print | xargs /bin/rm -f

and

find /PATH -name *.exe -type f -print | xargs /bin/rm -f

should do the job for you.

Better wait again for someone more knowledgeable to confirm this and then hit it!!!!:)


EDIT: sorry did not see the previous post as I was writing the above....:)

---

### Post by dwarfolo on 2010-04-21
I usually check things like this using the -print option in find.
So for example you can do :
```
find /path -depth \( -name '*.exe' -o -name '*.ini' -o -name '*.lut' \) -print
```
and just see what *find* .... finds. Then you can safely procede with the actual operation you need to perform.

---

### Post by sisco311 on 2010-04-21
EDIT: Wow, I'm slow... :)

You can use the find command to search for the files recursively in /path & it's subdirectories:
```
find /path \( -iname "*.exe" -o -iname "*.ini" -o -iname "*.\!ut" \)
```

See: 
[uhelp]community/find[/uhelp]

NOTE: ! is a special character, you have to escape it:
```
man bash | less +/"Event Designators"
man bash | less +/^QUOTING
```

and the gvfs-trash command to move the files in the trash:
```
find /path \( -iname "*.exe" -o -iname "*.ini" -o -iname "*.\!ut" \) -exec gvfs-trash '{}' +;
```

or -delete option to remove the files:
```
find /path -depth \( -iname "*.exe" -o -iname "*.ini" -o -iname "*.\!ut" \) -delete
```

BE CAREFUL! First run the command without the -delete option.

---

### Post by jpaugh64 on 2010-04-21
By /path/, do you mean to delete every exe file in one of the directories in the $PATH variable, or do you actually have a folder *named* path. To do the former, you could use something like
```
rm  -i `echo $PATH | sed 's/:/\/{exe,ini} /g'` 
```But then you would have to manually check for the files that you want to keep, and it would not go into subdirectories. By the way, I didn't try this command, and neither should you.

edit: rm doesn't even seem to expand stuff in braces the way that I had hoped. That is probably for the best.

---

### Post by john newbuntu on 2010-04-21
One small note here, before you run any such commands, replace "rm -f" with "ls -l".  

```
  find /home/user -depth \( -name '*.exe' -o -name '*.ini' -o -name '*.lut' \) -exec ls -l {} \;
```This way, you will get a list of all files that will actually get deleted once you run the actual command with rm -f.

---

### Post by Loves SSH on 2010-04-21
Thanks a lot guys, and in particular, sisco311, worked like a charm!!

---

