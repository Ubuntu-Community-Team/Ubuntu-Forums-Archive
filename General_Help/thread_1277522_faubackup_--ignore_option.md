---
title: "faubackup --ignore option"
date: 2009-09-28
forum: General Help
---

### Post by tgeer43 on 2009-09-28
I'm hoping that someone here has experience with the faubackup package. I want to start using it instead of 'tar' to manage my backups. It's a simple enough command but I can't find any examples of how to use the --ignore option to exclude certain directories. I have tried things like:
```
--ignore-/home/tgeer/Music
and
--ignore=/home/tgeer/Music/
and
--ignore=/home/tgeer/Music/*
```and none of them are working correctly.

So does anyone know the correct syntax for the --ignore option?

Thanks in advance,

tgeer

---

### Post by tgeer43 on 2009-09-28
Well, I got it partly figured out by trial and error.
The correct syntax is:
```
--ignore="**/Music"
```The double-quotes are only needed if the file name or directory name contains spaces.

What I haven't figured out yet is how to specify more than one pattern to ignore. The man page says:
> --ignore=pattern
   Add  patterns  for  files that should not be backed up.  Those will be directly passed to faubackup-find. Notice that it says "adds pattern**_s_**" which seems to indicate that multiple patterns can be specified. I've tried using spaces and commas to separate the patterns like this:
```
--ignore="**/Music","**/Videos"
and
--ignore="**/Music" "**/Videos"
```but those don't work. I even tried using '--ignore=' multiple times on the command line but no joy.

I don't know what else to try.

tgeer

---

### Post by tgeer43 on 2009-09-28
I never did figure out how to specify multiple patters to ignore from the command line but I was able to accomplish the same thing by specifying them in /etc/faubackup.conf.

I'd still like the flexibility to specify everything on the command line rather than having to edit faubackup.conf every time I want to change my backup parameters.

I'll leave this thread open for a couple of days to see if anyone can answer my original question.

tgeer

---

### Post by falconindy on 2009-09-28
If its anything like rsync, you can just keep specifying more --ignore=PATTERN options.

---

### Post by tgeer43 on 2009-09-29
> **falconindy said:**
> If its anything like rsync, you can just keep specifying more --ignore=PATTERN options.
Yeah, in my post #2 I mentioned that I had tried using ignore=PATTERN more than once in the command but no joy. :(
Maybe I had something else wrong with the syntax at that point so I'll give it another shot but I'm not holding my breath.
The config file uses slightly different syntax than the command line but works just fine for me in specifying multiple ignore patterns.

tgeer

---

