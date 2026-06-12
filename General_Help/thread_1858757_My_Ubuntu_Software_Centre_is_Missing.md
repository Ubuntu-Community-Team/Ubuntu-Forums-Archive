---
title: "My Ubuntu Software Centre is Missing"
date: 2011-10-13
forum: General Help
---

### Post by kaege on 2011-10-13
Hello.
I am generally new in Ubuntu community (I used another distro in the past). When I open my Ubuntu Software Centre, it asked to reload or refresh something. I regrettably didn't pay more attention and just clicked here and there. I minimized the app and when I maximized it, it goes blank white (Windows's "Not Responding" style). I closed it and the app icon disappear from the Unity sidebar.
I restart the computer and it's still missing. What am I to do now?

---

### Post by philmjones on 2011-10-13
Open up a terminal (CTRL+ALT+T) and type:

```
sudo apt-get update
```If this gives you an error message, post it here. It could be that one of your software sources is messing things up.

In the terminal, then try to open Software Centre:

```
software-center
```Notice the name of the package is the American English spelling of 'centre.' If you get an error message, post it.

---

### Post by Kai Summers on 2011-10-13
Just a quick addition to the last post, in case this is just a missing launcher from within the Ubuntu GUI menu, simply right-click the Ubuntu menu and select Edit Menus...

You need to add a new application Call it Ubuntu Software Centre and then in the command box place the following...

```
/usr/bin/software-center %u
```

Hope that helps

---

### Post by kaege on 2011-10-15
thanks for the advice. I've tried your suggestion and it said that I should install the app via sudo apt-get install software-center. It worked flawlessly :):popcorn:

---

