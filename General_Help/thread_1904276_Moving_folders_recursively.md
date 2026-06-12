---
title: "Moving folders recursively"
date: 2012-01-04
forum: General Help
---

### Post by Calimerorulez on 2012-01-04
Hi :D

I'm looking for a recursive 'find' command that lets me move folders starting with the '(' character to another folder in the same parent folder.

I have some music folders that are organised like

A
[INDENT]ABBA[/INDENT]
    [INDENT][INDENT](2001) Blabla[/INDENT][/INDENT]
    [INDENT][INDENT](2002) Blabla234[/INDENT][/INDENT]
    [INDENT][INDENT]Album[/INDENT][/INDENT]
  [INDENT]ATB[/INDENT]
    [INDENT][INDENT](1999) Happy Sound[/INDENT][/INDENT]
    [INDENT][INDENT]Album[/INDENT][/INDENT]
B
  [INDENT]Beyonce[/INDENT]
    [INDENT][INDENT](2011) New Music[/INDENT][/INDENT]
    [INDENT][INDENT]Album[/INDENT][/INDENT]

My goal is to move all the folders starting with '(' into the Album folder in the same parent folder. Source folder can contain spaces.

Can anyone help?

---

### Post by carranty on 2012-01-04
> **Calimerorulez said:**
> My goal is to move all the folders starting with '(' into the Album folder in the same parent folder.

Sorry, I'm possibly just being thick but I don't quite understand what you're after, can you give an example.  For instance where would you like the *A/ABBA/(2001)\ Blabla/* folder moving too?

EDIT : Apologies, ignore the above, I've realised what you're asking

---

### Post by nothingspecial on 2012-01-04
Test this, I may have made a typo.

You don't need find if your directory structure is strict. If you do have Directories A-Z and in all of them is a directory Album. If the only directories in them starting with ( are the numbered ones (with dates) then

```
for f in *; do mv "$f"/\(* "$f"/Album; done
```

will do it, issued from the directory that contains the A-Z directories.

It puts A-Z in a variable then moves any directory starting with a ( into a directory named "Album" in the corresponding parent.

---

### Post by Calimerorulez on 2012-01-04
> **nothingspecial said:**
> Test this, I may have made a typo.

You don't need find if your directory structure is strict. If you do have Directories A-Z and in all of them is a directory Album. If the only directories in them starting with ( are the numbered ones (with dates) then

```
for f in *; do mv "$f"/\(* "$f"/Album; done
```

will do it, issued from the directory that contains the A-Z directories.

It puts A-Z in a variable then moves any directory starting with a ( into a directory named "Album" in the corresponding parent.

Well, I have directories A-Z, but underneath for example A, there are directories with artist names. In each artist directory, there are the directories starting with '(' and an Album directory, into which the '('-directories have to be copied. :D

edit: Other than that, I tried the command in the A folder itself and it works. Thanks!

---

### Post by carranty on 2012-01-05
> **Calimerorulez said:**
> Well, I have directories A-Z, but underneath for example A, there are directories with artist names. In each artist directory, there are the directories starting with '(' and an Album directory, into which the '('-directories have to be copied. :D

I think a slight alteration to nothingsspecial's script will sort it

```
for f in *; do for g in "$f"/*; do mv "$g"/\(* "$g"/Album; done ; done
```

That command should work from the parent directory (the one containing the folders A-Z).

---

### Post by nothingspecial on 2012-01-05
Or just for ```
f in */* ......
``` instead of nested for loops, although both will work :)

---

