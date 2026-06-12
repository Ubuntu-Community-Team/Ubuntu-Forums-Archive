---
title: "Help defragment drive."
date: 2009-09-22
forum: General Help
---

### Post by Ubu4moi on 2009-09-22
The last disk check said I had a lot of non-contiguous files. I'm running Ubuntu Ultimate Edition 64bit. How can I difragment the drive?

---

### Post by scragar on 2009-09-23
There are a few defragmenting tools for linux, but for the most part they aren't needed, ext file systems don't get fractured files unless your hard drive is continually running with very little free space.

pyfragtools is one such tool, google if for more information if you really do want to try and defragment ubuntu.
[http://ubuntuforums.org/showthread.php?t=169551](http://ubuntuforums.org/showthread.php?t=169551)

---

### Post by dankdave on 2009-09-23
According to these threads:

[http://ubuntuforums.org/showthread.php?t=407889](http://ubuntuforums.org/showthread.php?t=407889)

[http://ubuntuforums.org/showthread.php?t=228199](http://ubuntuforums.org/showthread.php?t=228199)

they claim you don't ever need to defrag your hard drive unless you went above 90% usage, and then if you clean up some space it'll fix itself.

---

### Post by scragar on 2009-09-23
> **dankdave said:**
> 
they claim you don't ever need to defrag your hard drive unless you went above 90% usage, and then if you clean up some space it'll fix itself.  If you insist on running a defragmenter, then you can try a package called defrag:

[http://packages.ubuntu.com/dapper/defrag](http://packages.ubuntu.com/dapper/defrag)

The link you posted points to a dapper drake install, could you pick a link for a currently supported install?

---

### Post by ibuclaw on 2009-09-23
> **Ubu4moi said:**
> The last disk check said I had a lot of non-contiguous files. I'm running Ubuntu Ultimate Edition 64bit. How can I difragment the drive?

Usually just letting the routine disk checks at boot complete is enough, as part of the fsck routine is to optimise directory structures.

Regards
Iain

---

### Post by Ubu4moi on 2009-09-23
Thanks.
 Are you really Valentinez Alkalinella Xifax Sicidabohertz Gumbigobilla Blue Stradivari Talentrent Pierre AndrT Charton-Haymoss Ivanovicci Baldeus George Doitzel Kaiser the third? I think I know your sister Mimi.

---

### Post by scragar on 2009-09-23
> **Ubu4moi said:**
> Thanks.
 Are you really Valentinez Alkalinella Xifax Sicidabohertz Gumbigobilla Blue Stradivari Talentrent Pierre AndrT Charton-Haymoss Ivanovicci Baldeus George Doitzel Kaiser the third? I think I know your sister Mimi.

I changed that to my sig after watching Trigun, the way Vash rhymes that off as if it's nothing, I just had to make it my sig :p

I'm intending to change my sig again at some point, I'm currently watching FMA Brotherhood, there's no really special quotes I can think of though.

---

### Post by CatKiller on 2009-09-23
> **Ubu4moi said:**
> How can I difragment the drive?

If it really bothers you, you can move files to another partition and move them back. The file will then be contiguous. **tar** is a useful tool for this.

---

