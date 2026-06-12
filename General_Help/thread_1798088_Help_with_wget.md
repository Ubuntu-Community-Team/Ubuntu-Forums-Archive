---
title: "Help with wget"
date: 2011-07-05
forum: General Help
---

### Post by 98cwitr on 2011-07-05
So this, in my understanding, should download all .pdf files from this site...unfortunately it only downloads the damn index and folder structure. Why doesn't it grab the .pdfs?

```

wget -r -A .pdf http://www.nicoclub.com/FSM/Altima/2002/
```

wtf am I doing wrong here?

---

### Post by sidzen on 2011-07-05
Try 
. . . 
[http://www.nicoclub.com/FSM/Altima/2002/](http://www.nicoclub.com/FSM/Altima/2002/)***.pdf**

---

### Post by 98cwitr on 2011-07-05
Wildcards are not supported by HTML. I tried that :(


output

> 
:~$ wget [http://www.nicoclub.com/FSM/Altima/2002/*.pdf](http://www.nicoclub.com/FSM/Altima/2002/*.pdf)
Warning: wildcards not supported in HTTP.
--2011-07-05 21:01:24--  [http://www.nicoclub.com/FSM/Altima/2002/*.pdf](http://www.nicoclub.com/FSM/Altima/2002/*.pdf)
Resolving [www.nicoclub.com](www.nicoclub.com)... 216.92.96.26
Connecting to [www.nicoclub.com|216.92.96.26|:80](www.nicoclub.com|216.92.96.26|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-07-05 21:01:25 ERROR 404: Not Found.


---

### Post by Vaphell on 2011-07-05
you can always check index.html for pdf names and wget them explicitly

```
grep -o '[a-z]*.pdf' index.html | uniq | while read pdf
do
  wget http://www.nicoclub.com/FSM/Altima/2002/$pdf
done
```

---

### Post by erind on 2011-07-05
To prevent huge loads on the servers, many site admins don't allow users to download huge portions of their sites. Try this instead:

```
wget -e robots=off --wait 1 -r  http://www.nicoclub.com/FSM/Altima/2002/
```

---

### Post by 98cwitr on 2011-07-05
> **erind said:**
> To prevent huge loads on the servers, many site admins don't allow users to download huge portions of their sites. Try this instead:

```
wget -e robots=off --wait 1 -r  http://www.nicoclub.com/FSM/Altima/2002/
```

that got it...thank you!

---

### Post by Habitual on 2011-07-05
```
wget -e robots=off --wait 1 -r  http://www.nicoclub.com/FSM/Altima/2002/ -P/tmp -A".pdf"
```

and check /tmp/www.nicoclub.com/* for PDFs

---

