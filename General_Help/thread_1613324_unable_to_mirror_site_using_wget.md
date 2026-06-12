---
title: "unable to mirror site using wget"
date: 2010-11-04
forum: General Help
---

### Post by nitstorm on 2010-11-04
Hey there

Thanks for taking a look at the thread. 

I am trying to wget a site so that I can read stuff offline.

I have tried
```
 wget -m sitename
wget -r -np -l1 sitename

```but can't navigate beyond the home page from the downloaded content.

I just need the right parameters, so help please and thanks in advance :)

P.S: Also, I saw a lot of folders with .asp extensions. Is that the root of the prob?

---

### Post by nitstorm on 2010-11-04
Also tried
```

wget -m -E sitename

```but the pages ain't linking at all. Firefox says unable to find defaults.asp (coz it got renamed to defaults.asp.html wen i used the -E argument)

Also just noticed that the default.asp file has nothing in the <body> tag...

---

### Post by nitstorm on 2010-11-05
Bump!

---

### Post by nitstorm on 2010-11-06
Bump!!!

---

### Post by nitstorm on 2010-11-06
Bump!!!

---

### Post by nitstorm on 2010-11-07
I am getting seriously bored of bumping this. This will be my last bump. 

B-U-M-P!!!

---

### Post by geoffmcc on 2010-11-07
I recently tried to mirror a site for offline browsing. Havent done so in forever.

I too had troubles. I chalked it up to the site having some sort of protection against it like how robots.txt will stop a crawlbot.

I googled that theory and didnt come up with anything.
but maybe this will help

[http://fosswire.com/post/2008/04/create-a-mirror-of-a-website-with-wget/](http://fosswire.com/post/2008/04/create-a-mirror-of-a-website-with-wget/)

---

### Post by nitstorm on 2010-11-07
I tried wget -m -k sitename but to no avail, maybe it's got a special way of treating robots as you said. But the thing is all the pages on the site have an ending with .asp Eg: [http://www.sitename.com/defaults.asp](http://www.sitename.com/defaults.asp)

---

