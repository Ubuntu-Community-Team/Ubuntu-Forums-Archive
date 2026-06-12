---
title: "Update Information?"
date: 2012-06-27
forum: General Help
---

### Post by asdk on 2012-06-27
I have a red triangle with an exclamation mark in the middle, as an icon near the mail, then wifi, then sound (here's a picture because I'm really bad at describing it:
[IMG]http://i50.tinypic.com/1zquk94.jpg[/IMG])

When I click on it, it says:

The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by clicking this icon then selecting 'Check for updates' and check if some of the repositories fail.

I followed it, and clicked 'Check' in Software Manager. I got an error about my internet connection which I doubt is the problem. Here is the error it showed:

W:Failed to fetch [http://le-web.org/repository/dists/stable/main/binary-i386/Packages](http://le-web.org/repository/dists/stable/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Can anyone help me out here?

---

### Post by wildmanne39 on 2012-06-28
Hi, run:
```
gksu software-properties-gtk
```
in a terminal, uncheck the appropriate boxes under the 'Other Software' tab. Close the program when you're done, and it should prompt you to reload the sources lists do that and it should work.
Thanks

---

