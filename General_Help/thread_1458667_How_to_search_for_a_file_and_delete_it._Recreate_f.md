---
title: "How to search for a file and delete it. Recreate file with same name"
date: 2010-04-20
forum: General Help
---

### Post by srikanth007m on 2010-04-20
Hi all, 
 I have a problem while executing below command. 
 
 find Desktop/Test -name test -exec rm -rf {} \; -exec touch {}/test  \; 

 
From the above command first command is executing  successfully. But 
 when comes to touch command it was not creating  file under specified directory. Is there any thing wrong with touch syntax or expressions used?   Can any one please 
 help me. 

Actually my requirement is to find a file in a  specific 
 directory and remove it and want to create a file with the  same name

---

### Post by xhalarin on 2010-04-20
I would use a bash script loop vs using the find exec parameter.  I have found exec to be quirky.

Here is an example:
```
#! /bin/bash

find Desktop/Test -name test -type f -print | while read FILEPATH;
do
	FILENAME=${FILEPATH##*/}
	rm -rf $FILENAME
	touch $FILENAME	
done

```

It's easier to debug and understand what's going on this way.  Note that I have not tested this script and you will want to modify it to meet your needs.  (careful, it's doing a 'rm' and could delete files)

---

### Post by Paddy Landau on 2010-04-20
> **srikanth007m said:**
> find Desktop/Test -name test -exec rm -rf {} \; -exec touch {}/test  \;
I'm not sure whether [FONT=Courier New][SIZE=3]find[/SIZE][/FONT] can take two [FONT=Courier New][SIZE=3]-exec[/SIZE][/FONT] commands. But surely the [FONT=Courier New][SIZE=3]{}[/SIZE][/FONT] refers to the file name, so you've put it twice? I would try:
```
find Desktop/Test -name test -exec rm -rf {} \; -exec touch {} \;
```> **xhalarin said:**
>  ```
find Desktop/Test -name test -type d -print | while read FILEPATH;
```
I think the type should be f.
[FONT=Courier New][SIZE=3]-type f[/SIZE][/FONT]

---

### Post by gmargo on 2010-04-20
There is no reason that you can't do it all at once.  Find will take multiple -exec options, and I've never found it "quirky".  Your first attempt is only missing a mkdir (and a -type d to be safe).

```

$ pwd
/tmp/find_test
$ ls -l
total 0
$ mkdir test
$ touch test/foo
$ ls -l 
total 4
drwxr-xr-x 2 gmargo gmargo 4096 Apr 20 08:03 test
$ ls -l test
total 0
-rw-r--r-- 1 gmargo gmargo 0 Apr 20 08:03 foo
$ 
$ find . -type d -name test -exec rm -rf {} \; -exec mkdir {} \; -exec touch {}/bar \; 
$ 
$ ls -l
total 4
drwxr-xr-x 2 gmargo gmargo 4096 Apr 20 08:04 test
$ ls -l test
total 0
-rw-r--r-- 1 gmargo gmargo 0 Apr 20 08:04 bar


```**Update:**
> Actually my requirement is to find a file in a  specific 
 directory and remove it and want to create a file with the  same nameDarn I should have read it again before posting.

To find a file (named Desktop/Test/test), remove, create, this should do:
```

find Desktop/Test -type f -name test -exec rm -f {} \; -exec touch {} \; 

```

---

### Post by srikanth007m on 2010-04-21
Yes, that worked for me.  I am giving file name as twice like -exec  touch {}/test. Now I got it. Thanks to all

---

