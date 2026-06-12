---
title: "Make find command ignore /media"
date: 2009-10-16
forum: General Help
---

### Post by rob86 on 2009-10-16
When I want to search every directory in "/" _except_ "/media" using find, what can I type?

---

### Post by spiderbatdad on 2009-10-16
find / -not -name "media"

?

---

### Post by rob86 on 2009-10-16
Doesn't that "not" display files with the name "media"?

I want to search my entire "Linux" drive but I want to avoid searching through everything in the /media/ directory of the file system, because it contains my other drives including cd's etc and I know the files im searching for aren't on them. It takes a while to search through all that so it makes searches take longer than I'd like.

I thought there'd be a command like

find / -not /media/ -name *FileName* but that doesn't work because -not only works on expressions, not paths.

---

### Post by rob86 on 2009-10-17
I'm thinking -xdev might be what I'm looking for.

find / -xdev -name 'filename'

This seems to work , though I haven't experimented much.

---

### Post by diesch on 2009-10-17
```
find / -path /media -prune -or -print
```

---

### Post by televisi on 2009-10-23
Hi diesch, I have similar [issue]("http://ubuntuforums.org/showthread.php?t=1298390").
I need to find large file from root folder, but exclude /data1 folder.
I use the following command:

```
sudo find / -size +300M -path /data1 -prune -or -print
```
and now it **[COLOR=Red]just find large file inside /data1[/COLOR]**, which not what I want...

Could I be wrong in interpreting your code below?

> **diesch said:**
> ```
find / -path /media -prune -or -print
```

---

### Post by diesch on 2009-10-23
The order matters here. You first have to exclude to folders you don't want:

```
sudo find / -path /data1 -prune -or -size +300M -print
```

---

### Post by OpenGuard on 2009-10-23
```
find / -prune -o -name /media*

```

Not sure if it works ( not on Linux at the moment ), but give it a try.

---

### Post by televisi on 2009-10-25
> **diesch said:**
> The order matters here. You first have to exclude to folders you don't want:

```
sudo find / -path /data1 -prune -or -size +300M -print
```
Thanks!, the above code works like a charm


> **OpenGuard said:**
> ```
find / -prune -o -name /media*

```Not sure if it works ( not on Linux at the moment ), but give it a try.
Unfortunately, yours giving an error message:
```
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-name `/media'' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ `/media''.

```

---

