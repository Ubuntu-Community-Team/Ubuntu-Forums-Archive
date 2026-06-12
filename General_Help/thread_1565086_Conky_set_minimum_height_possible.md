---
title: "Conky set minimum height? possible?"
date: 2010-08-31
forum: General Help
---

### Post by polardude1983 on 2010-08-31
Ok So i have a gmail checker script that says how many unread messages i have and it displays the subject and who it is from. I also have another script below it to display my twitter feed.

It all looks good and fine when there are emails to display but when there are none, it moves up my twitter script too. I would like to set a minimum height for the gmail checker script.

Here is an example when there are messages to display and its how i like it.
[IMG]http://i.imgur.com/o31kw.jpg[/IMG]

And here is what i dont like it when there are no emails to be displayed

[IMG]http://i.imgur.com/dgg3z.jpg[/IMG]

---

### Post by Brandon Williams on 2010-08-31
I see two possibilities that might work.

1. run two instances of conky: 1 to display your twitter feeds and one for everything else. This would allow you to ensure that twitter always shows up exactly where you want it.

2. modify your mail checker script so that it always outputs the same number of lines. if you don't have e-mail to display, output blank lines to get up to the total number you want.

---

