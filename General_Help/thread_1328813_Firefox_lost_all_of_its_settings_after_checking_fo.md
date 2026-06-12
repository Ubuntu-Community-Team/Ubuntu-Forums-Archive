---
title: "Firefox lost all of its settings after checking for updates as root"
date: 2009-11-16
forum: General Help
---

### Post by Guyon on 2009-11-16
The other day I ran sudo FireFox in terminal and checked for updates to see that there weren't any. When I opened Firefox again all oh my bookmarks/history are gone and some extensions don't keep me signed in. My home page won't go to the page I set it to and when I type something in the url box, it will go to that place but what is in url box never changes (even when switching tabs). Back/Forward/Refresh/Stop don't work either.

I am completely clueless on how to fix this. I went to /etc/firefox-3.0/profile and deleted localstore.rdf (I saw this worked for somebody else here: [http://forums.mozillazine.org/viewtopic.php?f=38&t=371059&start=0&sid=497c857a0110cf2bc97c0e168d959ec1](http://forums.mozillazine.org/viewtopic.php?f=38&t=371059&start=0&sid=497c857a0110cf2bc97c0e168d959ec1))

Any help would be *greatly* appreciated. :D

---

### Post by phillw on 2009-11-16
You may have messed up your permissions in your ~home folder.

```
ls -al .moz*
```

should show things as owned by you. 

Phill.

---

### Post by oldfred on 2009-11-16
You may have created a new profile and your old one is now not the default.

./firefox -profilemanager
[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

---

### Post by phillw on 2009-11-16
If you head over to lovinglinux's FF section over here --> [http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

There are various troubleshooting guides, plus he does a really good job of supporting stuff.

> **[COLOR=#990000]Note:[/COLOR]** Please DO NOT use *sudo firefox*. If you really need to run Firefox with administrative rights for whatever reasons, then use *gksudo firefox* instead. When you use gksudo it's starts Firefox with administrative rights, but uses the root Firefox profiles, while *sudo* uses the user profiles, thus messing with the permission and preventing regular users from loading their profiles correctly

Is the area you need to be in, under trouble-shooting

Phill.

---

### Post by Guyon on 2009-11-16
> **oldfred said:**
> You may have created a new profile and your old one is now not the default.

./firefox -profilemanager
[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)

Worked perfectly, thank you SO MUCH! And thanks for the tip phillw, I'll remember that.

---

### Post by Guyon on 2009-11-16
On second thought, that *sort-of* worked. I can get back to my original settings, but only though opening Firefox with firefox -profilemanager. When opening it normally it still starts broken.

/bump

@aysiu - Thanks, this works perfectly now!

---

### Post by Guyon on 2009-11-16
Bump

---

### Post by aysiu on 2009-11-16
Close Firefox completely, and then paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R guyon:guyon /home/guyon/.mozilla
``` Substitute in your actual username if *guyon* isn't it.

Then **never** use *sudo firefox* again.

More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

