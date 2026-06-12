---
title: "Moving 5 random files from a folder to another folder"
date: 2011-11-01
forum: General Help
---

### Post by raamkum on 2011-11-01
Hi,
 
I have 200 pictures in a folder and I would like move 10 random pictures every week to given folder automatically. 
 
I have this server on 1and1.com.
 
So I tried the following using Bash script for manual copy and paste for testing:
 
```
 
#!/bin/bash
mapfile -t -n 3 files < <(find /homepages/mylocation/location/htdocs/release/randompics/ -type f | sort -R)
cp --backup=numbered "${files[@]}" /homepages/mylocation/mylocation/htdocs/release/pictures/

```
 
Got the above code from one of the thread from this forum.
 
when I execute this script on my linux machine I get:
 
> sort: invalid option -- R
Try `sort --help' for more information.
cp: missing destination file operand after `/homepages/mylocation/mylocation/htdocs/release/sites/default/files/banner/'
Try `cp --help' for more information.
(uiserver):u35495245:~ > sort: invalid option -- R
Try `sort --help' for more information. 
 
NOTE: 'mylocation' is just my reference. I have changed it for privacy issue. 
 
I am not sure about the above error.
 
So I tried another method:
 
```

 
ls | while read x; do echo "`expr $RANDOM % 1000`:$x"; done \ | sort -n| sed 's/[0-9]*://' | head -5
 

```
 
The above script prints out the 5 random file to the variable. now I don't know how to copy file to another folder from a variable. If I can do this then I will be able to achieve whatever I want to do.
 
Can somebody help me out? 
 
Awaiting your response!
 
Thanks!

---

### Post by sisco311 on 2011-11-01
Check out BashFAQ 026 (link in my signature).

---

