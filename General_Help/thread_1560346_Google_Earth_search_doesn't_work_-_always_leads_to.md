---
title: "Google Earth search doesn't work - always leads to one place!"
date: 2010-08-24
forum: General Help
---

### Post by Svens on 2010-08-24
Hi!
I hope that you all have a good day and someone will know a fix for this. :)
I have installed Google Earth on my PC and today I wanted to test the built in search for addresses, shops and stores. But then I realized that every time I try to search for something, it leads me to the wrong place! 
Example: ( I will now try to translate the buttons on Google Earth, because it is my local language): I click on the "Fly to" button and search for "Swedbank". It gives me a list with all places that are related with "Swedbank" and when I click on any of them, Google Earth automatically takes me to that place, and all places leads to here: [http://maps.google.com/maps?ll=56,24&z=16&t=h&hl=lv](http://maps.google.com/maps?ll=56,24&z=16&t=h&hl=lv) It somewhere in the middle of my neighbour country (I live in Latvia, the place shown is in Lithuania). OK - then I try to click on the middle button on the top of the search list that says "Find bussinesses"  and search for my local school - yes, it shows me a list of schools - the first one is the right one - then I click on it and it again takes me to the same place where before - in the middle of Lithuanina and it shows that the place I am looking for is right there!
What could possibly be wrong here and do you have this kind of problem in your Google Earth?
I hope that I explained it all so that everybody could understand.
And if you have anything to say about it - please. I would appreciate any advices!
Thank you! And have a nice day! :)

---

### Post by Vaphell on 2010-08-24
out of curiosity i tested it and i didn't land in lithuania, but in the middle of nowhere in forests or at sea o.O There is always some kid of oddball offset
strange :)

edit:
[http://www.google.com/support/forum/p/earth/thread?tid=72b851d55f188cea&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=72b851d55f188cea&hl=en)
maybe this is it? helped in my case

---

### Post by Svens on 2010-08-25
Thank you for your answer!
Yes, this problem seems the same and the explanation is very logical. I could do all the things that people are trying to do in that discussion, but the only problem - they are talking about files, that doesn't exist for me. How can it be?
For example:
the script /opt/google-earth/googleearth - I don't have it. In /opt there is no "google-earth" or nothing related to it.
/etc/profile.d/lang.csh and /etc/profile.d/lang.sh - don't have them there. There I only have "speechd-user-port.sh"

So I can't do any of those workarounds. Does anybody have any suggestions? 
Thank you in advance!!

---

### Post by Svens on 2010-08-25
Still looking for answer. :)
Thank you!

---

### Post by Svens on 2010-08-25
Still looking for solution. I am not impatient, I just would not want that this post slips by someone, who could know the solution. :)
Thank you! :)

---

### Post by DeMus on 2010-08-25
I typed Swedbank and also got a couple of answers. Because most of them are in Sweden you see a lot of red icons there. But one, with me it is answer H, is in New York state. So to be able to see all of them the earth is rotated in such a way that all the answers to the quest are shown. Meaning the Atlantic Ocean is the middle of the picture. Quite normal. Double clicking an answer in the list gives you a zoomed-in detail of the result.
At least, this is how it works here for me.

---

### Post by Vaphell on 2010-08-25
```
whereis googleearth
```
or ```
locate googleearth
```

---

### Post by Svens on 2010-08-25
Yes, DeMus - that's how it should be and that's how it is, except that ALL my local places I am looking for shows in Lithuania, no matter what. If I search for my local bank - it's in the middle of Lithuania (when I double click on it), when I search for my school - what do you know - I study in middle of Lithuania, etc. :D

And YES - the solution is here!
Thanks to Vaphell!
So the reason for this to happen is > The bug is in the Qt4-4.5.2.

If LOCALE is setted to a language that uses 'comma' as decimal separator (for example, it_IT), then Qt4-4.5.2 truncates the decimal part of a real number; for example, 35,2 becomes 35
So I needed to change LOCALE, and the way it is done:
> If you have this problem, edit the script /opt/google-earth/googleearth
Search for the line: 
export LD_LIBRARY_PATH
and add hereupon:
export LC_ALL=us_US.UTF-8

Only in my case, my googleearth file wasn't there, and thanks to Vaphell again I found it - it was on usr/bin :)

Thank you for your work very much!
Problem is solved!
I just love Ubuntu Community. :)

---

