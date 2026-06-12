---
title: "wget to download blogger of blogspot.com"
date: 2012-04-26
forum: General Help
---

### Post by techbrainless on 2012-04-26
Hi All,
I used the following wget command to download wordpress blogs

```
$ wget -r -Nc -mk --recursive  --page-requisites --html-extension --no-parent --convert-links  http://myblogger.wordpress.org/

```
but when It wont work for blog site of blogger.com(myblogger.blogspot.com) it will not update the links/labels/archives

```
$ wget -r -Nc -mk --recursive  --page-requisites --html-extension --no-parent --convert-links  http://myblogger.blogspot.com/
```

---

### Post by techbrainless on 2012-04-27
any suggestion

---

### Post by techbrainless on 2012-04-28
any suggestion

---

### Post by techbrainless on 2012-04-30
any suggestion

---

### Post by techbrainless on 2012-05-01
?

---

### Post by techbrainless on 2012-05-14
Hi All any one at least can give me tips regarding the above issue ?

All the tips/advises/replies are appropriated .

---

### Post by HiImTye on 2012-05-14
remove the 'c' from '-Nc' and it should download your file so that it is like:
```
wget -r -N -mk --recursive  --page-requisites --html-extension --no-parent --convert-links  http://myblogger.blogspot.com/
```

---

### Post by techbrainless on 2012-05-15
Thanks HiImTye for your reply , 

> remove the 'c' from '-Nc' and it should download your file so that it is like:but the option c is for Continue getting a partially-downloaded file

anyhow I will execute the command and feed you back , thanks again

BTW I have tested the same command with option 'c' with blogger at word press and it worked fine . the problem only with bloggers at  blogspot site

---

### Post by techbrainless on 2012-05-15
Thanks HiImTye for your reply ,

>  			 				remove the 'c' from '-Nc' and it should download your file so that it is like: 			 		

It does not work even so after removing the option 'c'

here is the command I have executed 
```
$ wget -r -N -mk --recursive  --page-requisites --html-extension --no-parent --convert-links  http://myblogger.blogspot.com/
```

---

### Post by techbrainless on 2012-05-15
All the tips/advises/replies are appropriated .

---

### Post by HiImTye on 2012-05-15
paste the output of the command, you are asking us to solve this without giving us any insight into what's actually happening

---

### Post by techbrainless on 2012-05-15
Thanks HiImTye for your reply , 

command with option 'c':
```
$ wget -r -Nc -mk --recursive  --page-requisites --html-extension --no-parent --convert-links  http://ciornabg.blogspot.com/

```

command without option 'c':
```
$ wget -r -N -mk --recursive  --page-requisites --html-extension --no-parent --convert-links  http://ciornabg.blogspot.com/
```

---

### Post by techbrainless on 2012-05-16
All the tips/advises/replies are appropriated .

---

### Post by techbrainless on 2012-05-18
All the tips/advises/replies are appropriated .

---

### Post by techbrainless on 2012-06-04
All the tips/advises/replies are appropriated .

---

### Post by techbrainless on 2012-06-30
All the tips/advises/replies are appropriated .

---

### Post by |{urse on 2012-06-30
Maybe if you keep repeating that someone will help faster!

---

