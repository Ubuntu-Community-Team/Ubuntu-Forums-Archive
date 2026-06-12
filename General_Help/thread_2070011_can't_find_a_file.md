---
title: "can't find a file"
date: 2012-10-11
forum: General Help
---

### Post by unibroker on 2012-10-11
I was told by the terminal that I already had a file and Package Manager confirms this but when I search the Home directory it comes up with nothing.

---

### Post by papibe on 2012-10-11
Hi unibroker.

What package?
Could you post that command and its results?

BTW, usually packages are not store on the Home directory.

Regards.

---

### Post by unibroker on 2012-10-11
> **papibe said:**
> Hi unibroker.

What package?
Could you post that command and its results?

BTW, usually packages are not store on the Home directory.

Regards.

**sun-java6-jdk**

I have a feeling that I use the terms **files** and **package** interchangeably and I shouldn't.

---

### Post by Bashing-om on 2012-10-11
Seems a strong indication the "file" is located some place else.
If It is a file you seek to find; terminal code:
```
sudo find / -name <file-name you are looking for>
```which searches from the root directory recursively for the named file's location.
see the manual for complete details:
```
man find
```[INDENT]hth <==BDQ

[/INDENT]

---

### Post by papibe on 2012-10-11
Could you post the result of these commands?
```
apt-cache policy sun-java6-jdk

java -version
```
Regards.

---

### Post by unibroker on 2012-10-11
> **Bashing-om said:**
> Seems a strong indication the "file" is located some place else.
If It is a file you seek to find; terminal code:
```
sudo find / -name <file-name you are looking for>
```which searches from the root directory recursively for the named file's location.
see the manual for complete details:
```
man find
```[INDENT]hth <==BDQ

[/INDENT]

Thank you!  I've found it in /etc.  I need to review file systems!

---

### Post by unibroker on 2012-10-11
> **papibe said:**
> Could you post the result of these commands?
```
apt-cache policy sun-java6-jdk

java -version
```
Regards.

Thanks for your help but I found it in /etc.  Now I hope I'm able to move it to my android location.  Still learning!

---

### Post by jerrrys on 2012-10-11
nevermind

---

