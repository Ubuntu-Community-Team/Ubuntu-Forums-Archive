---
title: "hidden files &amp; backup files"
date: 2012-09-25
forum: General Help
---

### Post by clockworktri on 2012-09-25
I can't find info on this anywhere, but I could swear that when I used to view hidden files in nautilus, what showed up were only the ".name" ones (this would have been back in 10.04). But now it also shows all the backup "name~" files as well. There are loads of these automatically generated, and it's very frustrating to have to wade through them in order to work in my hidden folders. 

I have been googling all over the place, but I can't find anyone mentioning this. Is there any way that I can view only the ".name" files and not the "name~" ones?

---

### Post by HiImTye on 2012-09-26
nautilus shows all files, including regular files when showing hidden files. the reason those backup files appear, is because they are also hidden files (they begin with a '.'). you can use the search function (top right corner) to filter content

I always prefer the command line for displaying and filtering information, since it's much more powerful

---

### Post by clockworktri on 2012-09-30
So, turns out these issue was not based in nautilus, but in gedit, which was automatically creating backup files. I stopped them from being created in the first place by un-checking the box for "create a backup copy of files before saving" in gedit preferences. Then I just went through and deleted the ones that had already been created. (Thought I'd explain it in case anyone else went off looking in the wrong direction, like I did.)

BTW, these are not files with a period in front of them. They are backup files (as opposed to just hidden files) which are designated with a tilde (~) at the end, not the period (.) at the beginning.

---

