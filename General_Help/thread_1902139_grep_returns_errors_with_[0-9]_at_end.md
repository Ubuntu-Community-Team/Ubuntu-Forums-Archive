---
title: "grep returns errors with [0-9] at end"
date: 2011-12-30
forum: General Help
---

### Post by chipbuster on 2011-12-30
I'm sorry if this is a repeated question, but I tried to search this on the forums and was inundated with unrelated posts.

I was messing around in the terminal and decided to try to find all my hard drive devices. So I changed to /dev and entered "ls -a | grep [hs]d[a-z][0-9]"

Lo and behold, I get this: 
> 
grep: sda2: Permission denied
grep: sda3: Permission denied
grep: sda5: Permission denied
grep: sda6: Permission denied
grep: sda7: Permission denied
using sudo on ls and grep did nothing to change that. I also tried putting an ampersand after the pipe--no dice. What did work was eliminating any sort of bracket at the end of the command--if I put in "grep [hs]d[a-z]." with a period at the end instead of "[0-9]", grep returns everything perfectly. I couldn't find a good explanation for this anywhere on the internet or in the man pages. Anybody know why it's acting this way?

EDIT: To be clear, when the errors occur, there is no STDOUT being displayed. Piping 2> /dev/null returns nothing

---

### Post by yetiman64 on 2011-12-30
I tried this here from the home folder (not cd-ing into /dev), it found ALL my drives, only needed sudo on grep, listing /dev without raising privileges seems to work fine.

```
$ ls -a /dev | sudo grep [hs]d[a-z][0-9]
[sudo] password for *<my-local-username>*: 
sda1
sda10
sda11
sda12
sda13
sda14
sda2
sda3
sda5
sda6
sda7
sda8
sda9
sdb1
sdb2
sdb3
sdb4
sdc1
sdd1
```

---

### Post by chipbuster on 2011-12-30
interesting, that command seems to freeze my terminal emulator....after a minute or so it spits > Binary file sda2 matches and just sits there after that. I have to enter ^C to get it to do anything after that.

---

### Post by yetiman64 on 2011-12-30
> **chipbuster said:**
> interesting, that command seems to freeze my terminal emulator....after a minute or so it spits  and just sits there after that. I have to enter ^C to get it to do anything after that.
Yes I got that exact result during testing a few different code combinations here at one stage. 

Are you copying and pasting the code I used above or did you type it in ? (only a very small change to my original command was needed to get the above command working).

Edit: I will also note again, I am working directly from my user home folder and NOT cd-ing into /dev if that makes any difference.

---

### Post by chipbuster on 2011-12-30
I'm copypasta-ing verbatim. I tried to execute that from home too. I actually suspect that it may have just crashed my system (I left it running in the background and suddenly my computer froze as if it had suddenly started using large amounts of swap).

---

### Post by yetiman64 on 2011-12-30
Ok, in that case it would be best to wait for others here to check this as well, as I said earlier, in testing I got a very similar effect to what you described (not a full system lockup though). But changing my code only slightly got it working with no more terminal hangs.

Can anyone else add more info/explanations to this question? Cheers.

---

### Post by Stanley_00 on 2011-12-30
It work fine for me, just quote the text after grep, like this
> ls -a | grep "[hs]d[a-z][0-9]"

---

### Post by Vaphell on 2011-12-30
why bother with grep when ls can do the same?
```

$ cd /dev; ls -a [hs]d[a-z][0-9]
sda1  sda2  sda5  sda6  sdb1  sdb2  sdb5  sdb6  sdb7  sdb8  sdc1  sdc2

```
another way using echo
```
$ cd /dev; echo [hs]d[a-z][0-9]
sda1 sda2 sda5 sda6 sdb1 sdb2 sdb5 sdb6 sdb7 sdb8 sdc1 sdc2
```

---

### Post by yetiman64 on 2011-12-30
> **Vaphell said:**
> why bother with grep when ls can do the same?
```

$ cd /dev; ls -a [hs]d[a-z][0-9]
sda1  sda2  sda5  sda6  sdb1  sdb2  sdb5  sdb6  sdb7  sdb8  sdc1  sdc2

```another way using echo
```
$ cd /dev; echo [hs]d[a-z][0-9]
sda1 sda2 sda5 sda6 sdb1 sdb2 sdb5 sdb6 sdb7 sdb8 sdc1 sdc2
```
Just make sure you don't have more than 10 partitions per disk if you use the ls method, it lost my partitions sda10 to sda14 here :lol:.

```
:/dev$ ls -a [hs]d[a-z][0-9]
sda1  sda3  sda6  sda8  sdb1  sdb3  sdc1
sda2  sda5  sda7  sda9  sdb2  sdb4  sdd1
```Same result with echo. At least grep picks up on the 1st "1" in sda10 through to sda14 on my install.
```
:/dev$ echo [hs]d[a-z][0-9]
sda1 sda2 sda3 sda5 sda6 sda7 sda8 sda9 sdb1 sdb2 sdb3 sdb4 sdc1 sdd1
```Note sda4 does not exist on my install, so no command will find it. :)

Edit: @ OP, the code in post 7 worked well here without using sudo at all, from the home folder and specifying /dev or from the /dev folder directly. 
Also not many people may have as many installs / partitions on the same drive as I have, but it is still good to know what will work in the largest set of circumstances.

---

### Post by Vaphell on 2011-12-30
> Just make sure you don't have more than 10 partitions per disk if you use the ls method, it lost my partitions sda10 to sda14 here

true, so you need to add */? to the end to include sda[0-9]<whatever> because shell globbing works differently that grep regexes
or you can go with
```
ls -a [hs]d[a-z][0-9]{[0-9],}
```
or with ```
find -maxdepth 1 -name '[hs]d[a-z][0-9]'
```

either way ls-and-grep is not a good approach and people doing that love doing other bad things like
```
for f in $( ls | grep ... ); ...; done 
```
Builtin patterns should be used as often as possible because they are foolproof and avoid the problem of whitespaces (which appears when parsing file lists by hand) completely.

---

### Post by chipbuster on 2011-12-30
Thanks for the advice all! Just out of curiosity, is ls | grep bad because it just runs into a lot of errors, or is there something else that could happen?

---

### Post by sisco311 on 2011-12-30
ls shows you a representation of files. They are NOT file names (for simple names, they mostly happen to be equivalent). See: [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

