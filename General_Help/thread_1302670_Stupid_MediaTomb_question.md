---
title: "Stupid MediaTomb question"
date: 2009-10-27
forum: General Help
---

### Post by blazemore on 2009-10-27
I've just installed MediaTomb on my server, and it's running. The webUI works and Windows 7 sees the network share.

But how do I actually add my media to it?!

---

### Post by Giblet5 on 2009-10-27
I found that the scan directory options for config.xml just plain Did Not Work as advertised. So, I changed the DAEMON_ARGS variable in /etc/init.d/mediatomb to provide a "-a /path_to_media" argument.

Ugly but it works.

Now my PS3 sees all of the music, videos, and images on my server. And that was the goal.

---

### Post by blazemore on 2009-10-27
Sorry, what?

---

### Post by Giblet5 on 2009-10-27
> **blazemore said:**
> Sorry, what?

Did you configure mediatomb after you installed it?

You will remember whether you did that or not.

Mediatomb is not *anyone's* idea of a polished application... It requires that you edit an XML configuration file (/etc/mediatomb/config.xml), install a bunch of tools to perform media transcoding (so that your target systems can use the media), write shell scripts, and spend hours scratching your head when only half of your media works correctly.

(not an exaggeration)

---

### Post by blazemore on 2009-10-27
Oh. I seem to remember a Linux Format article about MediaTomb, maybe I'll dig that out. If I find it, I'll type it up and make a Howto!

---

### Post by Giblet5 on 2009-10-27
> **blazemore said:**
> Oh. I seem to remember a Linux Format article about MediaTomb, maybe I'll dig that out. If I find it, I'll type it up and make a Howto!

That would be spectacular. Mediatomb is the only game in town and it's not ready for mainstream...

---

### Post by buntunoob on 2009-10-28
Adding the Folders is Ezy as can be from Firefox.
with the webbrowser opened up to your server    [http://yourmediatomb](http://yourmediatomb) ip:49152
On the left side youll see     
 
Database          |         Filesystem
 
 
click on filesystem, from there your file system will open up.
within the filesystem click on a folder that you want to add, then to the Right youll see a "+"  (cilck on that), now that folder is added to the DB and your kinda done, If your like me and keep adding files to that folder then you can set it to timed scan of that folder or Inotify(adds files when you put it in the folder), if you add folders to the folders that are being Scanned they wont be added automaticly unless you set Recursive.

---

