---
title: "Cannot open text from .htm with openoffice"
date: 2009-12-05
forum: General Help
---

### Post by Tryfon on 2009-12-05
Hi,

I am trying to open a text from a website in OpenOffice but it doesn't work. I am selecting File->Open.. then pasting the following URL [http://www.inclusivedemocracy.org/fotopoulos/greek/grE/gre2009/5_12_PRINTABLE.html]("http://www.inclusivedemocracy.org/fotopoulos/greek/grE/gre2009/5_12_PRINTABLE.html") and afterwards I click Open but nothing happens. No response at all.

Same thing in Abiword.

In MS Office it works just fine.

Any ideas?

---

### Post by Meskarune on 2009-12-05
um...

open a browser. in the menu's click on "view source"

copy paste source into a text editor, I would recommend NOT using open office. Try leafpad or emacs or something...

---

### Post by Tryfon on 2009-12-05
Ok, maybe I wasn't clear enough.
The text I am trying to import is enriched. It has references and everything. Check out the link. I want to import it in OpenOffice to do some editing.

Anyway, the fact remains that both OpenOffice and Abiword fail to perform a simple function, which is supposedly supported by both of them and I wonder why and your suggestion, while useful, is not a solution. 

It looks like a bug related to Ununtu ant GTK+ to me, because even with leafpad same thing happens exactly.

---

### Post by Tryfon on 2009-12-07
bumb!

---

### Post by Tryfon on 2009-12-16
bumb!

---

### Post by ean5533 on 2009-12-16
> **Tryfon said:**
> It looks like a bug related to Ununtu ant GTK+ to me, because even with leafpad same thing happens exactly.

I agree, this appears to be a bug or unsupported feature related to Ubuntu. I am able to open that link with OpenOffice on Windows with no problem. I'm not sure if the same feature is supported on Ubuntu or not, and I'm not near an Ubuntu computer to try it out, but I'm willing to believe that it doesn't work.

I'll see if I can find out anything about opening rich text documents on Ubuntu and get back to you.

---

### Post by Tryfon on 2009-12-16
It is definitely a bug, because even when you try to open a web link which shows at a simple .doc file it doesn't work. 
Try it out yourselfs please to verify it. I want to know if I am the only one who experiences the problem.

By the way: Could it be perhaps a matter of configuration? Maybe it is set this way for security reasons. (Though I consider this highly unlikely.)

---

### Post by ean5533 on 2009-12-16
> **Tryfon said:**
> It is definitely a bug, because even when you try to open a web link which shows at a simple .doc file it doesn't work. 
Try it out yourselfs please to verify it. I want to know if I am the only one who experiences the problem.

By the way: Could it be perhaps a matter of configuration? Maybe it is set this way for security reasons. (Though I consider this highly unlikely.)
I couldn't find much about the subject. It looks to me like the issue isn't with OpenOffice, but with the different way Ubuntu handles opening files. The Windows open file dialog can handle an HTTP URL and open a remote file; the Ubuntu file choose cannot, as far as I can tell (unless someone wants to correct me on this).

A work around for this would be to save the web somewhere locally and open it with OpenOffice from there, or just select the entire page and paste it into OpenOffice directly -- both methods give me the same result.

---

