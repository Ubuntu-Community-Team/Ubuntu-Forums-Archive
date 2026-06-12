---
title: "patch command"
date: 2010-11-17
forum: General Help
---

### Post by c2tarun on 2010-11-17
can anyone please explain me what patch do???
i read many documents but not able to understand what it is.
i tried to patch a difference file by
 
```

patch -p0 < file.diff

```but got the following output

patch: **** Only garbage was found in the patch input.


anyone please help me.

thanx

---

### Post by Mark Phelps on 2010-11-17
Sigh ... Google is your friend:  

[http://linux.about.com/od/commands/l/blcmdl1_patch.htm]("http://linux.about.com/od/commands/l/blcmdl1_patch.htm")

---

### Post by c2tarun on 2010-11-17
> **Mark Phelps said:**
> Sigh ... Google is your friend:  

[http://linux.about.com/od/commands/l/blcmdl1_patch.htm](http://linux.about.com/od/commands/l/blcmdl1_patch.htm)

thanx a lot friend but sorry to my understanding capability i m still not getting. let me give u all few details.

mine first file is
file.old
```

aaa
bbb
ddd
eee
ggg
hhh
iii
kkk
nnn

```

new file
file.new
```
bbb
ccc
ddd
eee
fff
ggg
hhh
jjj
kkk
lll

```

file.diff
```
1d0
< aaa
2a2
> ccc
4a5
> fff
7c8
< iii
---
> jjj
9c10
< nnn
---
> lll

```


but still i m getting the following error.
patch: **** Only garbage was found in the patch input.

---

