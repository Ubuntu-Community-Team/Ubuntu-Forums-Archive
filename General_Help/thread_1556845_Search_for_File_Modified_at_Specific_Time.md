---
title: "Search for File Modified at Specific Time"
date: 2010-08-20
forum: General Help
---

### Post by CLCressman on 2010-08-20
[LIST=1]
[*]How do you find a file modified March 17, 2010, between 3:30 pm and 4:05 pm? I know that I must be missing something somewhere.
[*]How do you search for info like this? I goggled "search files time Linux" and got about 38,300,000 results. I looked through the first four pages and did not see what I was looking for.
[*]Do I need to calculate how many minutes ago that is and give that to _find_*.*
[*]I really want to do this in the GUI so that I can operate on the files found without typing in so much stuff.
[/LIST]

---

### Post by CLCressman on 2010-08-20
> **CLCressman said:**
> 
[LIST=1]
[*]How do you find a file modified March 17, 2010, between 3:30 pm and 4:05 pm? I know that I must be missing something somewhere.
[*]How do you search for info like this? I goggled "search files time Linux" and got about 38,300,000 results. I looked through the first four pages and did not see what I was looking for.
[*]Do I need to calculate how many minutes ago that is and give that to _find_*.*
[*]I really want to do this in the GUI so that I can operate on the files found without typing in so much stuff.
[/LIST]

1. and 3. I got an inspiration. I opened terminal in /tmp, and executed the following commands.
```
touch -t 03171530 t1
touch -t 03171605 t2
sudo find / -mount -type f -newer t1 -not -newer t2 -fprint0 result
```I used *sudo* as I thought I might want results from restricted directories. I opened *result* with a hex editor because my first two choices did not display it properly.

Does anyone have a different suggestion? How about 2. and 4.?

---

