---
title: "Firefox UI on 10.04"
date: 2010-05-03
forum: General Help
---

### Post by Pazau on 2010-05-03
Hello everyone.

I've just got Ubuntu 10.04 installed on my laptop and have already get problems with the appearance.

I know that Firefox does not use system settings for appearance, but it irritates me that I can not get the look changed.

Here is a screenshot. Notice the difference between the panel and Firefox:
[http://img28.imageshack.us/img28/7460/firefoxudseende.png](http://img28.imageshack.us/img28/7460/firefoxudseende.png)

I've read online about something with XUL, which must determine how Firefox looks.
But unfortunately I can not any programming language yet.

I am running at a resolution of 1280x800 and I run with this option in Ubuntu: [http://img80.imageshack.us/img80/8223/screenee.png](http://img80.imageshack.us/img80/8223/screenee.png)

Some who can help me to customize Firefox to the settings I use in the system?

Sorry for my bad english..

---

### Post by Brandon Williams on 2010-05-04
It looks like you accidentally applied a "persona". This is easy to do ... all you have to do is hover your mouse over one in the browser window. Go to tool -> addons -> themes and switch back to the default theme for 3.6.3. With the default theme, firefox does in fact use the system settings for display of panels, menus, etc.

---

### Post by Treelvr on 2010-05-04
Sorry to piggy back since I have no idea to start a new thread no mater where I look.
Ubuntu is becoming totally worthless to me because I can't control the firefoxs stupid behavior. The whole disappearing bookmark tool bar is driving me nuts. I've found out I need to change the chrome.css file. But once I open it I can't save because of sudo. And if I go sudo gedit I can't find the file. ARRGGHH!

---

### Post by Existance0 on 2010-05-04
View -> Toolbars -> Bookmarks Toolbar

---

### Post by WorMzy on 2010-05-04
You shouldn't need to edit chrome.css. Just make a userChrome.css file in the following folder: /home/<username>/.mozilla/firefox/<profilename>/chrome, and put any UI tweaks in there.

Alternatively, install a persona or a theme.

---

### Post by Pazau on 2010-05-04
Even if I switch back to default theme, there is no difference. My problem is that Firefox does not follow the settings I have set in Ubuntu, and therefore I will have to put them in Firefox in some way to match those I have set in Ubuntu.

It irritates my eyes to use Firefox with the ugly fonts. :(

---

### Post by techunit on 2010-05-04
I can only recommend that you try to remove the persona. Reinstalling firefox may also help.

---

### Post by WorMzy on 2010-05-04
Reinstalling Fx won't help, but making a new profile might. (Alt+F2, run firefox -profilemanager).

If you don't like the default Fx font, change it. Add this to the userChrome file I mentioned earlier:

```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");
* {
        font-family: FreeSans;
        font-size: 10px;
        text-shadow: none;
}
```

Don't like FreeSans? Use something else.

Want to change the colour of the interface without using themes or personas or userChrome? Install [AnyColor]("https://addons.mozilla.org/en-US/firefox/addon/6991").

There's plenty of ways to customise your user experience if you take the time to look.

---

### Post by banerjeerupak on 2010-05-17
how do i install a custom made persona. The little fox that the tutorial talks about is not there on my linux based firefox 3.6.3

---

