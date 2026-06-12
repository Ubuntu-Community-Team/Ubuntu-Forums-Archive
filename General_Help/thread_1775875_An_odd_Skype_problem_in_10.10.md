---
title: "An odd Skype problem in 10.10"
date: 2011-06-05
forum: General Help
---

### Post by kmarzi on 2011-06-05
Hi all,

This is a very strange one: my Skype no longer starts since installing various updates for 10.10. I've uninstalled it, reinstalled it, tried fixes, everything.

This fix seem to be the most efficacious, looking at various websites:[I] 

"press Ctrl+H and find the directory .Skype. Inside that one you should  delete the file called shared.xml by right-clicking on it and select  'move to trash;"[/I]

However, the skype directory simply isn't there in my home folder. It's odd, because Skype is definitely installed (e.g., when I uninstall, the Skype logo disappears in, say, Apps>Internet, and in my systray. Then I reinstall and, like I can see now, the Skype logos are visible).

Any ideas how I can fix this? I've uninstalled and reinstalled Skype 2 or 3 times now: but the .skype folder isn't there! (I have displayed "hidden folders" too, so it definitely isn't that). I've installed with the software centre and in terminal. Hmmmm....

Any help would be great.

Thanks.
Kmarzi

---

### Post by IWantFroyo on 2011-06-05
What do you get if you just open a terminal and type:
```
skype
```

---

### Post by kmarzi on 2011-06-05
> **IWantFroyo said:**
> What do you get if you just open a terminal and type:
```
skype
```

I get this:

skype: symbol lookup error: /usr/lib/libQtDBus.so.4: undefined symbol: _ZN14QObjectPrivate15checkWindowRoleEv

---

### Post by timgood on 2011-06-05
Try ```
rm -rf /home/yourusername/.Skype
``` (note that .Skype has a dot before it and a capital S and that you should replace yourusername with your user name) and then re-start Skype. What happens?

---

### Post by kmarzi on 2011-06-05
> **timgood said:**
> Try ```
rm -rf /home/yourusername/.Skype
``` (note that .Skype has a dot before it and a capital S and that you should replace yourusername with your user name) and then re-start Skype. What happens?

Skype still won't start...

---

### Post by kmarzi on 2011-06-05
I've also noticed that VLC won't start either (and there's also no .VLC directory in my home folder - I'm not sure if it should actually be there too?). I'm not sure if it's linked but thought I'd post it here anyway.

---

### Post by timgood on 2011-06-05
Take a look at [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/115970](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/115970) which may throw some light on the problem. Have you installed anything (like Google Earth for example) which may have placed qt4 libraries in /usr/local/lib ? These may conflict with libraries installed in the correct place /usr/lib and removing the /usr/local/lib versions seems to help in some cases (afterwards run ldconfig). But read through the entire thread first!

---

### Post by kmarzi on 2011-06-05
> **timgood said:**
> Take a look at [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/115970](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/115970) which may throw some light on the problem. Have you installed anything (like Google Earth for example) which may have placed qt4 libraries in /usr/local/lib ? These may conflict with libraries installed in the correct place /usr/lib and removing the /usr/local/lib versions seems to help in some cases (afterwards run ldconfig). But read through the entire thread first!

Thanks for that. I did actually install GoogleEarth today, so I wonder if that is the problem? I've read the link you sent. Now, I'm hardly a complete noob, but I think that 90% of whatever is written in that Bug report makes no sense to me at all. 

Any ideas what I should do? Uninstall GoogleEarth (which I really need)? 

Your help is really appreciated :)

---

### Post by kmarzi on 2011-06-05
Ok, I uninstalled  GoogleEarth via Synaptic Package Manager and  Skype now works. So does VLC. Thanks a million for your help, I really appreciate it. I think I will try to install GoogleEarth via the Software Centre, rather than via Google's website, and see if Skype, VLC, etc., still work.

Kmarzi

---

### Post by kmarzi on 2011-06-05
I have re-installed Google Earth using the instructions on this website: [http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/)

Now, Skype, VLC and Google Earth all work :D

---

### Post by dFlyer on 2011-06-05
Last week there was several threads of Skype no working. You may want to search the archives here. As for myself, I have not had any of these problems. I use skype daily.

---

