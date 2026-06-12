---
title: "How does one measure &quot;lightness&quot;?"
date: 2012-09-30
forum: General Help
---

### Post by vasa1 on 2012-09-30
I've been wanting to ask this for a while but haven't.

How do we objectively measure "lightness"? Assuming we change just one variable at a time, how can the effect of that one change be measured?

I'm not technically proficient so my question maybe quite stupid ...
Is there some way to monitor how many CPU cycles are consumed to perform a specific task (performed with and without a single change.)

If not CPU cycles then is there something more appropriate?

Just for example ...
Say we have a long page of text in a local html page with two "varieties":
1. Every letter of that text is "text-shadowed".
2. Nothing is text-shadowed.

My "guess" is that displaying the page in a browser with shadowed text would take more resources than displaying that text without a shadow. But how can I prove or disprove that?

---

### Post by HiImTye on 2012-09-30
use 'ps' it displays CPU time in the 'TIME' field. you likely want to use it as either 'ps -e' (every process), or 'ps -ef' (every process with full command paths and arguments), although you can use it in a variety of different ways and customize the information that it outputs.
```
man ps
```

---

### Post by vasa1 on 2012-09-30
Thank you!

I'm going to try it out on a non-default browser working off-line for simplicity.

---

### Post by Lars Noodén on 2012-09-30
You can also use [time](http://manpages.ubuntu.com/manpages/precise/en/man1/time.1.html) preceeding your program to measure the amount of processing resources it used as it ran.

```

time ls
time ll

```

---

### Post by vasa1 on 2012-10-01
This is what I did and at the outset, I'll make it clear that I didn't see any difference!
I made an html file like this:
```

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN">
<html>
<head>
<meta http-equiv="content-type" content="text/html; charset=ISO-8859-1">
<title>Test</title>
</head>
<body style="background-color: #888888;">
<style type="text/css">
</style>
<pre>* {text-shadow: 2px 2px #333333;}</pre>


Lot's of text.


 </body>
 </html>

```
The file is ~ 4.8 MB.

I opened Seamonkey and chose "Work Offline".
I opened a terminal window and got the process ID for Seamonkey (1234 for example).
In the same terminal I ran
```
ps 1234
```
and noted the "time".
I switched to Seamonkey and loaded the file. Switched back to the terminal and ran
```
ps 1234
```
and noted the "time".
I switched back to Seamonkey. Cleared the cache, noted the "time", reloaded the file, noted the "time". I did this a few times.

Then, I repeated the whole process with the text-shadow code placed within the style tags.

I was expecting a significant increase in the "time" but it was virtually the same even though each and every letter in the body of the html file now had a text-shadow.

I did the whole exercise with Midori as well. No difference.

So either I'm not doing things properly or text-shadow isn't a big deal at all (as I had feared it would be).

(My computer is a Dell Inspiron 1545 laptop; core2 Duo from 2009 and it can run "Unity 3D" without choking.)

---

