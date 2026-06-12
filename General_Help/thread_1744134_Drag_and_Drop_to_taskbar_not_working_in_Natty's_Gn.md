---
title: "Drag and Drop to taskbar not working in Natty's Gnome Classic"
date: 2011-04-30
forum: General Help
---

### Post by inameiname on 2011-04-30
Using the non-default desktop environment of Natty that just came out a few days ago, I noticed I am unable to drag and drop items from one folder to, say, another, or even a terminal window, by dragging and dropping it to the taskbar.

In all other previous versions of Ubuntu, when I want to copy/move an item in such a way, I would drag it to the appropriate window, such as a terminal window or another folder, and then on the highlight, it opens into that folder/window. Unfortunately, that is not the case here.

My guess is it is because Unity is the default and by changing things with that, it screwed the classic stuff.

Anybody know how I can fix this?

---

### Post by bdarb on 2011-04-30
seems to be an issue with compiz, if you login to ubuntu classic with no effects it works fine.

---

### Post by inameiname on 2011-04-30
Ah I see. 

So I guess if that is the case, I must choose to have this feature, or not have desktop effects. That sucks. I really like the magic lamp effect. :(

Thanks for the info.

---

### Post by inameiname on 2011-05-04
Bump. This issue is still occurring; I miss dragging and dropping from one folder to another on the taskbar.



UPDATE:

I figured out that if you type in the terminal the following, this gets fixed. I do not know what it does not do it at default, or why you have to in the first place. My guess is because the old desktop and compiz is set to Unity. 

compiz --replace & exit

Seems to work thus far, but every time you restart or log out and log back in, it is needed once again. I guess if added in a script in startup applications it will work every time the computer logs in. I will have to try that.

---

### Post by manishk on 2011-05-21
Thanks inameiname!! I was facing the same problem, your fix works fine for me too.:)

---

### Post by inameiname on 2011-05-21
No problem.

It has remained one of the few fixes for this issue I have found. 

For me, though, I found logging in under: Ubuntu Classic (No Effects) also fixes the problem, and also fixes a couple other things I was having too, such as having a silvery default theme pop up from time to time and/or an entire computer/screen freeze. Again, not a great solution, but it works.

---

### Post by inameiname on 2011-05-27
Aside from using Ubuntu Classic (No Effects), I think I may have found the culprit that if 'fixed', will allow you to once again use Ubuntu Classic like in Maverick.

The 'fix' is to downgrade Compiz, as per these instructions. I have done this some hours ago and have restarted, and this issue does not come up. Further test will be needed, but it seems Compiz was to blame all along. Very buggy in general I hear.

[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html#disqus_thread](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html#disqus_thread)

---

### Post by inameiname on 2011-06-18
The fix to downgrade Compiz seems to have fixed things for me. 


Ill mark this as solved, even though its not really a fix, but a workaround. Whatever.

---

