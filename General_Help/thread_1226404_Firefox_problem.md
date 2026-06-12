---
title: "Firefox problem"
date: 2009-07-29
forum: General Help
---

### Post by lorenz_b on 2009-07-29
Hi all,

I ran into a problem with firefox. I ran firefox via "sudo firefox" to check something. However, after closing and restarting firefox again normally, I observed severe problems. One thing is, that the booksmarks are not loading into firefox, although the right profile is chosen. Furthermore I could not copy my profile and try to use it as a new profile - same issues. Another thing is, that when surfing, I cannot press buttons, like a login or search button within an internet page. It also showed, that some plug-ins (maybe even all) didnt work at all, e.g. I tried to sync my bookmarks with Xmarks.
Ideas are highly appreciated!
cheers,
Lorenz

---

### Post by HappyFeet on 2009-07-29
Although the following will delete any personal settings in firefox, I believe it will work. Close firefox. Go to home folder and do Ctrl-H. That will show you the hidden directories. Delete the .mozilla folder. Then start firefox. A new .mozilla folder will be created with default settings.

---

### Post by michy99 on 2009-07-29
If you haven't deleted the .mozilla folder yet, you just need to chown it back to your username.```
sudo chown -R username ~/.mozilla
```where username is your username.

If you ever need to run firefox as root, use```
gksudo firefox
```

---

### Post by philinux on 2009-07-29
> **HappyFeet said:**
> Although the following will delete any personal settings in firefox, I believe it will work. Close firefox. Go to home folder and do Ctrl-H. That will show you the hidden directories. Delete the .mozilla folder. Then start firefox. A new .mozilla folder will be created with default settings.

That would loose him his bookmarks. Best to advise to back them up first. Or just rename .mozilla rather than delete it. :D

---

### Post by lorenz_b on 2009-07-29
Thank you very much.
I tried HappyFeets suggestion and deleted the .mozilla folder. Then I restored my yxz.default profile folder. Worked great.
@michy99: sorry, didnt see your reply in time. why is sudo firefox changing the folder properties?

thanks,
Lorenz

---

### Post by philinux on 2009-07-29
sudo and gksu

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by michy99 on 2009-07-29
This link explains it better than I can:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by lorenz_b on 2009-07-29
Thank you very much!

---

### Post by HappyFeet on 2009-07-29
> **lorenz_b said:**
> Thank you very much.
I tried HappyFeets suggestion and deleted the .mozilla folder. Then I restored my yxz.default profile folder. Worked great.
@michy99: sorry, didnt see your reply in time. why is sudo firefox changing the folder properties?

thanks,
Lorenz
Glad to hear it worked. My solutions are not always elegant, but usually work. I go by the K.I.S.S. method.
> **philinux said:**
> That would loose him his bookmarks. Best to advise to back them up first. Or just rename .mozilla rather than delete it. :D
I warned him ahead of time that he would lose any personal settings, but you are right in a way, and should have the person backup first. I will remember to do so in the future. And btw, it's **lose** not **loose**.  ;)

---

