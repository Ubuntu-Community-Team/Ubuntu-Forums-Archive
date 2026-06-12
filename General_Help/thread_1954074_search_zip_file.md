---
title: "search zip file"
date: 2012-04-07
forum: General Help
---

### Post by winzip on 2012-04-07
Hi,

I have a zip file....myapps.zip

It has a file which has  text "/home/user/appkey".

I  want to find that file name and its location.

Whats the command to shoot ? 



Here I post a sample  input / output to explain my requirement.
_Input:_  myapps.zip  and  "/home/user/appkey"
_Expected Output:_  match  found.  file "/home/khg/ijk"  has text "/home/user/appkey".

---

### Post by raja.genupula on 2012-04-07
[http://ubuntuforums.org/archive/index.php/t-946280.html](http://ubuntuforums.org/archive/index.php/t-946280.html)

---

### Post by winzip on 2012-04-07
> **raja.genupula said:**
> [http://ubuntuforums.org/archive/index.php/t-946280.html](http://ubuntuforums.org/archive/index.php/t-946280.html)

I have visited that link . still not clear. I'm looking for text match  here.

Could you please tell whats the command to check in my case ?

---

### Post by Vaphell on 2012-04-07
```
zipgrep '/home/user/appkey' myapps.zip
```

---

### Post by codemaniac on 2012-04-07
zgrep would aslo do that .

```
zgrep '/home/user/appkey' myapps.zip
```

---

### Post by Vaphell on 2012-04-07
in my case (10.04) zgrep shows that the phrase is somewhere inside the archive, but doesn't show where
```
$ zgrep test zip.zip 
test
$ zipgrep test zip.zip 
1.txt:test
2.txt:test
xxx/1.txt:test
xxx/2.txt:test

```

---

### Post by winzip on 2012-04-07
> **Vaphell said:**
> in my case (10.04) zgrep shows that the phrase is somewhere inside the archive, but doesn't show where
```
$ zgrep test zip.zip 
test
$ zipgrep test zip.zip 
1.txt:test
2.txt:test
xxx/1.txt:test
xxx/2.txt:test

```

I'm using   ubuntu 10.04  server  os  edition.

whats  the  solution to  my  problem then ?

---

### Post by Vaphell on 2012-04-07
if you want the exact location then zipgrep, apparently. There is no difference if it's server or desktop edition as they share common repositories (desktop is by default loaded with more user oriented bling which is not necessary for servers)

---

### Post by lisati on 2012-04-07
Are you looking for [LIST=1]
[*]myapps.zip
[*]/home/user/appkey
[*]Something else?
[/LIST]

---

### Post by codemaniac on 2012-04-07
> **Vaphell said:**
> in my case (10.04) zgrep shows that the phrase is somewhere inside the archive, but doesn't show where
```
$ zgrep test zip.zip 
test
$ zipgrep test zip.zip 
1.txt:test
2.txt:test
xxx/1.txt:test
xxx/2.txt:test

```

zgrep should be be used when a single fat file is gzipped .
Otherwise when multiple text files are zipped in one single zip file , zipgrep is designed for that purpose .

---

