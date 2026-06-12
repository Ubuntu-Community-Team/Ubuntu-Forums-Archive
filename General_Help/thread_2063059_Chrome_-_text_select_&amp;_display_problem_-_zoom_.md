---
title: "Chrome - text select &amp; display problem - zoom related"
date: 2012-09-26
forum: General Help
---

### Post by Ace..... on 2012-09-26
In a text field you might place the cursor, and backspace over text, but the effects are not displayed - unless you zoom out or in (ctrl+ or -).

You try to highlight text, but nothing is highlighted in the display. Yet, if you right click you are offered the option to search on the highlighted text.

It doesn't happen all the time.

Some months ago, I spent ages trying to configure a search for the solution, and eventually found it (something disabled or removed via Terminal)

However, since the re-install, I have the problem again, though have totally failed to find the answer this time around. :sad:

---

### Post by Frogs Hair on 2012-09-26
When you removed Chrome the last time did you remove the folders also or is this a new Chrome installation on a new Ubuntu installation ?

---

### Post by Ace..... on 2012-09-26
> **Frogs Hair said:**
> When you removed Chrome the last time did you remove the folders also or is this a new Chrome installation on a new Ubuntu installation ?

I didn't specifically delete anything.

I did the re-install using same name and password, so my home folder was kept.
Other than home dir it was a full install.
All previously downloaded progs required downloading again.

Chrome being one of them.

All my bookmarks were in place, but it seems that the config command, previously entered into terminal, is not.

---

### Post by Frogs Hair on 2012-09-27
I was wondering about the folder because profile changes are normally kept if the folder regardless of re-installing. I can only suggest trying to retrace your steps or wait for a user who knows exactly what you did the first time. Based on your description I can't duplicate the problem in Chrome.

---

### Post by Ace..... on 2012-10-01
> **Frogs Hair said:**
> I was wondering about the folder because profile changes are normally kept if the folder regardless of re-installing. I can only suggest trying to retrace your steps or wait for a user who knows exactly what you did the first time. Based on your description I can't duplicate the problem in Chrome.
Oh wow.... it's now terrible today.
I'm writing this blind.
If I want to see what I'm writing I need to click ctrl+ or ctrl-.
Why?
Because I'm writing this directly into the message text area.

I know I'm not the only one to suffer this problem, cos I found the fix a few months ago.
what I dont understand is why google haven't fixed the problem.

I think I need to contact google ...... which I have just done. :)

---

### Post by Ace..... on 2012-10-01
I posted the prob on the chrome help forum.
I then searched on 'chrome text field problems'
(I thought I'd keep trying).

The support pages are full of complaints that go back years - and every post has a whole ream of 'me too' posts attached.

Plus a lot of complaints that google aint responding.

Why didn't I bookmark the fix - what a plonker :???:

---

### Post by Ace..... on 2012-10-01
Okay,
I think it may be something to do with this command:

```
google-chrome –disable-bundled-ppapi-flash
```

I can't be certain, but it rings a bell, and apparently it is a fix for a number of issues.
However, I'm not sure how to apply it because there was more to it than just this.

I ran the command anyway, but it wasn't recognised, though chrome loaded with an oops page.

I think I had to get something first

I found this post: 
[http://askubuntu.com/questions/158009/google-chrome-freezes-for-seconds](http://askubuntu.com/questions/158009/google-chrome-freezes-for-seconds)

I've checked and I already have adobe flash plugin installed, but I have no version of pepperflash to disable.

---

### Post by Ace..... on 2012-10-01
Okay I found this:

google-chrome --disable-bundled-ppapi-flash %U

This command worked.
Flash video still plays.
The text field problem seems to have disappeared (though it was always intermittent)
Google chrome appears to have doubled its response time - it immediately seemed bizarrely responsive.

The post suggested that this should be added to the chrome command line.
Something like this:

/opt/google/chrome/google-chrome --disable-bundled-ppapi-flash %U

However, I don't know how to do this.
I had a look in /opt/google/chrome/
and saw the google-chrome shell script, but it wasn't apparent what the next step was.

Perhaps someone might help. :)

Okay here is the fix:

[http://ubuntuforums.org/showthread.php?t=2065621](http://ubuntuforums.org/showthread.php?t=2065621)


:)

---

