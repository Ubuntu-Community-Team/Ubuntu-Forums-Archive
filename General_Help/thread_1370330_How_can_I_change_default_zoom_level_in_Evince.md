---
title: "How can I change default zoom level in Evince ?"
date: 2010-01-02
forum: General Help
---

### Post by 7Lj3)(P38J on 2010-01-02
Folks,

I need to change the default zoom level for Evince. There must be some way to do this. Besides, can Evince start without any PDF file loaded? 
Also, what is the command line to execute evince?

(I run Linux Mint 8 based on Koala 9.10).

Whenever it loads a file for which it assigns a zoom level more than 175% or 200%, the whole PC hangs if I click on the "reduce zoom" icon in the toolbar. This is a very big regression.

This is ridiculous!  Even ePDFViewer is better than this.

thanks in advance for your tips to solve this. I really would like to stay with Evince for the time being, and not need to move to Foxit.

best regards
Carlos Manuel
Portugal

---

### Post by kaibob on 2010-01-02
> **crolidge said:**
> Folks,

I need to change the default zoom level for Evince. There must be some way to do this. Besides, can Evince start without any PDF file loaded? 
Also, what is the command line to execute evince?

The command to open Evince is simply evince. No PDF file is loaded when you type this command. I have never found a way to set a default zoom level with Evince--instead it remembers the zoom level from session to session. Perhaps another forum member will have a way to do this.

---

### Post by 7Lj3)(P38J on 2010-01-03
Thanks for the reply, but I don't quite agree. Evince does not always remember each session settings. Otherwise I wouldn't be stuck with it. Quite frankly, I just moved to Foxit Reader 1.1, definitely way better.

I would love to stick with Gnome, but honestly can't handle these bunch of bugs any longer.

---

### Post by kaibob on 2010-01-03
> **crolidge said:**
> Thanks for the reply, but I don't quite agree. Evince does not always remember each session settings. Otherwise I wouldn't be stuck with it. Quite frankly, I just moved to Foxit Reader 1.1, definitely way better.

You are correct! 

I just created three test PDF documents and zoomed one to "fit page width" and the second to "best fit". I zoomed out the third document until it was very small in size. I then opened and closed these documents in succession without changing the zoom level. The first document was always zoomed to "fit page width"; the second document was always zoomed to "best fit"; and the third document was always zoomed to a very small size. So, the zoom level is retained for each individual document--not from session to session. 

I then created a new PDF document that had not previously been opened and found that it took on the zoom level of the last-opened PDF document. 

Anyways, I'm glad that you found an alternative to Evince that works.

---

### Post by Johnny K on 2010-07-05
I'm also a bit annoyed by this behavior. It looks like we're not the only ones to care about this, someone submitted a bug report in May 2010:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=583973](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=583973)

Has there been any progress on this issue, or should I try to add to the bug report?

---

### Post by Johnny K on 2010-07-05
Funny enough, it now seems that I can't repeat this behavior. A recent version of evince might have fixed it (i.e., the fix is 6 months away in Ubuntu land :-)).

---

