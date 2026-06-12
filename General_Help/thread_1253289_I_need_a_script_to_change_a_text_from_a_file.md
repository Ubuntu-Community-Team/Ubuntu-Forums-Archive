---
title: "I need a script to change a text from a file"
date: 2009-08-29
forum: General Help
---

### Post by sorino737 on 2009-08-29
PLS. can some one help me with a script that change some numbers from a text in a file. 
I need to download some pic from a web site weekly and i use a file with the links as input for wget. In the file a have the link for every pic from pict01 to pict19. What i need is to change the numbers from the links that specifies the folder number. (ex. http//www.site.com/picture/folder101/pict1.jpg) and every week i need an editor to replace 101 with 102. 

Is there any solution because I want to schedule this task. 

Thank you very much

PS> I am a very beginner.

---

### Post by mathfeel on 2009-08-29
> **sorino737 said:**
> PLS. can some one help me with a script that change some numbers from a text in a file. 
I need to download some pic from a web site weekly and i use a file with the links as input for wget. In the file a have the link for every pic from pict01 to pict19. What i need is to change the numbers from the links that specifies the folder number. (ex. http//www.site.com/picture/folder101/pict1.jpg) and every week i need an editor to replace 101 with 102. 

Is there any solution because I want to schedule this task. 

Thank you very much

PS> I am a very beginner.

```
#!/bin/sh
for x in $(seq -w 1 19); do
  wget http://url/folder${1}/pict${x}.jpg;
done
```

then run it as, e.g.
```
./getpicts.sh 101
```

Add it to cron to schedule regular run.

---

### Post by sorino737 on 2009-08-30
Thank you very much!

---

