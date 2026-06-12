---
title: "Help assigning custom icon to nickel-browser"
date: 2011-02-27
forum: General Help
---

### Post by doodlebox on 2011-02-27
Right now, I've got ubuntu 10.04 installed and themed to look like jolicloud and I've installed nickel-browser to make my own web apps. This is the program developed by jolicloud that is used to make the apps. The problem is that I can't seem to get the icon on the taskbar to match the one on my desktop. I'm assuming it has to do with the code in the launcher, but I can't find out how to do it. I've searched and nothing. I know it would be easier to just go to jolicloud, but I like regular ubuntu much better.

Right now this is the code that I have for the launcher
```
nickel-browser --app=http://listen.grooveshark.com
```

Is there anyway I can change this so that the taskbar will use my custom icon instead of the regular chromium icon? This is what it looks like:
[[IMG]http://i14.photobucket.com/albums/a315/green-cheese/th_Screenshot.png[/IMG]](http://i14.photobucket.com/albums/a315/green-cheese/Screenshot.png)

---

### Post by doodlebox on 2011-02-28
Bump, I really need help with this one.

---

### Post by doodlebox on 2011-02-28
I figured out how to do it!

I needed to put the following code in the launcher
```
nickel-browser --app=http://listen.grooveshark.com -icon-id=**grooveshark**
```

Then I moved the png icon that I wanted into the following directory:
~/.icons/Jolicloud/scalable/apps

And renamed it to match the -icon-id (I put it in bold)
So in this case it would be  **grooveshark**.png

And then edited the index.theme to include the following
```
[scalable/apps]
Size=48
Context=Applications
Type=Scalable
```

---

