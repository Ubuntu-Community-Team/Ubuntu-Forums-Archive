---
title: "&quot;compress&quot; doesn't compress (Ubuntu 10.04)"
date: 2012-05-12
forum: General Help
---

### Post by shelbyvision on 2012-05-12
When I select a bunch of image files to put in a zip file, and click "Compress", it lets me make the zip file, but it doesn't do any compressing. The zip file is exactly the same size as the collection of image files. In the past, with windows, when I made a zip file, there was a significant difference in size. There were also controls for amount of compression, etc. Ubuntu's compression has no options at all. Is there something I'm missing?

---

### Post by insane_alien on 2012-05-12
are you trying to compress .jpg's .png's or other already heavily compressed images? if so then thats your problem. you can't just keep adding layers of compression as files will only get so small before they can't get any smaller.

if its bitmaps on the other hand, then you might have a problem as these should be highly compressible.

I do agree that the compress option has too few options though.

---

### Post by shelbyvision on 2012-05-12
Yes it's jpg's, but they were saved at 100%, so I thought that would leave a lot of room for further compression.

---

### Post by SeijiSensei on 2012-05-12
You can try a different compression algorithm like this:

```
gzip filename
```

That will create a file called filename.gz.  To unpack it, use "gunzip filename.gz".  However I'd agree that you shouldn't expect much improvement if you're trying to compress images.

---

### Post by flemur13013 on 2012-05-12
They're correct that .jpg files shouldn't compress much, if at all, in zip or rar files, regardless of the original compression settings on the image file; the latter is more a measure of image quality rather than of compression.

---

### Post by insane_alien on 2012-05-12
> **shelbyvision said:**
> Yes it's jpg's, but they were saved at 100%, so I thought that would leave a lot of room for further compression.

jpeg is a lossy compression algorithm. I'll strip out information based on that 100% setting then essentially zip what's left to make the smallest file possible. The % quality really just determines how much data gets permanently lost.

---

### Post by shelbyvision on 2012-05-12
Hmmmm, I guess I just remember wrong. It has been a few years since I had Windows. It makes me wonder why some people insist on uploading a zip file instead of individual image files.

---

