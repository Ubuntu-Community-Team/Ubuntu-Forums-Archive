---
title: "need help in getting a webpage"
date: 2011-06-30
forum: General Help
---

### Post by dragonflyFZX on 2011-06-30
hello all,

I want to download a webpage to extract information. This used to work with other pages, but with this particular page ([http://www.farmgainafrica.org/index.php?option=com_content&view=article&id=5&Itemid=27](http://www.farmgainafrica.org/index.php?option=com_content&view=article&id=5&Itemid=27)), I get the following error.

```
bjvca@ifpri-laptop:~$ wget http://www.farmgainafrica.org/index.php?option=com_content&view=article&id=5&Itemid=27
[1] 10375
[2] 10376
[3] 10377
bjvca@ifpri-laptop:~$ --2011-06-30 16:10:05--  http://www.farmgainafrica.org/index.php?option=com_content
Resolving www.farmgainafrica.org... 173.212.204.162
Connecting to www.farmgainafrica.org|173.212.204.162|:80... connected.
HTTP request sent, awaiting response... 404 Article #0 not found
2011-06-30 16:10:05 ERROR 404: Article #0 not found.

```

what goes wrong?

d

---

### Post by dragonflyFZX on 2011-06-30
ok, it seems putting the address in quotes saves the page. Still I dont get all information. That is, how can I set the show entries drop down box to 100 before I download the page?

d

---

### Post by Cheesehead on 2011-06-30
Look at the html source for that page. All 22 rows of data **are** in the HTML; a javascript feature limits the browser display to 10 by default. You cannot change that in wget - it gets created in your browser (not the server) after the download.

So you are getting the data you want.

---

### Post by Habitual on 2011-06-30
```
curl "http://www.farmgainafrica.org/index.php?option=com_content&view=article&id=5&Itemid=27" -o x.html
```works for me here. YMMV

Cheesehead is right. 10 rows.

---

