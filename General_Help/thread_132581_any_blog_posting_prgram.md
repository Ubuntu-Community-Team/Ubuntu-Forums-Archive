---
title: "any blog posting prgram?"
date: 2006-02-18
forum: General Help
---

### Post by tikal26 on 2006-02-18
Hey:
i am astarting a blogg, and have tried flokc and love the way in which I can post to my blocg, but now I want to know if  there is something similar for konqueror or for kde in general. I know there is a del.isui.us bar for konqueror so maybe there is bar for wordpress blogs. And also a flickr one would be nice.
tanks for your replies

---

### Post by Vogateer on 2006-02-18
Well, if you're using KDE, you might try kblogger, though I doubt that's part of the Ubuntu package system, and you'll have to download kblogger from [kde-apps.org]("http://www.kde-apps.org/content/show.php?content=29552"),  then untar it, and follow the instructions to build it from source.  Then you'd have to add it to kicker.  Then you just click on the button and use it to post.

If you don't like building programs from source, you may be able to set it up so that wordpress will appear in the sidebar of your browser, though I can't seem to find the link on my WordPress 2.0 site, like it was on my WordPress 1.5 site.

Well, here's something you can try, add a sidebar web module to konqueror. Take whatever your url for your blog is and add "wp-admin/sidebar.php" to the end of it, and you should be able to use this for the sidebar URL.  So the URL will read like this:

```
http://[your blog url here]/wp-admin/sidebar.php
```

Get your sidebar visible in Konqueror, usually by hitting F9, Right click on a blank area of the sidebar, choose "Add New -> Web Sidebar Module.  On mine, a little netscape icon appears.  Right click on that icon, select "Set URL", and put in the URL I mentioned above.  That should make a web log post a sidebar click away during a konqueror session.  Other than that, I'm not sure what other programs exist for kde as of yet.

Hope this was helpful.

---

### Post by tikal26 on 2006-02-18
vogateer- thanks for you help I did not know that I could do that. How did you learn that? I feel that for the most part konqueror can serve my need is just that I don't know how to use it to its maximum potential. It is not as flexible and nice as flock, bt for the most part is good enough for me
again thanks

---

### Post by Vogateer on 2006-02-18
No problem tikal26, and I'm glad to help someone out.  Konqueror is just an amazing program, and if you're new to it, you should google around for some howtos and questions so you can learn more about it.  It can actually do a lot of stuff that Firefox can, but it's already built into the program and you have to do some searching to look around for it.  The sidebar has amaroK, bookmark, and del.icio.us integration, and you can use mouse gestures, which is a setting you can find in the Control Center, depending on which KDE version you have.  Mouse gestures is one of those things everyone should be using.  It's just a faster way to browse than anything else, save maybe keyboard shortcuts, and that's a pretty close race.

Some of the stuff it does is just amazing.  Fore file management it's simply the best in my opinion.  If you have several computers, or are transfering files across the net, then I think there is no easier way of transfering files than using the fish:// kioslave, you can browse and act upon programs pretty much like they're local files, and the same goes for ftp sites.  You can add several things to the right click menu with simple dcop type scripts.  Like I said try to google for konqueror howtos, and see what you can find, you'll probably find something you didn't know about it every day you look.

I often times use firefox, because it's a great browser as well and has the web developer extension which is fantastic for trying to get your website standards compliant, but Konqueror loads so much faster and its integration with programs like Akregator for RSS feeds is great, so that if you're using KDE, I really recommend using Konqueror and getting used to it.  It's worth it.

---

### Post by Vogateer on 2006-02-18
Sorry, I forgot to say how I learned that.  In WordPress 1.5 there was some type of link that led you to that bookmark, and it was a lot easier then.  I had to fiddle with it a bit to learn how to add it in WordPress 2.0, but since I already had the sidebar in Konqueror from the last time, I just right clicked and figured out how it was done.  With just about everything in KDE, when in doubt, right click.

---

### Post by www-empty on 2006-11-28
I think kblogger is included with kubuntu. I installed it as an applet. If you do use it, use the metablog API and the url has to include xmlrpc.php at the end.
Cool konquerer side panel solution, Vogateer.

---

