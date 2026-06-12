---
title: "Can't Unrar"
date: 2009-12-27
forum: General Help
---

### Post by TheNerdAL on 2009-12-27
Okay, I am trying to Unrar something but I don't know how, I have Ubuntu 9.10! Help! Thanks. :)

---

### Post by dillandriskell on 2009-12-27
Run this in a terminal dude; (to get to terminal: **Applications > Accessories > Terminal**)

```
sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller
```

It's a lot more than unrar, but that'll install everything you'll need to ever unpackage anything, and it doesn't take long either. 

Then just open a terminal and navigate to the right directory.  Here's an example of how to do that if it's on the Desktop:

```
cd /home/<your username>/Desktop
```

Then just type;

```
unrar <name of file>
```

Alternatively, I think you can just right click the file and click "unzip" or "unrar".  Not sure though, I always just use the terminal.

---

### Post by TheNerdAL on 2009-12-27
> **dillandriskell said:**
> Run this in a terminal dude; (to get to terminal: **Applications > Accessories > Terminal**)

```
sudo apt-get install unace rar unrar zip unzip p7zip-full p7zip-rar sharutils aish uudeview mpack lha arj cabextract file-roller
```It's a lot more than unrar, but that'll install everything you'll need to ever unpackage anything, and it doesn't take long either. 

Then just open a terminal and navigate to the right directory.  Here's an example of how to do that if it's on the Desktop:

```
cd /home/<your username>/Desktop
```Then just type;

```
unrar <name of file>
```Alternatively, I think you can just right click the file and click "unzip" or "unrar".  Not sure though, I always just use the terminal.

It says this: "E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

---

### Post by ram4nd on 2009-12-27
just close other terminals or package manager or what ever other utility which scans for packages.

---

### Post by dillandriskell on 2009-12-27
> **ram4nd said:**
> just close other terminals or package manager or what ever other utility which scans for packages.

I second that, a reboot might be in order too.

---

### Post by TheNerdAL on 2009-12-27
> **ram4nd said:**
> just close other terminals or package manager or what ever other utility which scans for packages.
Thanks! :D

---

### Post by TheNerdAL on 2009-12-27
It says:
"UNRAR 3.90 beta 2 freeware      Copyright (c) 1993-2009 Alexander Roshal

Usage:     unrar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  e             Extract files to current directory
  l[t,b]        List archive [technical, bare]
  p             Print file to stdout
  t             Test archive files
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ad            Append archive name to destination path
  ai            Ignore file attributes
  ap<path>      Set path inside archive
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  dh            Open shared files
  ep            Exclude paths from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  id[c,d,p,q]   Disable messages
  ierr          Send all messages to stderr
  inul          Disable all messages
  kb            Keep broken extracted files
  n<file>       Include only specified file
  n@            Read file names to include from stdin
  n@<list>      Include files listed in specified list file
  o[+|-]        Set the overwrite mode
  or            Rename files automatically
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  sl<size>      Process files with size less than specified
  sm<size>      Process files with size more than specified
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             List all volumes
  ver[n]        File version control
  vp            Pause before each volume
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files listed in specified list file
  y             Assume Yes on all queries"

What now?

---

### Post by TheNerdAL on 2009-12-27
lol, I got it, I feel stupid. XD It was right there! :P

---

### Post by dillandriskell on 2009-12-27
> **TheNerdAL said:**
> lol, I got it, I feel stupid. XD It was right there! :P

:lolflag: Just glad you figured it out

---

