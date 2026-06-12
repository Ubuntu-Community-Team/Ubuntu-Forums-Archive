---
title: "Skype icon has disappeared after updating to 11.10"
date: 2011-10-16
forum: General Help
---

### Post by kirill578 on 2011-10-16
Hey, I've just updated my ubuntu to 11.10, but for some reason the skype's icon (in the right left cornor )
has disappeared. I've tried to reinstall '**sni-qt' **but it doesn't seems to work. 

Is there something I can do?

---

### Post by roobinatube on 2011-10-16
yeah, this is what I did. Some applications can be whitelisted as being allowed an icon there.

```
 gsettings get com.canonical.Unity.Panel systray-whitelist
```

gave me: ['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Update-notifier', 'Skype']

So then skype must be added to the whitelist. So add skype like below:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Update-notifier', 'Skype']"

```

Now it should work.

I also found, that if you want skype to start at login, and sit in the tray, you need another little trick. I found that the whitelist only works if skype is started manually after login. Add this to the startup list:

```
gnome-panel --replace
```

And it all works perfectly for me.

Hope that works for you too.

Roo

---

### Post by claudiueu on 2011-10-20
Thanks a lot Roo, it works!


> **roobinatube said:**
> yeah, this is what I did. Some applications can be whitelisted as being allowed an icon there.


```
 gsettings get com.canonical.Unity.Panel systray-whitelist
```gave me: ['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Update-notifier', 'Skype']

So then skype must be added to the whitelist. So add skype like below:

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Update-notifier', 'Skype']"

```Now it should work.

I also found, that if you want skype to start at login, and sit in the tray, you need another little trick. I found that the whitelist only works if skype is started manually after login. Add this to the startup list:

```
gnome-panel --replace
```And it all works perfectly for me.

Hope that works for you too.

Roo

---

### Post by Ivo_Wever on 2011-10-21
```
gnome-panel --replace
``` didn't do it for me: I had to log out and log in again to get it working, but work it did :).

```
gnome-panel --replace
``` did return the regular Gnome panel bottom panel to me, but I didn't really want that ;)

---

### Post by nikola.borisof on 2011-10-22
This is by far the stupidest **** I have seen been put in Ubuntu. Why would there be a white list for notification icons. If i use an application and it has a notification i probably want it displayed. This Unity thing...

---

### Post by joris1977 on 2011-10-25
Thanks roobinatube! That did the trick.

---

### Post by brynellis on 2011-10-27
Worked perfectly for me!  Thanks very much.  I've been missing loads of messages.  This is wicked.  Thanks again.

---

### Post by roobinatube on 2011-10-27
I have realised the easiest way to avoid the "gnome-panel --replace" issue, is make sure that skype starts after gnome-panel. I was having some issues because sometimes the skype icon would be present, others not. I figure this was because "gnome-panel --replace" was actually happening before skype started!

So I found the most consistant thing to do is delete the startup entries for skype and "gnome-panel --replace", and add my own shell script.

```
gedit ~/.skype-start.sh
```

Copy/paste this into the file:

```
#!/bin/bash

sleep 10
skype
```

Then make it executable (or right click > properties >permissions > allow executing):
```
chmod +x ~/.skype-start.sh
```

Then add this as a startup item. 10 seconds should be plenty on most systems to guarantee skype starts after everything else.

---

### Post by gairsty on 2011-10-29
thanks roobinatube, works fantastically.

---

### Post by vmajor on 2011-11-07
...did not work for me.

Still no Skype notification at the top, and now I have gnome-panel start up every time I boot.

I no longer care about Skype notification even though it is stupid that I just cannot make it appear and that the bloody thing is so buggy that it dies/disappears so often, but I truly, really need to get rid of gnome-panel on boot.

I looked through various threads and solutions and I cannot find anywhere where gnome-panel is included as a boot/session start process.

Please tell me where gnome-panel was added so that I can remove it.

Right now I have to kill -9 gnome-panel every time I start Ubuntu...

V.

---

### Post by wpf999 on 2011-11-23
> **roobinatube said:**
> I have realised the easiest way to avoid the "gnome-panel --replace" issue, is make sure that skype starts after gnome-panel. I was having some issues because sometimes the skype icon would be present, others not. I figure this was because "gnome-panel --replace" was actually happening before skype started!

So I found the most consistant thing to do is delete the startup entries for skype and "gnome-panel --replace", and add my own shell script.

```
gedit ~/.skype-start.sh
```

Copy/paste this into the file:

```
#!/bin/bash

sleep 10
skype
```

Then make it executable (or right click > properties >permissions > allow executing):
```
chmod +x ~/.skype-start.sh
```

Then add this as a startup item. 10 seconds should be plenty on most systems to guarantee skype starts after everything else.

Works perfectly. Thanks so much :D

---

### Post by coverup1128 on 2012-01-05
I use 11.04 with classic gnome, but have the same problem, ie the skype icon does not appear in the panel, so I cannot even tell whether I am signed in or not.  

Is there a way to make the green tick icon appear in the top panel? How should I modify the proposed whitelisting command to work on Gnome classic?

Thanks

---

### Post by Momof9Blessings on 2012-01-10
I can see the icon after I turn it on manually.

Is there a way for it to load at startup?

I did find it in my startup....

---

### Post by Jynks on 2012-05-06
these instructions are workign fine.. but i do not know how to "ad it to start up" 

I have made the file as per intsructions... but i can not even run it form the console... like when i do a ls -ls I can see ti and it is green... .

[img]http://www4.picturepush.com/photo/a/8204302/640/8204302.png[/img]

But how do i add this to my startup items, maybe you cna only run it from there?

---

### Post by jbaldwin9182 on 2012-06-02
Try '[FONT=Courier New]~/.skype-start.sh[/FONT]' to run the script from the command line. You need to type the full path to the script (or an abbreviation, like ~ which means home directory) unless said script is in a directory in the PATH, or the shell will not be able to find it.

To add the script to startup, go to 'Gear->Startup Applications', click Add, Browse for the script (or just put [FONT=Courier New]'~/.skype-start.sh[/FONT]' as the Command,) give it a Name and optionally a Comment, hit Add, and make sure the new entry is enabled. Note: the Gear is the icon at the top right of your Unity environment, the same one you click before you Shut Down your computer.

---

