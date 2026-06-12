---
title: "Creating multiple directories using MKDIR"
date: 2011-09-01
forum: General Help
---

### Post by aviceda on 2011-09-01
Hi, I know this subject has been answered elsewhere on the web, but I just can't relocate it now.
Basically I want to create multiple sub-directories under a directory using a text-file list, I remember the command-line went something like MKDIR {foo1,foo2,foo3} but I can't seem to get it to work now.
Can anyone help please? All help gratefully received.

---

### Post by nothingspecial on 2011-09-01
```
mkdir {blah1,blah2,blah3}
```

if you want directories called fish and cheese in blah1 blah2 and blah3
```

mkdir -p {blah1,blah2,blah3}/{fish,cheese}
```

---

### Post by aviceda on 2011-09-01
Almost, but all I'm trying to achieve is the blah directories, 

This is what I tried, and got a weird result, why do the brackets appear in the first and last directory names?


aviceda@aviceda-desktop:~/images/birds/Phaethontidae$ mkdir -p {"Red-billed Tropicbird", "Red-tailed Tropicbird", "White-tailed Tropicbird"}
aviceda@aviceda-desktop:~/images/birds/Phaethontidae$ ls -la
total 616
drwxr-xr-x   5 aviceda aviceda  4096 2011-09-01 19:53 .
drwxr-xr-x 230 aviceda aviceda 12288 2011-09-01 16:15 ..
drwxr-xr-x   2 aviceda aviceda  4096 2011-09-01 19:53 {Red-billed Tropicbird,
drwxr-xr-x   2 aviceda aviceda  4096 2011-09-01 19:53 Red-tailed Tropicbird,
-rw-r--r--   1 aviceda aviceda 94922 2011-07-29 19:01 rttb_0194a.jpg
-rw-r--r--   1 aviceda aviceda 78920 2011-07-29 19:01 rttb_0194b.jpg
-rwxr-xr-x   1 aviceda aviceda 93305 2003-12-14 18:48 rttb0301.jpg
-rwxr-xr-x   1 aviceda aviceda 90473 2003-12-14 18:51 rttb0302.jpg
-rwxr-xr-x   1 aviceda aviceda 76518 2003-12-14 18:53 rttb0303.jpg
-rwxr-xr-x   1 aviceda aviceda 60889 2003-12-14 18:55 rttb0304.jpg
-rwxr-xr-x   1 aviceda aviceda 81493 2003-12-14 18:57 rttb0305.jpg
-rwxr-xr-x   1 aviceda aviceda 10053 2003-12-15 00:23 rttbsmall.jpg
drwxr-xr-x   2 aviceda aviceda  4096 2011-09-01 19:53 White-tailed Tropicbird}

Looks like we are getting there though, some of the directories I have already created will need 50-100 sub-directories to accommodate all the species.

---

### Post by nothingspecial on 2011-09-01
Get rid of the spaces

```
mkdir {"Red-billed Tropicbird","Red-tailed Tropicbird","White-tailed Tropicbird"}
```

Also you don't need the -p if you are only creating one level.

---

### Post by nothingspecial on 2011-09-01
To be honest you don't need the brackets at all. Just ```
mkdir "Red-billed Tropicbird" "Red-tailed Tropicbird" "White-tailed Tropicbird"
```

The brackets would only be useful in a case like
 ```
mkdir {Red,White,Blue,Yellow}-tailed_Tropicbird
``` so you only have to type the bit outside the brackets once.

---

### Post by aviceda on 2011-09-01
Nice! Thanks for your help ;)

---

### Post by nothingspecial on 2011-09-01
One thing comes to mind. If you use the brackets method (brace expansion) like in my last example don't use double quotes.If you do you will get two directories like this.

```
$ mkdir "{Red,White,Blue,Yellow}-tailed Tropicbird"
$ ls
{Red,White,Blue,Yellow}-tailed Tropicbird
```

If you don't you will get this

```
$ mkdir {Red,White,Blue,Yellow}-tailed Tropicbird
$ ls
Blue-tailed  Red-tailed  Tropicbird  White-tailed  Yellow-tailed
```

If you require spaces then you will have to escape them with a \ like this
```

$ mkdir {Red,White,Blue,Yellow}-tailed\ Tropicbird
$ ls
Blue-tailed Tropicbird  Red-tailed Tropicbird  White-tailed Tropicbird  Yellow-tailed Tropicbird
```

---

