---
title: "wget downloads corrupt files; gwget doesn't work at all."
date: 2010-12-26
forum: General Help
---

### Post by mount_evans on 2010-12-26
In order to download files from a particular website, I have to include a header containing the text of a cookie, to indicate who I am and that I am properly logged in.  So the wget command ends up looking something like:

```
wget --header "Cookie: user=stringofgibbrish" http://url.domain.com/content/porn.zip

```
Now, this does work in the sense that the command does download a file of the right size that has the expected name.  But the file does not contain what it should--the .zip files cannot be unzipped, the movies can not be played, etc.  Do I need some additional option, like the "binary" mode in the old FTP protocols?

I tried installing gwget; it is easier to use, but has no way to include the --header stuff, so the downloads never happen in the first place.  So:  How do I tell wget to download binaries properly, or how do I tell gwget about the --header?

---

### Post by mikewhatever on 2010-12-26
You should probably edit the file name, you know, that stuff before the .zip.
:lolflag:

---

### Post by karthick87 on 2010-12-26
> **mikewhatever said:**
> you should probably edit the file name, you know, that stuff before the .zip.
:lolflag:

+1

---

### Post by noah++ on 2010-12-26
Yeah! It's spelled *gibberish*.

...or is that what he meant by "corrupt files"?

---

