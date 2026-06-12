---
title: "Nautilus gone crazy!"
date: 2009-10-02
forum: General Help
---

### Post by bogdan_5844 on 2009-10-02
Ok,this evening I started my computer as usual, and from nowhere nautilus popped up to me looking weird.
Look at this: 
[http://img203.imageshack.us/img203/9528/screenshote.png](http://img203.imageshack.us/img203/9528/screenshote.png)

I don't really like the fact that the location bar is on the same row with the left/right/up/blablah bar.
How can I change this to default?
Tried purging nautilus then installing again,tried removing configuration from home folder,to no avail.On other accounts, the same thing happens.
Please,NO comments such as "it's better that way because it gives more screen space" because I prefer wasted space instead of crappy navigation (I really use the breadcrumb navig a lot)

Is there some trigger somewhere to move this back to it's place?
On the View menu it doesn't show separate Location Bar and Toolbar (or something like that)

Ubuntu 9.04

---

### Post by Giblet5 on 2009-10-02
Did you try creating a test user and seeing if it's the same there?

Does your cat drink a lot of "energy" drinks and frequent the hacker forums?

---

### Post by bogdan_5844 on 2009-10-02
Yes,on new user accounts it is the same.

Didn't get the joke about the cat...:confused:

---

### Post by Giblet5 on 2009-10-02
I insinuated that your cat has Mad Hacker Skillz. It's a joke that plays on the inherent mysterious nature of cats.

So, someone changed the system-level settings for Nautilus and you have no idea who or how or why?

These are (mostly) kept in /usr/share/nautilus/ui and I hope you like XML. Reinstalling nautilus won't fix them.

It probably makes the most sense to copy them from the Live CD after you make a short-term backup of what you have via
```
tar cf ~/naughtylus.tar /usr/share/nautilus/ui
```

---

### Post by bogdan_5844 on 2009-10-02
Thanks! Edited the .xml's to suit me(copied the ones from the livecd..no result)
Still not like the default,but it works :-)
Thanks a bunch!

---

### Post by SQuark on 2009-10-02
Same thing happened to me yesterday.
And this guy: [http://www.uluga.ubuntuforums.org/showthread.php?p=8042459#post8042459](http://www.uluga.ubuntuforums.org/showthread.php?p=8042459#post8042459)

What the hell is going on??

---

### Post by t4ggs on 2009-10-02
[http://ubuntuforums.org/showthread.php?t=1277187](http://ubuntuforums.org/showthread.php?t=1277187)

---

