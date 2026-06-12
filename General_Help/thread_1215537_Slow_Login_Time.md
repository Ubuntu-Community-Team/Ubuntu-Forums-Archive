---
title: "Slow Login Time"
date: 2009-07-17
forum: General Help
---

### Post by Bubblebeard on 2009-07-17
Hi,

I recently reinstalled ubuntu then configured everything the way I like it.  However, it originally logged in in ~12 seconds (from when I enter username and pw) but now it takes over twice that.  I don't have that much flashy stuff, though I have some.

Is there a way to find out what is taking most of that time so that I can disable whatever is slowing my startup down?

Thanks!

---

### Post by Bubblebeard on 2009-07-18
Can anyone please help with this?

---

### Post by Bubblebeard on 2009-07-22
There must be some way to do this.  I have looked around a lot but have found none... :confused:

Any help would be greatly appreciated 	[-o<

Thanks!

---

### Post by Buttons840 on 2009-09-07
I'm having the same issue.  I used to login in, I'd guess, 5 seconds or less.  Now it takes just over 20 seconds to log in.  I can't identify any changes I've made to the system that would have caused this?  Although, I have been installing the automatic updates.

It would be nice to have some kind of visual indication of login progress, is there anyway to see any useful information instead of the usual black screen?

At one point I ran into the fallowing problem:

[http://www.youtube.com/watch?v=Az4dQxhtEKs](http://www.youtube.com/watch?v=Az4dQxhtEKs)

I eventually solve this problem by reinstalling.

In both cases it don't recall having installed anything or made any system changes.  From my perspective it just seems Ubuntu degrades to this type of performance over time.

---

### Post by gradysghost on 2009-09-07
To both of you -- Can you tell us what software is being launched automatically when you log in?

The contents of the autostart directory are a good place to start looking.  That's in your home directory: ~/.config/autostart  If you're going to look using your file browser, you'll need to turn on hidden folders.  If you want to do this quickly, execute this command:

```
ls ~/.config/autoconfig > ~/Desktop/autostart.txt
```

That will create a file on your desktop.  Please paste the contents of that file into this board, and I'll gladly take a look at it.

Also, for what it's worth, what are your systems' specs?

---

### Post by gradysghost on 2009-09-18
Sorry.  My code was bad.  Let's try this instead:

```
ls ~/.config/autostart > ~/Desktop/autostart.txt
```

---

