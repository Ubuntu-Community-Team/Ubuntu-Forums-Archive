---
title: "File Sharing?"
date: 2010-01-31
forum: General Help
---

### Post by sethhikari on 2010-01-31
I need to be able to share a file and have it accessible by my ip via the web browser. This file will be local.

Is there a great program for this or will I have to setup some kind of server my self? Thx

---

### Post by hawthornso23 on 2010-01-31
> **sethhikari said:**
> I need to be able to share a file and have it accessible by another computer via the web browser. This file will be local.

Is there a great program for this or will I have to setup some kind of server my self? Thx

If you install samba you could create a shared folder and access the files in it from another computer on the local network. In particular you could open them using firefox in the same way that you can open any file stored locally using firefox.

This would only work across your lan.

---

### Post by sethhikari on 2010-01-31
Really I am trying to access files on my comp from my iPod's browser. I have Samba

---

### Post by hawthornso23 on 2010-01-31
> **sethhikari said:**
> Really I am trying to access files on my comp from my iPod's browser. I have Samba

I wouldn't call an Ipod "another computer". I don't think you can have an ipod on your lan for example. They don't file share the same way a computer does. I don't have an ipod and know little about them. You need someone who knows about ipod networking to answer this question. Try changing the title of the thread so it has the word "ipod" in it. That way you'll have a better chance of attracting the interest of someone who knows something about them.

---

### Post by hawthornso23 on 2010-01-31
Interesting - the article heading changed but the thread heading did not. I didn't know the forum worked like that.

Maybe you should just start another thread.
****

---

### Post by 3rdalbum on 2010-01-31
You need to install some kind of web server, such as Apache. When that is done, you put the file you want to share into the /var/www folder.

On your router (assuming you have one), forward port 80 to your computer's internal IP address (the one that is reported by Network Manager) and people outside your network will be able to access your Apache server.

Now, all you have to do to access your file is to type your external IP address into the web browser, preceeded by "http://".

---

