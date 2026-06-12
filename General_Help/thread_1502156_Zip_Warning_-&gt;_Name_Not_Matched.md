---
title: "Zip Warning -&gt; Name Not Matched ?"
date: 2010-06-05
forum: General Help
---

### Post by jv2112 on 2010-06-05
I am trying to zip up my Home directory (zip -r -9 /Destination /home/joe) & when I do I get the error below in a constant loop until I hit ctrl-c to stop. 

This use to work fine. The only change I made lately was change the permissions to 700 but I don't see how this would do anything.

Any thoughts ? :confused:

> 
zip warning: name not matched: /home/joe/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/drive_c/users/joe/My Documents/.wine/dosdevices/z:/usr/lib32/libxslt.so


---

### Post by saiganeshb on 2011-05-27
Apparently, the zip program doesn't support archiving files larger than 2 gb. ( Check this out: [http://wiki.linuxquestions.org/wiki/Zip](http://wiki.linuxquestions.org/wiki/Zip) ) .

What i suggest:
You can probably use something else like tar / winrar ( from wine ) ,etc.

---

### Post by PFudd on 2012-09-21
Initially I thought I had the same problem as you, but it turns out I only had the same error message.

In my case, all of the files generating the error were in fact symbolic links pointing outside the directory I was zipping.

In your case, it looks like zip is following a symbolic link in an infinite loop, as /home/joe/.wine/drive_c/ is a link to your root directory.  When the filename gets to be too long, zip dies with an incorrect (well, uninformative) error message.

---

### Post by overdrank on 2012-09-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

