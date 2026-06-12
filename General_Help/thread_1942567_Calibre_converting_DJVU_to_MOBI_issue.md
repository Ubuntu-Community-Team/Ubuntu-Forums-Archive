---
title: "Calibre converting DJVU to MOBI issue"
date: 2012-03-17
forum: General Help
---

### Post by Q-collective on 2012-03-17
When I try to upload a DJVU ebook to my Kindle, Calibre nicely asks me if it has to automatically convert it to a MOBI file, to which I say yes. But after the conversion, the resulting MOBI file is only a few kB big and looks completely empty when opening it in either the Calibre viewer or Kindle.

This has happened now with three random DJVU files. Am I missing a library or something? Is Calibre capable of converting DJVU files at all?

I'm running Ubuntu 11.10 and Calibre 0.8.43

---

### Post by camurgo on 2012-08-17
You should have asked this on Calibre forum. This is a known issue, still without solution on Calibre, as far as I know. (Calibre can only convert .djvu files with pages comprised of embedded text, not embedded images.)

What you need to do is convert the djvu files to pdf using some other program. I recommend **DJview4**. Install it from the repositories, then open your .djvu ebooks, click on File -> Export As... -> PDF

And that's it.

---

