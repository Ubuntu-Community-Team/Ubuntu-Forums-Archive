---
title: "Changing paths/ links"
date: 2010-06-28
forum: General Help
---

### Post by Archeleus on 2010-06-28
This is my first time posting in this forum so hello to all of you.

Anyway I just installed the LAMP package for debian linux and well, as you all know, you can't modify contents of the root folders without super user privileges which means you can't edit it using file manager.

I'm using eclipse IDE for PHP development and the pages created are being stored in my workspace.

How can I link it from there to the /var/www folder without actually copying using su cp everytime I modify it?

Cheers

---

### Post by Smart Viking on 2010-06-28
I don't know the answer to your question, but you can use the file manager as superuser in ubuntu, with this command:

```
gksudo natutilus
```

Where "nautilus" is the command for the file manager, in xubuntu it would be 

```
gksudo thunar
```

Since that is the file manager xbuntu uses. :)

---

### Post by Archeleus on 2010-06-28
Nope that's not what I am looking for but thank you.

---

### Post by Javich on 2010-06-28
Did you tried:

```
cd /var/www
sudo ln -s /home/yourusername/workspace_php workspace
```

?
That should do it

---

