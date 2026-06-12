---
title: "a bash script request"
date: 2010-02-02
forum: General Help
---

### Post by rahilm on 2010-02-02
hello..
I am in need of a script that edits the hyper link to give only the file name..
for example :
if the input is:
[[HTML]http://in.archive.ubuntu.com/ubuntu/pool/universe/g/glew/libglew1.5_1.5.1-4ubuntu1_i386.deb[/HTML]]("http://in.archive.ubuntu.com/ubuntu/pool/universe/g/glew/libglew1.5_1.5.1-4ubuntu1_i386.deb")the output should be:
```
libglew1.5_1.5.1-4ubuntu1_i386.deb
```any attempt to help are appreciated

---

### Post by bluefrog on 2010-02-02
to test:
sed 's-^.*/--' file

If happy then edit in place or redirect to another file:
sed -i 's-^.*/--' file
sed 's-^.*/--' file > processed-file

---

### Post by DaithiF on 2010-02-02
or to do the same within bash:
```
url=http://in.archive.ubuntu.com/ubuntu/pool/universe/g/glew/libglew1.5_1.5.1-4ubuntu1_i386.deb
echo ${url##*/}
```

---

### Post by undecim on 2010-02-02
how about the basename command?```
undecim@caffeine:~$ basename http://in.archive.ubuntu.com/ubuntu/pool/universe/g/glew/libglew1.5_1.5.1-4ubuntu1_i386.deb
libglew1.5_1.5.1-4ubuntu1_i386.deb
```

---

### Post by DaithiF on 2010-02-02
and just for completeness, to get the path up to the filename, 
```
$ echo ${url%/*}
http://in.archive.ubuntu.com/ubuntu/pool/universe/g/glew
```

---

### Post by arpan251089 on 2010-02-02
yeah basename is best suitable

---

### Post by rahilm on 2010-02-02
thnx guys....works like charm..liked the basename one and the {url##*/}

out of curiosity, what does url##*/ mean actually??

---

### Post by DaithiF on 2010-02-02
take a look at table B-5 here: [http://tldp.org/LDP/abs/html/refcards.html](http://tldp.org/LDP/abs/html/refcards.html)

---

### Post by jamesisin on 2010-02-02
Great thread.

Please mark it as SOLVED in Thread Tools above.

---

### Post by rahilm on 2010-02-03
okay...i declare this thread as SOLVED...

---

### Post by rahilm on 2010-05-08
umm. i reopen this thread with another question.
i have got a file with a list of urls. each on a different line.
so, it is possible to make a script that will make a file which has a list of all the basenames..

---

### Post by DaithiF on 2010-05-08
Hi, something like:
```
while read line
do
echo ${line##*/} 
done < sourcefile > destinationfile
```

---

