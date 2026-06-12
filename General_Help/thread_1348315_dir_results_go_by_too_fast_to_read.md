---
title: "dir results go by too fast to read"
date: 2009-12-07
forum: General Help
---

### Post by magnetsandlasers on 2009-12-07
I have a directory with a few thousand files in it.

If I run the dir or ls commands the files go by too fast to read and if I scroll up I can only see the last few hundred. 

What argument or command can I use to view the files at the top of the list?

I would think this would be an easy question to find the answer to but I have been searching and googling for 90 mins and I have found nothing. The man pages were equally unhelpful. What am I missing?

---

### Post by chillicampari on 2009-12-07
Try

```

ls | more 
```then you can spacebar through each page of the list.

"q" will get you back out.

---

### Post by magnetsandlasers on 2009-12-07
Aha! Chillicampari, in the drawing room, with a pipe! 

Thank you!

---

### Post by chillicampari on 2009-12-07
You're welcome, glad it helped!

(slinks off to the study, with a candlestick :D)

---

### Post by hawthornso23 on 2009-12-07
ls | more

or

ls | less

... more or less  ;-)

---

