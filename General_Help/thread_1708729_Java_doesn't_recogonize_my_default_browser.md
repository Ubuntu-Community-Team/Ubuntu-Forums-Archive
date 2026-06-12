---
title: "Java doesn't recogonize my default browser"
date: 2011-03-17
forum: General Help
---

### Post by TheWatcher000 on 2011-03-17
I'm using SeaMonkey instead of FireFox, and this won't change. SeaMonkey is set to be the default browser in Preferred Applications
I use a java chat client every day (.jar), which has a button that opens an appropriate web address.

The problem is, it opens that site with FireFox instead of my desired SeaMonkey.

The client runs fine with openjdk and sunjava too ( I have both installed ), but they both open sites with FireFox. In Sun Java 6 Plugin Control Panel I set the SeaMonkey launcher as "Command to launch default browser", but the client still opens sites with FireFox.
As for OpenJDK, I haven't found any way to modify settings.

I would be fine using either java, thanks for any help

---

### Post by TheWatcher000 on 2011-03-18
Bump..

---

### Post by luigi_mb on 2011-03-18
> **TheWatcher000 said:**
> I'm using SeaMonkey instead of FireFox, and this won't change. SeaMonkey is set to be the default browser in Preferred Applications
I use a java chat client every day (.jar), which has a button that opens an appropriate web address.

The problem is, it opens that site with FireFox instead of my desired SeaMonkey.

The client runs fine with openjdk and sunjava too ( I have both installed ), but they both open sites with FireFox. In Sun Java 6 Plugin Control Panel I set the SeaMonkey launcher as "Command to launch default browser", but the client still opens sites with FireFox.
As for OpenJDK, I haven't found any way to modify settings.

I would be fine using either java, thanks for any help

Did you use the **full path** for Seamonkey in the "Sun Java 6 Plugin Control Panel" > "Command to launch default browser"?

Did you click on **Apply** after doing so?


/luigi

---

### Post by TheWatcher000 on 2011-03-19
Yes and yes. I copied the file path from the launcher I normally use to start the browser, then clicked apply. If I open the Plugin Control Center, the path is there.

---

### Post by TheWatcher000 on 2011-03-20
bump

---

### Post by TheWatcher000 on 2011-03-22
bump

---

### Post by TheWatcher000 on 2011-03-25
Bump

---

### Post by TheWatcher000 on 2011-03-27
bump

---

### Post by JP121 on 2011-03-27
The program may not recognize SeaMonkey as being legitimate.  I know that I have a few programs that don't recognize my default Chrome and continue to run Firefox.

---

### Post by TheWatcher000 on 2011-03-28
What to do,  how to fix?

---

### Post by TheWatcher000 on 2011-03-31
Anyone?

---

### Post by TheWatcher000 on 2011-04-04
Where else could I ask?

---

### Post by Kuitsi on 2012-04-16
I have same kind of problem in Kubuntu. Opera is my default browser and other programs uses it when opening links but Java keeps opening URLs with Firefox.

```
sudo update-alternatives --config x-www-browser
```
gives me this:
```
There are 5 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                    Priority   Status
------------------------------------------------------------
  0            /usr/bin/google-chrome   200       auto mode
  1            /usr/bin/firefox         40        manual mode
  2            /usr/bin/google-chrome   200       manual mode
  3            /usr/bin/konqueror       30        manual mode
* 4            /usr/bin/opera           200       manual mode
  5            /usr/bin/rekonq          40        manual mode
```

I don't know about those priorities but at least Firefox does not have biggest nor smallest value.

---

### Post by oldos2er on 2012-04-16
Closed. Please start a new thread; this one is over a year old.

---

