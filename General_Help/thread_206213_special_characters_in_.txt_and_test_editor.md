---
title: "special characters in .txt and test editor"
date: 2006-06-29
forum: General Help
---

### Post by evaristegalois on 2006-06-29
I type 

würde oder wäre sind zwei Füße des österreichischen Konjunktivs

save it as a file and then email the file as message body to myself to get

wÃ¼rde oder wÃ¤re sind zwei FÃ¼Ã&#376;e des Ã¶sterreichischen Konjunktivs

What happened to my beautiful German umlauts?

--evaristegalois

---

### Post by mlind on 2006-06-29
Does the text on look okay after you save it and re-open it using your editor?

Also, I'm not sure, but if messages are inlined on the body of the mail, mail client
could change the content type to something else.. Not sure though.

---

### Post by evaristegalois on 2006-06-30
the text looks fine in the editor (which is emacs, btw) I suspect that emacs encodes the text differently than the shell. there are different international encoding standards (iso, mule etc.) if anybody knows how to mess with those pls let me know

--evaristegalois

---

### Post by evaristegalois on 2006-07-29
As I edit my texts in emacs, I have a solution for the problem there. I highlight the whole text (C-x h) and then run the command M-x encode-coding-system with iso-latin-1

Then the file shows up with all the right umlauts.

--evaristegalois

---

