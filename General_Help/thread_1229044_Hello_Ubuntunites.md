---
title: "Hello Ubuntunites"
date: 2009-08-01
forum: General Help
---

### Post by weedeater64 on 2009-08-01
I was hoping some one could nudge me in the right direction on this. I was in another forum,

[http://sfbay.craigslist.org/forums/?ID=132177575](http://sfbay.craigslist.org/forums/?ID=132177575)

And some one posted the handles and number of posts for each. They said they used a macro to do the counts for them, I would like to do this also. I know very little about scripting, meaning I could get bash to say "hello world" only if I went back and found the instructions again. So I was wondering if ubuntu has an easy to use tool that would do this for me.

                   Thanks, Jeff.

---

### Post by aesis05401 on 2009-08-01
If there is not a function on the website to provide the info, and you are gathering it an automated fashion it is known as scraping.  I have no idea what this forum's policy on scraping is, but generally it is the sort of thing that is expressly prohibited in web sites' TOS.  It would be wise to do a bit more research on the issue before actually trying to scrape a site or you will end up with a bad reputation and some IP bans ;)

---

### Post by weedeater64 on 2011-01-08
Follow up.. Wow, this was a while back..
I actually found the answer to this elsewhere, within a day or two.
I don't recall where, perhaps OpenOffice forums... idk..

Anyway, what I do is select the entire text on that page, copy it to a .txt file then run this on the file,

```
cat totals.txt | egrep -o '<[^>]+>' | sort | uniq -c | sort -rn
```

and I get this,

9 < chichooch >
8 < Most_Spiritual_One >
8 < aaiou >
7 < saawftx >
7 < Gunthar2011 >
6 < spagirl74 >

---

