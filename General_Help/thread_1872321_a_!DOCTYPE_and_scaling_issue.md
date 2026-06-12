---
title: "a !DOCTYPE and scaling issue"
date: 2011-10-30
forum: General Help
---

### Post by maclenin on 2011-10-30
In a nutshell: I am trying to scale a web site - using javascript - to fit the viewport of an iPad.

The structure of the web site lends itself to "simple" scaling (of divs and images) - upon detection of an "iPadder".

This "listener"...```
if (navigator.userAgent.match(/iPad/i))
```...triggers a scaling function, which, essentially, shrinks ("optimizes") the site to fit the iPad.

I have run the listener / scaling function on a "test" page - without a !DOCTYPE declared - the javascript runs and the site is scaled. 

The same function does NOT work on the "live" site, which has the following !DOCTYPE declared:```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

NB0: The function works if I <!-- comment out !DOCTYPE --> from the live site.
NB1: The function does NOT work if I add a !DOCTYPE to the test page.

Why might the scaling function fail - with a !DOCTYPE declared?

I have Firebug (1.8.3) enabled - and she's not picking up any javascript errors.

I have other / similar javascript re-sizing and re-placement / slideshow functions working in the live site - to flawless effect. Curious.

Thanks for any thoughts!

---

### Post by maclenin on 2011-11-01
After further review, it seems it was a (simple) coding oversight on my part - the !DOCTYPE required that I be a tad more rigorous re: certain elements - merely adding a "px" [SOLVED] the problem for me....

It's cleaned up and working now.

...you know what they say about what lurks in the details....

---

