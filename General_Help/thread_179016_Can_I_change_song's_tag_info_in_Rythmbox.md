---
title: "Can I change song's tag info in Rythmbox?"
date: 2006-05-18
forum: General Help
---

### Post by LsrLine on 2006-05-18
Can I change song's tag info in Rhythmbox?  If so how?

---

### Post by Dr. Nick on 2006-05-18
nope, try easytag its in the repos

---

### Post by LsrLine on 2006-05-18
[QUOTE=Dr. Nick]nope, try easytag its in the repos[/QUOTE]

I just found this on the Rhythmbox faq.  How would I do this:

Why will preferences not let me edit my song tag info?

    Some mp3s are not detected properly by GStreamer. Rhythmbox supports id3 tag editing as an experimental feature. This is a feature that will be supported at some point in the future. Use the --enable-tag-writing flag to configure to enable it, at your own risk obviously.

---

### Post by Dr. Nick on 2006-05-18
[quote=LsrLine]I just found this on the Rhythmbox faq.  How would I do this:

Why will preferences not let me edit my song tag info?

    Some mp3s are not detected properly by GStreamer. Rhythmbox supports id3 tag editing as an experimental feature. This is a feature that will be supported at some point in the future. Use the --enable-tag-writing flag to configure to enable it, at your own risk obviously.[/quote] 
to do that you will have to go to rhythmbox site and download the source code to manually compile it with that option enabled. It appears that the ubuntu packaged version doesnt have that enabled since its not fully supported yet.

My prefrences windows wont let me change it either and i am using the newest version available.

You could compile it yourself but using another program may be easier

---

