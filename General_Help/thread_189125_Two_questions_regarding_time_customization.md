---
title: "Two questions regarding time customization"
date: 2006-06-04
forum: General Help
---

### Post by Madstone on 2006-06-04
Two questions I hope will be easier to answer.

How can I modify the logon screen to use the 24hr format instead of the default 12hr format?

How can I modify the creation of all new users to use the 24hr format for their sessions using the gnome user management tool?

---

### Post by thingy on 2006-06-08
For the logon screen, it may turn out that the time is actually part of the theme code and hence no config option to twiddle.

hmm I wonder if you can tweak your locale settings to do what you want.

For example:
LC_TIME  - Changes the behaviour of the strftime() function to display the current time in a locally acceptable form; for example, most of Europe uses a 24-hour clock vs. the US' 12-hour clock. 

So something like export LC_TIME="en_US" might do what you want. The variable needs to be made permanent by putting it in your /etc/profile or such.

---

