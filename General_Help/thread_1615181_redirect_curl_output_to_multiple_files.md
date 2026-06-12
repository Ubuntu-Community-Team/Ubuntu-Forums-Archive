---
title: "redirect curl output to multiple files"
date: 2010-11-06
forum: General Help
---

### Post by techbrainless on 2010-11-06
Hi All,  I am using curl as the following ```
 curl &quot;http://site.com/pages/{1,2,3,4,5}.html&quot; > /home/myuser/allpages.html 
``` i need to save each page in a separate page     by the way i have tried this command  ```
 curl &quot;http://site.com/pages/{1,2,3,4,5}.html&quot; > /home/myuser/{1,2,3,4,5}.html 
``` but it displays error ```
 ambiguous redirect 
```   is there any way to do that ..........  thanks all.

---

### Post by techbrainless on 2010-11-06
Hi All, any reply ?

---

### Post by luigi_mb on 2010-11-06
Try "tee".

```

man tee

```

/luigi

---

### Post by techbrainless on 2010-11-07
Hi luigi thanks alot for your reply ,

I have redirecting the output using tee as the following 

```
curl "http://site.com/pages/{1,2,3,4,5}.html" | tee 1.html 2.html 3.html 4.html 5.html
``` but am not getting each page separately , I am getting the contents of whole 5 pages in the each single file , that is the content
 of all files (1.html , 2.html , 3.html , 4.html , 5.html) are same 
 
 Could you please help............

---

### Post by dcstar on 2010-11-07
> **techbrainless said:**
> Hi luigi thanks alot for your reply ,

I have redirecting the output using tee as the following 

```
curl "http://site.com/pages/{1,2,3,4,5}.html" | tee 1.html 2.html 3.html 4.html 5.html
``` but am not getting each page separately , I am getting the contents of whole 5 pages in the each single file , that is the content
 of all files (1.html , 2.html , 3.html , 4.html , 5.html) are same 
 
 Could you please help............

Read the curl man page:

```
curl http://{site,host}.host[1-5].com -o "#1_#2"
```

---

### Post by techbrainless on 2010-11-08
Thanks alot docstar.

It worked fine for me , here is some of what i have executed :


```
curl "http://site.com/pages/{1,2,3,4,5}.html"  -o page#1.html
```or ( it is the same as )

```
curl "http://site.com/pages/[1-5].html"  -o page#1.html
```

---

