---
title: "rar archive recovery"
date: 2012-03-09
forum: General Help
---

### Post by abdolah on 2012-03-09
hello
i have a rar file of size 800MB and i cannot open it : 
??? - the file header is corrupt
how i can recover 800 MB of it (it contains more than 100 files so if i can recover some of them it will be worth)

---

### Post by CaseyC on 2012-03-09
Have you tried other compression tools to try and open the file? I know it probably sounds crazy :P 

Here is some more info: 
[http://ubuntuforums.org/showthread.php?t=1453595](http://ubuntuforums.org/showthread.php?t=1453595)

---

### Post by Jon Monreal on 2012-03-09
I've experienced corrupted rar files, and you might try this:

sudo apt-get install rar
rar [corruptfilename.rar] -F fix.rar

Replacing the first part with the path of the corrupt file. This would spit out fix.rar in your home folder.

---

### Post by abdolah on 2012-03-09
abdolah@abdolah-laptop:~$ rar 3.rar -F fix.rar

RAR 3.90 beta 2   Copyright (c) 1993-2009 Alexander Roshal   3 Jun 2009
Shareware version         Type RAR -? for help

Cannot open fix.rar
No such file or directory
Usage:     rar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  a             Add files to archive
  c             Add archive comment
  cf            Add files comment
  ch            Change archive parameters
  cw            Write archive comment to file
  d             Delete files from archive
  e             Extract files to current directory
  f             Freshen files in archive
  i[par]=<str>  Find string in archives
  k             Lock archive
  l[t,b]        List archive [technical, bare]
  m[f]          Move to archive [files only]
  p             Print file to stdout
  r             Repair archive
  rc            Reconstruct missing volumes
  rn            Rename archived files
  rr[N]         Add data recovery record
  rv[N]         Create recovery volumes
  s[name|-]     Convert archive to or from SFX
  t             Test archive files
  u             Update files in archive
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ad            Append archive name to destination path
  ag[format]    Generate archive name using the current date
  ai            Ignore file attributes
  ap<path>      Set path inside archive
  as            Synchronize archive contents
  av            Put authenticity verification (registered versions only)
  av-           Disable authenticity verification check
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  df            Delete files after archiving
  dh            Open shared files
  ds            Disable name sort for solid archive
  dw            Wipe files after archiving
  e[+]<attr>    Set file exclude and include attributes
  ed            Do not add empty directories
  en            Do not put 'end of archive' block
  ep            Exclude paths from names
  ep1           Exclude base directory from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  hp[password]  Encrypt both file data and headers
  id[c,d,p,q]   Disable messages
  ierr          Send all messages to stderr
  ilog[name]    Log errors to file (registered versions only)
  inul          Disable all messages
  isnd          Enable sound
  k             Lock archive
  kb            Keep broken extracted files
  m<0..5>       Set compression level (0-store...3-default...5-maximal)
  mc<par>       Set advanced compression parameters
  md<size>      Dictionary size in KB (64,128,256,512,1024,2048,4096 or A-G)
  ms[ext;ext]   Specify file types to store
  n<file>       Include only specified file
  n@            Read file names to include from stdin
  n@<list>      Include files listed in specified list file
  o[+|-]        Set the overwrite mode
  ol            Save symbolic links as the link instead of the file
  or            Rename files automatically
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  r-            Disable recursion
  r0            Recurse subdirectories for wildcard names only
  rr[N]         Add data recovery record
  rv[N]         Create recovery volumes
  s[<N>,v[-],e] Create solid archive
  s-            Disable solid archiving
  sc<chr>[obj]  Specify the character set
  sfx[name]     Create SFX archive
  si[name]      Read data from standard input (stdin)
  sl<size>      Process files with size less than specified
  sm<size>      Process files with size more than specified
  t             Test files after archiving
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tk            Keep original archive time
  tl            Set archive time to latest file
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             Create volumes with size autodetection or list all volumes
  v<size>[k,b]  Create volumes with size=<size>*1000 [*1024, *1]
  ver[n]        File version control
  vn            Use the old style volume naming scheme
  vp            Pause before each volume
  w<path>       Assign work directory
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files listed in specified list file
  y             Assume Yes on all queries
  z[file]       Read archive comment from file
abdolah@abdolah-laptop:~$

---

### Post by Jon Monreal on 2012-03-09
Actually try:

rar 3.rar -r fix.rar

It might be a good idea to back up the original somewhere, just in case.

---

### Post by abdolah on 2012-03-09
abdolah@abdolah-laptop:~$ cd w_qe/
abdolah@abdolah-laptop:~/w_qe$ rar 3.rar -r fix.rar

RAR 3.90 beta 2   Copyright (c) 1993-2009 Alexander Roshal   3 Jun 2009
Shareware version         Type RAR -? for help

Usage:     rar <command> -<switch 1> -<switch N> <archive> <files...>
               <@listfiles...> <path_to_extract\>

<Commands>
  a             Add files to archive
  c             Add archive comment
  cf            Add files comment
  ch            Change archive parameters
  cw            Write archive comment to file
  d             Delete files from archive
  e             Extract files to current directory
  f             Freshen files in archive
  i[par]=<str>  Find string in archives
  k             Lock archive
  l[t,b]        List archive [technical, bare]
  m[f]          Move to archive [files only]
  p             Print file to stdout
  r             Repair archive
  rc            Reconstruct missing volumes
  rn            Rename archived files
  rr[N]         Add data recovery record
  rv[N]         Create recovery volumes
  s[name|-]     Convert archive to or from SFX
  t             Test archive files
  u             Update files in archive
  v[t,b]        Verbosely list archive [technical,bare]
  x             Extract files with full path

<Switches>
  -             Stop switches scanning
  ad            Append archive name to destination path
  ag[format]    Generate archive name using the current date
  ai            Ignore file attributes
  ap<path>      Set path inside archive
  as            Synchronize archive contents
  av            Put authenticity verification (registered versions only)
  av-           Disable authenticity verification check
  c-            Disable comments show
  cfg-          Disable read configuration
  cl            Convert names to lower case
  cu            Convert names to upper case
  df            Delete files after archiving
  dh            Open shared files
  ds            Disable name sort for solid archive
  dw            Wipe files after archiving
  e[+]<attr>    Set file exclude and include attributes
  ed            Do not add empty directories
  en            Do not put 'end of archive' block
  ep            Exclude paths from names
  ep1           Exclude base directory from names
  ep3           Expand paths to full including the drive letter
  f             Freshen files
  hp[password]  Encrypt both file data and headers
  id[c,d,p,q]   Disable messages
  ierr          Send all messages to stderr
  ilog[name]    Log errors to file (registered versions only)
  inul          Disable all messages
  isnd          Enable sound
  k             Lock archive
  kb            Keep broken extracted files
  m<0..5>       Set compression level (0-store...3-default...5-maximal)
  mc<par>       Set advanced compression parameters
  md<size>      Dictionary size in KB (64,128,256,512,1024,2048,4096 or A-G)
  ms[ext;ext]   Specify file types to store
  n<file>       Include only specified file
  n@            Read file names to include from stdin
  n@<list>      Include files listed in specified list file
  o[+|-]        Set the overwrite mode
  ol            Save symbolic links as the link instead of the file
  or            Rename files automatically
  ow            Save or restore file owner and group
  p[password]   Set password
  p-            Do not query password
  r             Recurse subdirectories
  r-            Disable recursion
  r0            Recurse subdirectories for wildcard names only
  rr[N]         Add data recovery record
  rv[N]         Create recovery volumes
  s[<N>,v[-],e] Create solid archive
  s-            Disable solid archiving
  sc<chr>[obj]  Specify the character set
  sfx[name]     Create SFX archive
  si[name]      Read data from standard input (stdin)
  sl<size>      Process files with size less than specified
  sm<size>      Process files with size more than specified
  t             Test files after archiving
  ta<date>      Process files modified after <date> in YYYYMMDDHHMMSS format
  tb<date>      Process files modified before <date> in YYYYMMDDHHMMSS format
  tk            Keep original archive time
  tl            Set archive time to latest file
  tn<time>      Process files newer than <time>
  to<time>      Process files older than <time>
  ts<m,c,a>[N]  Save or restore file time (modification, creation, access)
  u             Update files
  v             Create volumes with size autodetection or list all volumes
  v<size>[k,b]  Create volumes with size=<size>*1000 [*1024, *1]
  ver[n]        File version control
  vn            Use the old style volume naming scheme
  vp            Pause before each volume
  w<path>       Assign work directory
  x<file>       Exclude specified file
  x@            Read file names to exclude from stdin
  x@<list>      Exclude files listed in specified list file
  y             Assume Yes on all queries
  z[file]       Read archive comment from file
abdolah@abdolah-laptop:~/w_qe$

---

### Post by Jon Monreal on 2012-03-09
Ugh, I'm guessing it just wants

rar -r 3.rar

---

### Post by abdolah on 2012-03-09
same as previous .

---

### Post by Jon Monreal on 2012-03-09
How about:

rar -F 3.rar fix.rar

---

### Post by abdolah on 2012-03-09
same.

---

### Post by Jon Monreal on 2012-03-09
Okay, sorry I just saw it's a command, not a switch.

rar r 3.rar fix.rar

should work.

---

### Post by abdolah on 2012-03-09
yes thanks it is now working , and created a file:
rebuilt.3.rar 
which contains some of my data.
thank you very much.

---

### Post by Jon Monreal on 2012-03-09
Sure, it's no problem.

If you get a chance, can you mark the thread as solved under "Thread Tools" at the top of the page?

Thanks.

---

