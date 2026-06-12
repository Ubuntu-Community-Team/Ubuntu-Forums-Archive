---
title: "[BASH] How to avoid &quot;unexpected&quot; results in a pipe after find"
date: 2009-07-16
forum: General Help
---

### Post by HotForLinux on 2009-07-16
Try:

```
find ./ -maxdepth 1 -iname '.ZZZZZXYZ' -print0 |xargs -0 ls 
```or

```
find ./  -name '.ZZZZZKLM'  |xargs  du -sch 
```or

```
find ./  -name '.ZZZZZKLM'  |xargs  [COLOR=Red]ls -ld [/COLOR]      [COLOR=Red](edit)[/COLOR]
```what do you get?  


Is there a simple way to avoid an empty result in find to be passed as a no-argument to the command on the other side of the pipe?

---

### Post by phillw on 2009-07-16
> **HotForLinux said:**
> Try:

```
find ./ -maxdepth 1 -iname '.ZZZZZXYZ' -print0 |xargs -0 ls 
```or

```
find ./  -name '.ZZZZZKLM'  |xargs  du -sch 
```or

```
find ./  -name '.ZZZZZKLM'  |xargs  ls -al
```what do you get?


Is there a simple way to avoid an empty result in find to be passed as a no-argument to the command on the other side of the pipe?


I'm not too sure what you're after, but grep -v  is the opposite of grep, in that grep passes  matches and EXLUDES everything else, but with the -v  it does the opposite, so | grep -v ""  would stop a null result - I'm not too sure what you mean by 'empty'

eg - your directory file list is

.
..
123
1234
123456
987
9876
98765

find . | grep 123  would ignore . and .. then pass the next 3 filenames, and ignore the last 3
find . | grep -v 123 would pass . and .. ignore the next 3 filenames then pass the last 3 file names.


Hope that helps ?

Phill.

---

### Post by HotForLinux on 2009-07-16
Thanks Phil:

I tried grep -v "" but it doesn't work. Ttry it.

I thought that with those examples was enough and I think you got the idea.

If you execute
find ./  -name '.ZZZ*'  |xargs  ls -l  

and you don't have a file named '.ZZZ*' in you working dir, you don't want to see the list of your directories or the amount of space your dir uses when making those queries. That will be usually NOISE to the result you want to get.

If you want to** get the disk usage of a the hidden files and dirs .[A-Z]*, using du -Sch,  **for example

```
user@host:~$ find ./ -maxdepth 1 -name '.[A-Z]*'
./.ICEauthority
./.Torrent Episode Downloader
./.Xauthority
./.Skype
```[B]
what would you do?[/B]

Look at this:
```
user@host:~$ find ./ -maxdepth 1 -name '.[A-Z]*'|ls -ld
drwxr-xr-x 96 user user 4368 2009-07-16 15:39 .

user@host:~$ find ./ -maxdepth 1 -name '.[A-Z]*'|grep -v "" |ls -ld
drwxr-xr-x 96 user user 4368 2009-07-16 15:39 .
```

---

### Post by sisco311 on 2009-07-16
```
find . -name "foo" -exec ls {} \;
```

---

### Post by HotForLinux on 2009-07-16
> **sisco311 said:**
> ```
find . -name "foo" -exec ls {} \;
```


Still not very intuitive and handy. It will only give me the list (ls) of the files that are dirs.
And if I want **ls -dl**, or **du -Sc**?

---

### Post by sisco311 on 2009-07-16
> **HotForLinux said:**
> Still not very intuitive and handy. It will only give me the list (ls) of the files that are dirs.
And if I want **ls -dl**, or **du -Sc**?

it seems to work for me.

can you post an example?

```
[sisco@acme xtmp]$ ls
1  12  2  3  4
[sisco@acme xtmp]$ ls 12
1
[sisco@acme xtmp]$ find . -name "1" -exec du -sh {} \;
0	./12/1
4.0K	./1
[sisco@acme xtmp]$ find . -name "foo" -exec du -sh {} \;
[sisco@acme xtmp]$ 

```

---

### Post by HotForLinux on 2009-07-16
> **sisco311 said:**
> can you post an example?


If you want to get the total disk usage of the hidden files and dirs called: 

**.[A-Z]*/...whatever_else**.../...

 like you do using ***du -Sch***,  for example, how would you do it?

```
find . -maxdepth 1 -name '.[A-Z]*' -exec du {} \;
```doesn't seems to help because is counting many times the same thing

In my case:
```

**find ./ -maxdepth 1 -name '.[A-Z]*'**
./.ICEauthority
./.Torrent Episode Downloader
./.Xauthority
./.Skype
./.Trash
```A file has spaces, threefore I had to use

```
find ./ -maxdepth 1 -name '.[A-Z]*' -print0 |xargs -0 du -Sch
```which seems to work fine as long as there are files found by ***find***.

But,
```
find ./ -maxdepth 1 -name '.ZZZZZV*' -print0 |xargs -0 du -Sch
```returns the disk usage of the working dir.

[COLOR=Red]**Edit:**[/COLOR]

The truth is that I don't see the great thing in naming **.**something the hidden files, instead of letting them live in a special folder like the Trash folder. The dot often gives some headaches.

---

### Post by HotForLinux on 2009-07-18
```
find ./ -maxdepth 1 -name '.ZZZZZxgfsdV*' -print0 |xargs -0 du -Sch
```

---

