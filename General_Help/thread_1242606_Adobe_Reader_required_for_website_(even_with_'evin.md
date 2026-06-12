---
title: "Adobe Reader required for website (even with 'evince' &amp; 'mozplugger')"
date: 2009-08-17
forum: General Help
---

### Post by altonbr on 2009-08-17
My girlfriend is a real estate agent here and she recently asked me to switch her to Ubuntu because she was sick of viruses, etc.

I gladly obliged and installed Ubuntu 9.04 on her laptop, plus all sorts of PPAs, themes, medibuntu, etc.

She has two websites which seem to only work with an IE6+/Windows mix and it has really annoyed both her and I. Recently, foruntately, one of the websites is fixable.

The problem is the one website pops up with a file called loadForm.php instead of the PDF she requested. Since I'm a web developer, I was actually able to read the PHP code and noticed that the website was rendering the PDF on-the-fly.

I was also able to talk to the developer of the website and he said the entire site should work in Ubuntu (although he's never tried) because it uses purely open-source technoliges.

So I poked my head around and noticed that only Adobe Reader can read the file on his website, but when it's not installed, evince (the GNOME PDF viewer) fails to open the document (resulting in the loadForm.php file).

So I'm wondering what I need to do to get it to work in Ubunt without install 'acroread' from the partner repositories.

I looked through Edit > Preferences > Applications and everything seemed to be set up for Evince to be the default PDF viewer...

So what am I missing? Is this evince not setting the proper headers (e.g. application/pdf) in Firefox or the other way around?

---

### Post by mcduck on 2009-08-17
Are you trying to open the PDF directly, or save it to your computer and *then* open it?

Any change of getting a link to one of the sites so we could try?

(in the end, if everything else fails Acrobat Reader is available for Linux as well, but it's pretty much the heaviest, slowest and most buggy PDF reader available so I'd stay away from it by any means possible.. ;))

---

### Post by harry2006 on 2009-08-17
i'ld suggest installing acroread to confirm that we've certain issues with evince not able to open those pdfs in that website...
have you tried opening some other pdfs sitting right on your disk and make sure it opens with evince by default?

---

### Post by jtmedin on 2009-08-28
Well i tried evince & was unable to do a search on the document. So got acroreader & found the same problem. Went to edit & clicked on find then entered ctcss not found. Looked @ the document & i can see it. So what am i doing wrong?

---

