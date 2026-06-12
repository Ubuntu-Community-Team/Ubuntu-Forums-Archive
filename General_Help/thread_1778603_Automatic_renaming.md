---
title: "Automatic renaming"
date: 2011-06-09
forum: General Help
---

### Post by Vasar on 2011-06-09
I have pictures on two sdcards and they have the same names, I want to copy them to folder in Linux but they are the same name and there isn't automatic renaming option in Ubuntu like there is in Windows. I tried to rename already existing pictures in the folder with rename command in terminal, but without no luck. Then I tried with mrename and again nothing happened.

I really don't understand the rename command, I typed in this:

```
rename -n ’s/\.JPG$/\.JPG/’ *.JPG
```

and got this :

```
Unrecognized character \xE2 in column 1 at (eval 1) line 1.
```

I'm sure it's wrong so could you help me please? I want to rename all the .JPG files in that folder. 

Thank you!

---

### Post by matt_symes on 2011-06-09
Hi
[FONT=monospace]
[/FONT]```
[FONT=monospace]rename -n &#8217;s/\.JPG$/\.JPG/&#8217; *.JPG[/FONT]
```[FONT=monospace]The quotes are incorrect. Try this.
[/FONT]
```
rename -n 's/\.JPG$/\.JPG/' *.JPG
```Does this command do what you want ? Exactly how do you want to rename them ?

Have a look at 

```
man rename
```Kind regards

---

### Post by hawthornso23 on 2011-06-09
If I understand what you are trying to do then something like 

```
cp -b *.jpg targetdirectory
```

might do the job. The -b option to the copy command makes backups of existing files using a trailing ~ or numerical suffix. 

```
 man cp
```

to read about the details. Suggest you create a few test directories and check that it does what you want.

---

### Post by matt_symes on 2011-06-09
Hi

I concur with [hawthornso23]("http://ubuntuforums.org/member.php?u=867217") here. 

The rename command you have posted will not do what you want i think (although i will point out the syntactical error) and if you are just trying to copy you can rename while copying.

I am not really following the process you are envisaging.

Kind regards

---

