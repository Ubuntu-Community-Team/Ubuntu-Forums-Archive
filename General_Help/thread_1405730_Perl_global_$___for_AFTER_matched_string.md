---
title: "Perl global $_  for AFTER matched string"
date: 2010-02-13
forum: General Help
---

### Post by B34ST1Y on 2010-02-13
need help in Perl. I can't find the global variable for $_ (except not $_ it's the one to specify AFTER the matched string.) its dollar sign then something else. Does anyone have a cheat sheet for global symbols? 


Many thanks!

---

### Post by B34ST1Y on 2010-02-13
for reference purpose....I found what I was looking for. 

[http://perldoc.perl.org/perlreref.html](http://perldoc.perl.org/perlreref.html)

> 

   1.  $_ Default variable for operators to use
   2.
   3. $` Everything prior to matched string
   4. $& Entire matched string
   5. $' Everything after to matched string
   6.
   7. ${^PREMATCH} Everything prior to matched string
   8. ${^MATCH} Entire matched string
   9. ${^POSTMATCH} Everything after to matched string


---

