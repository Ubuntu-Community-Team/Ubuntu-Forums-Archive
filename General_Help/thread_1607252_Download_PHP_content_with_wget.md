---
title: "Download PHP content with wget"
date: 2010-10-27
forum: General Help
---

### Post by ntesla123 on 2010-10-27
If I try to download video files that are php content, wget doesn't download the files. It is possible to download them by right clicking and clicking "Save File As ...".

How can I get wget to download these kinds of files? Does wget have a "Save File As ..." option? 

[]("http://website.com/members/content.php?show=file&path=/videos/93/video.wmv")

---

### Post by WorMzy on 2010-10-27
What you are trying to save with that link is the php page, not the wmv file. If you can find out what the full path of the wmv file is (presumably it'll be in the html), then you can use wget to download it that way.

btw, that link doesn't work - IIS 404 error page.

---

