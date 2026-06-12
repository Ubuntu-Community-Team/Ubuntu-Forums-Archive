---
title: "advanced options in cp"
date: 2012-10-06
forum: General Help
---

### Post by IAMTubby on 2012-10-06
Hey,
How do you copy something from source to destination, even if the path to destination doesn't currently exist and it has to be made on the fly ?

```

$cp CopyThisFile.txt /This/Path/Has/To/Be/Made/

```

Something like the -p option in mkdir.

Thanks.

---

### Post by raja.genupula on 2012-10-06
This is what i think you are asking

>  -P, --parents[INDENT]Preserve intermediate directories in source. The last  argument must be the name of an existing directory. For example, the  command:
  cp --parents jphekman/book/ch1 newdir 
 copies the file jphekman/book/ch1 to the file newdir/jphekman/book/ch1, creating intermediate directories as necessary.
[/INDENT]          

---

