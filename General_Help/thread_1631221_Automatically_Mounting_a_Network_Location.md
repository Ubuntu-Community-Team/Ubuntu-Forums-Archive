---
title: "Automatically Mounting a Network Location"
date: 2010-11-26
forum: General Help
---

### Post by jpboyrox on 2010-11-26
If I can't get this sorted, I really can't use Ubuntu so pleeease help. I'm a complete newbie, as in, about 2 hours using ubuntu so far. Generally things are going well. I am trying to create a link to my windows xp workgroup where all my data is stored (I was surprised that linux could even see it!) I mounted a volume on the desktop apparently... that worked fine until I rebooted and it had disappeared. it was fairly annoying that I had to go back into the network and re-mount the volume. How can I get it to stay put, even after rebooting? 
I have limited to zero knowledge of linux/ubuntu so you may need to break it down for me.I tried using 'Storage Device Manager' as someone suggested but emmm I didn't understand a word of it. In fact there weren't many words. Only acronyms
Any help would be greatly appreciated. Thanks, a lot!

Does [http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473) help? I don't understand it at all...

---

### Post by Morbius1 on 2010-11-26
My advice is the same as your other post:
> **Morbius1 said:**
> There's the poor man's way: Connect to the  share in Nautilus and then Bookmark it ( Nautilus > Bookmarks >  Add Bookmarks )
Shows up like a mapped drive does in Windows. You'll have to click on the bookmark to actually mount it.

Then there's the Gigolo way: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

* Personal Note: After years of doing it the traditional way through  fstab I now use gigolo exclusively. It's a remarkable little utility  that will browse, mount, automount, and even wait for the remote share  to be available before it mounts.*

Then there's the traditional way.

---

### Post by jpboyrox on 2010-11-26
the 'poor man's way' didn't work at all but gigolo looks very promising. thanks a lot.
sorry about the thread repost btw haha didn't think I would get any replies. On an off-topic note, why do Ubuntu users use the 'terminal' so much when there is a GUI? not that its a bad thing, it just seems unnecessary to learn the language when you can use the gui

---

### Post by jpboyrox on 2010-11-26
gigolo's great! one more question then I'll shut up: is there a way to hide Gigolo's window on startup and automatically run it in the background (just in Ubuntu's version of the system tray)

---

### Post by Morbius1 on 2010-11-26
You didn't read my mini How To: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

> **Morbius1 said:**
> I used to use entries in fstab to automount  remote shares but then I found a remarkable little utility called  gigolo:
```
sudo apt-get install gigolo
```And just in case you already don't have it installed:
```
sudo apt-get install fuse
```It's considered a network browser but it does have the ability to automount remote shares.

The procedure is relative simple:
When you first bring it up make a change in the preferences:
[B]Edit > Preferences > Interface>
Select "Show Side Panel"[/B]
[COLOR=Blue]**Select "Start minimized in the Notification Area"**[/COLOR]
**Disable "Show auto-connect error messages"**

Then you browse to the share using the Network Tab on gigolo
Then you bookmark the share by right clicking the share icon and select **"Create Bookmark"**
When you bookmark it select the **"Auto-connect"** option

Then have gigolo start at login:
**System > Preferences > StartUp Applications > Add > Command = gigolo**

When you login it will automatically mount remote shares and you will see an icon on your desktop. 

This auto-connect function has one other feature. If the remote share  isn't available or if the connection is lost gigolo will scan the  network every 60 seconds ( user adjustable ) and mount it when it finds  it.

It will make more sense when you use it and it will take less time to implement than it took for me to try to explain it :wink:

---

### Post by jpboyrox on 2010-11-26
Sorry, really stupid of me. I read all the points I guess my eyes just skipped over it. I should have worked it out anyway. My bad.

---

### Post by Morbius1 on 2010-11-26
> On an off-topic note, why do Ubuntu users use the 'terminal' so much when there is a GUI? not that its a bad thing, it just seems unnecessary to learn the language when you can use the gui.
For the first 80% of my life with linux I was a KDE user. KDE3 was the most configurable Desktop environment known to man with little GUI applets that did everything for you. When KDE4 came out and for reasons I don't want to bring up for fear of a KDE3 vs KDE4 war I decided to move to Gnome. It's then that I realized that I really didn't know how to do anything without a GUI and Gnome either didn't have one or I couldn't find it. A terminal command is the same regardless of the desktop your running. It's faster and easier to explain in a forum than the 14 steps or so usually required to do the same thing in a GUI.

But as is the case with Gigolo there are exceptions ;)

---

