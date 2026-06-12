---
title: "Where is the best place to put shared files like images?"
date: 2006-03-10
forum: General Help
---

### Post by s|k on 2006-03-10
My wife and I both use Ubuntu on the same computer, we have different user accounts set up. We both want to access our pictures from our own account. Where is the best place to put these pictures?

Also what are some good picture organizers?

Thanks.

---

### Post by Zelut on 2006-03-10
You want to be able to access each others pictures from either account?  You might want to setup a seperate folder in /home called /public or /shared (or whatever) and set permissions to 777 (chmod 777 <folder>).  This will grant full read, write & execute access to everyone using that machine to that folder.

...again, I'm assuming that is what you're looking for.  Let me know otherwise.

---

### Post by hw-tph on 2006-03-10
/usr/local/share, /usr/local/media, etc is what I use. Create a group that should have access to the shared files, and add the users to that group. Change ownership of the directory that should be shared to that group (root:whatever) and set the sticky group bit.

Let's say the name of the group is "media" and the directory is /usr/local/media:
[b]chown root:media /usr/local/media
chmod g+rw /usr/local/media
chmod g+s /usr/local/media[/b]


Håkan


Håkan

---

