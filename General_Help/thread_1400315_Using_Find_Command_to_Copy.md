---
title: "Using Find Command to Copy"
date: 2010-02-06
forum: General Help
---

### Post by reavesr on 2010-02-06
Hello all, I'm fairly new to linux command line usage and I'm just starting to find how useful it can be.  Any way I'm trying to use the find command to copy all my mp3s on my hard drive to one folder.  I believe this should work but I don't want to miss any files:

find / -name "*.mp3" -exec cp {} /home/reavesr/mp3 \;

One thing I'm not fully understanding is the use of the {} and the \; at the end, if someone could elaborate that would be great.

---

### Post by jken146 on 2010-02-07
[QUOTE="man find"]```
-exec command ;
              Execute  command;  true  if 0 status is returned.  All following
              arguments to find are taken to be arguments to the command until
              an  argument  consisting of `;' is encountered.  The string `{}'
              is replaced by the current file name being processed  everywhere
              it occurs in the arguments to the command, not just in arguments
              where it is alone, as in some versions of find.  Both  of  these
              constructions might need to be escaped (with a `\') or quoted to
              protect them from expansion by the shell.  See the EXAMPLES sec&#8208;
              tion for examples of the use of the -exec option.  The specified
              command is run once for each matched file.  The command is  exe&#8208;
              cuted  in  the starting directory.   There are unavoidable secu&#8208;
              rity problems surrounding use of the -exec  action;  you  should
              use the -execdir option instead.

```[/QUOTE]

Hope that helps!

---

### Post by gmargo on 2010-02-07
> **reavesr said:**
> Hello all, I'm fairly new to linux command line usage and I'm just starting to find how useful it can be.  Any way I'm trying to use the find command to copy all my mp3s on my hard drive to one folder.  I believe this should work but I don't want to miss any files:

find / -name "*.mp3" -exec cp {} /home/reavesr/mp3 \;

One thing I'm not fully understanding is the use of the {} and the \; at the end, if someone could elaborate that would be great.

Please don't take offense at any of this, but my comments are:
If you are going to search from the root directory, you really should use the -xdev option, so as to not search through system directories like /sys and /proc.  Just run a different find for each filesystem you want to search.  You're also going to have a recursion problem when your find reaches the /home/reavesr/mp3 directory!  And when you specify the name it should be in single quotes.  It only worked for you because there are no .mp3 files in the root directory.  And lastly, a separate exec for each file is quite slow.

So, now that I shot my mouth off, how would I do it?  Something like this, which gives you more man pages to read.  Run one for each filesystem to search.
```

find / -xdev -type f -iname '*.mp3' -print | \
grep -v ^/home/reavesr/mp3/ | \
xargs -d '\n' cp -p -t /home/reavsr/mp3/

```

---

### Post by Brandon_oma#692 on 2010-02-07
how would i change this to look in my artition that windows is on?

---

### Post by gmargo on 2010-02-07
> **Brandon_oma#692 said:**
> how would i change this to look in my artition that windows is on?

Tell the find command where to look.  I don't know what the default windows mount point is, but if your windows partition is mounted on **/media/windows**, then use:
```

find **/media/windows** -xdev ....

```

---

### Post by reavesr on 2010-02-07
> **gmargo said:**
> Please don't take offense at any of this, but my comments are:
If you are going to search from the root directory, you really should use the -xdev option, so as to not search through system directories like /sys and /proc.  Just run a different find for each filesystem you want to search.  You're also going to have a recursion problem when your find reaches the /home/reavesr/mp3 directory!  And when you specify the name it should be in single quotes.  It only worked for you because there are no .mp3 files in the root directory.  And lastly, a separate exec for each file is quite slow.

So, now that I shot my mouth off, how would I do it?  Something like this, which gives you more man pages to read.  Run one for each filesystem to search.
```

find / -xdev -type f -iname '*.mp3' -print | \
grep -v ^/home/reavesr/mp3/ | \
xargs -d '\n' cp -p -t /home/reavsr/mp3/

```

Hah no offense taken at all I'm looking for information and yours is very helpful.  Really appreciate the input.  Thanks jken as well, *slaps self in head* why didn't I read the man page better.

---

