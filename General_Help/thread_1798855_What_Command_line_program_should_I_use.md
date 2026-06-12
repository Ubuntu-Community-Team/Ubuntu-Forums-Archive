---
title: "What Command line program should I use?"
date: 2011-07-06
forum: General Help
---

### Post by conradin on 2011-07-06
Hi all,
Im going to do a web based search for several thousand webpages which may or may not exist. 
I just want a list of the addresses which work. I dont want to load into firefox, and I'd preffer not to ping the url. I just want to test the URLs for validity and kick back a list of good URLs. 
Any Ideas on a simple program to do this, which I can use in a bash script?

---

### Post by enimeizoo on 2011-07-07
Did you try wget with the option --spider?
I actually never used that option, but it "will not download the pages, just check that they are there", according to the manual.

---

### Post by conradin on 2011-07-07
Hey, i like that Idea! i was trying wget, but didnt like how i was getting a folder downloaded each time I used it.... But this might work!

---

