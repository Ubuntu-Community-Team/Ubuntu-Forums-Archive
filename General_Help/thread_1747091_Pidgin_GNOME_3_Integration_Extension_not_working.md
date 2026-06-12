---
title: "Pidgin GNOME 3 Integration Extension not working"
date: 2011-05-02
forum: General Help
---

### Post by morgue on 2011-05-02
Hey guys, I found this extension
[http://blog.kagesenshi.org/2011/04/pidgin-and-gnome3.html](http://blog.kagesenshi.org/2011/04/pidgin-and-gnome3.html)

But haven't been able to get it working.

I copied the files to the mentioned directory
~/.local/share/gnome-shell/extensions/

I tried setting the file permissions to full

```

david@aitdes2:~/.local/share/gnome-shell/extensions/gnomeshell@pidgin.im$ ls -l
total 24
-rwxrwxrwx 1 david david 14219 2011-04-29 18:31 extension.js
-rwxrwxrwx 1 david david   163 2011-04-29 18:31 metadata.json
-rwxrwxrwx 1 david david   177 2011-04-29 18:31 stylesheet.css

```

No idea what else I could try.

---

### Post by morgue on 2011-05-02
Looks like it's installed in [LookingGlass]("http://live.gnome.org/GnomeShell/LookingGlass") but it does nothing for me yet.

---

### Post by numkem on 2011-05-02
> **morgue said:**
> Looks like it's installed in [LookingGlass]("http://live.gnome.org/GnomeShell/LookingGlass") but it does nothing for me yet.

Exact same thing...

---

### Post by morgue on 2011-05-02
Maybe it's something I need to enable so GNOME 3 extensions work? I don't know...

---

### Post by bmbaker on 2011-05-02
try checking your shell version in the metadata.json file of the extension and see if it has the value as your version of gnome-shell

i.e. "shell-version": ["3.0.1"]

---

### Post by numkem on 2011-05-02
> **bmbaker said:**
> try checking your shell version in the metadata.json file of the extension and see if it has the value as your version of gnome-shell

i.e. "shell-version": ["3.0.1"]

In the metadata.json
```
{"shell-version": ["3.0.0.2"], "uuid": "gnomeshell@pidgin.im", "name": "Pidgin Integration", "description": "Integrate the Shell chat notification with Pidgin IM"}
```

I'm running the lastest from the ppa :
```
Package: gnome-shell
Status: install ok installed
Priority: extra
Section: gnome
Installed-Size: 3924
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 3.0.0.2-0ubuntu1~build2

```

---

### Post by morgue on 2011-05-02
Same here:
3.0.0.2-0ubuntu1~build2

---

### Post by numkem on 2011-05-02
> **morgue said:**
> Same here:
3.0.0.2-0ubuntu1~build2

Figured it out!

From the site you quoted, the last post explains what to do, just not 100% clearly.

What you need to do is to changed version in metadata.json to :
```
"shell-version": ["3.0"]
```

And comment out the line 398 of extension.js like this :
    ```
//imports.gettext.bindtextdomain('gnome-shell-extensions', metadata.localedir);
```

And save all those files.

The reason we have to do this is because apparently the version of gnome-shell in the ppa isn't the "real" 3.0.0.2 making it incompatible and so not working.

Once all is done, you can easily restart gnome-shell by doing ALt-F2 and typing "r" (without quotes).

Enjoy!

---

### Post by mackendw on 2011-05-02
A quite useful tool in debugging the Javascript code you add as an extension is lg.  Alt-F2 -> lg.  Select the errors tab.

---

### Post by morgue on 2011-05-02
> **numkem said:**
> Figured it out!

From the site you quoted, the last post explains what to do, just not 100% clearly.

What you need to do is to changed version in metadata.json to :
```
"shell-version": ["3.0"]
```

And comment out the line 398 of extension.js like this :
    ```
//imports.gettext.bindtextdomain('gnome-shell-extensions', metadata.localedir);
```

And save all those files.

The reason we have to do this is because apparently the version of gnome-shell in the ppa isn't the "real" 3.0.0.2 making it incompatible and so not working.

Once all is done, you can easily restart gnome-shell by doing ALt-F2 and typing "r" (without quotes).

Enjoy!

Nice, got it working also, thanks.

---

### Post by _albatros on 2011-05-08
Hi,
I copied all the files, I made changes according to the post 8, but further integration is not working (even after rebooting the system).

Can someone help me?

PS How do I install it?
[http://sourceforge.net/projects/gnomeshpidgin/](http://sourceforge.net/projects/gnomeshpidgin/)

PS2 Google Translate

---

### Post by _albatros on 2011-05-09
Nobody can help?

---

### Post by matthewbpt on 2011-05-09
Does this extension provide integration only with the status menu on the top right, or notification integration like Empathy has?

---

### Post by _albatros on 2011-05-09
@matthewbpt, this extension provide integration only with the status menu on the top right

I have GNOME Shell version 3.0.1, I'm doing everything according to what you wrote on the previous page, unfortunately, still not working :/

---

### Post by _albatros on 2011-05-12
Nobody can help?

---

### Post by bmbaker on 2011-05-12
> **_albatros said:**
> Nobody can help?

you try this out I found it on line and have modified a bit, but i can't remember where to give the creator credit, but this wks i hope for you :-)

save this code as:  metadata.json

```

{
   "shell-version": ["3.0."],
   "uuid": "EvilStatusIconForever@NBGentoo",
   "name": "Evial Status Icon Forerver",
   "description": "This extension let you make notification status icon show at the top bar",
    "url": "http://example.com/"
}

```save this code as:  extension.js

```

const StatusIconDispatcher = imports.ui.statusIconDispatcher;
const Panel = imports.ui.panel;

function main() {

    // Put those those notification you want display at top bar here.
    // The key is the text show when you hover your mouse to the notification
    // bar icon at the bottom in the lower case letter.

    //StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['gcin'] = 'gcin';
    StatusIconDispatcher.STANDARD_TRAY_ICON_IMPLEMENTATIONS['pidgin'] = 'pidgin';

    // Disable bulit-in icon that you don't need.
    //Panel.STANDARD_TRAY_ICON_SHELL_IMPLEMENTATION['a11y'] = ''; 
    // Panel.STANDARD_TRAY_ICON_SHELL_IMPLEMENTATION['volume'] = ''; 
    // Panel.STANDARD_TRAY_ICON_SHELL_IMPLEMENTATION['battery'] = '';
    // Panel.STANDARD_TRAY_ICON_SHELL_IMPLEMENTATION['keyboard'] = ''; 
    // Panel.STANDARD_TRAY_ICON_SHELL_IMPLEMENTATION['bluetooth'] = '';
    // Panel.STANDARD_TRAY_ICON_SHELL_IMPLEMENTATION['network'] = '';

}

```

place both in a folder and name it:  EvilStatusIconForever@NBGentoo

place the folder in:  .local/share/gnome-shell/extensions
then do the  alt-f2 -r

---

### Post by _albatros on 2011-05-13
@bmbaker, unfortunately does not work :/
```
"shell-version": ["3.0."],
``` changed to ```
"shell-version": ["3.0.1"],
``` because I'm such a version.
Does not work as the first extension, I did everything according to your advice :/

---

### Post by bmbaker on 2011-05-15
> **_albatros said:**
> @bmbaker, unfortunately does not work :/
```
"shell-version": ["3.0."],
``` changed to ```
"shell-version": ["3.0.1"],
``` because I'm such a version.
Does not work as the first extension, I did everything according to your advice :/
just change the 3.0.1 to 3.0 and it should wk :-)

---

### Post by rabinhood on 2011-05-22
Thanks bmbaker! I also added wicd icon to top tray and now gnome3 is almost perfect for me.

---

### Post by bmbaker on 2011-05-23
> **rabinhood said:**
> Thanks bmbaker! I also added wicd icon to top tray and now gnome3 is almost perfect for me.

your welcome :-)

---

### Post by maverick280857 on 2011-05-27
> **rabinhood said:**
> Thanks bmbaker! I also added wicd icon to top tray and now gnome3 is almost perfect for me.

How did you add the wicd icon to the top tray? Is there an extension for this too? If yes, please post the details.

---

### Post by FanatikCZ on 2011-06-07
I just had to change ```
"shell-version": ["3.0."],
```to ```
"shell-version": ["3.0"],
```Seems the dot matters and it works fine so far. Thank you!

---

### Post by cusaro on 2011-06-10
hello

is it possible when i answer the message in the notifycation area that the message is marked as read in the pidgin chat window? actually i have to click inside the window to do that.


cusaro

---

