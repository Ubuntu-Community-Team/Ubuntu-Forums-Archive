---
title: "xnee not syncronized with java apps"
date: 2010-07-21
forum: General Help
---

### Post by Cezy on 2010-07-21
As xnee official packages did not work for me, I downloaded, compiled and installed the latest xnee version (3.06). It work almost well, but if I try to automate the execution of a Java web application, xnee lost the synchronization and give me this error:

```

Can't synchronize anymore .... have to leave!  11 10 
Error number: 5
  Error:      Synchronisation failure
  Solution:   For more information on this error, please read the manual(s)

```

I catch this error even when I try to automate firefox visiting website with flash pages.

Any suggestion? There is a xnee forum where I can contact the authors?

Waiting for any answer, I will go to the cinema to watch "Predators" :popcorn:

---

### Post by hesa on 2010-07-24
Xnee does not care about the app(s) or graphical tool kits you are executing (be they flash, mozilla, python, java, guile, gtk, qt....). It operates on the windowing system level.

I suggest reading the doc ([http://itupw056.itu.chalmers.se/xnee/doc/xnee.html](http://itupw056.itu.chalmers.se/xnee/doc/xnee.html)), especially:
  [http://itupw056.itu.chalmers.se/xnee/doc/xnee.html#SEC105](http://itupw056.itu.chalmers.se/xnee/doc/xnee.html#SEC105)

if you are bold (just as the axis), disable synchronisaton (cnee -ns) when replaying. 

For bug reporting:
   [http://savannah.gnu.org/projects/xnee](http://savannah.gnu.org/projects/xnee)
or 
 [http://lists.gnu.org/mailman/listinfo/bug-xnee](http://lists.gnu.org/mailman/listinfo/bug-xnee)


/hesa

---

