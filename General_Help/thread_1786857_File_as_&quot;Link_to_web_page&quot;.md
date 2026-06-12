---
title: "File as &quot;Link to web page&quot;"
date: 2011-06-20
forum: General Help
---

### Post by Seregwethrin on 2011-06-20
Hi,

I want to create a file that when it double clicked I want a specific web page to be opened with the default web browser.

This can be done easily in KDE just by selecting "Create New, Link to Location (URL)" at right click menu (context menu).

How can I do this? I searched but couldn't find, sorry.

I'm using Ubuntu 11.04.
Thanks.

---

### Post by Matt__ on 2011-06-20
I cant speak for other browsers, but with Firefox you can just drag the link using the favicon (to the left of the address bar) to the desktop...link auto created.


//edit: Ok so this works with Chromium, but not with Midori. The link made in chromium also opened up my default browser (Firefox) when I clicked it.

Otherwise create a new file and insert the following;
```
#bin bash!
<name of browser> <web address>
```so a link to this page using firefox would be ;
```
#bin bash!
firefox http://ubuntuforums.org/showthread.php?p=10960608#post10960608
```(dont forget to make it executable in the files properties menu)
which is much more effort than dragging and dropping :P

using 11.04 in classic or unity mode.

---

### Post by Seregwethrin on 2011-06-20
But it won't work for all computers :) For example if I set:

```
#bin bash!
chromium http://www.google.com
```

than a computer which is using firefox as default web browser and doesn't have chromium installed will give error.

---

### Post by Azdour on 2011-06-21
Hi,

I know in Gnome I would try:

```

gnome-open http://www.google.com
```

I think there is a kde-open in KDE.

---

### Post by Seregwethrin on 2011-06-21
gnome-open opened the web page in Firefox even my default web browser is Chromium.

---

### Post by mcduck on 2011-06-21
> **Azdour said:**
> Hi,

I know in Gnome I would try:

```

gnome-open http://www.google.com
```

I think there is a kde-open in KDE.

There's also a common standard which works in any xdg-compatible environment.
```
xdg-open { file | URL }
```

for example:
```

#!/bin/sh
xdg-open &#8216;http://ubuntu-forums.org&#8217;
```

xdg-open opens a file or url in the configured default program or browser.

At least with Firefox, you can also drag a page from it's icon in the urlbar, or a tab, into the desktop to create a .desktop file that points to that page.

---

### Post by Seregwethrin on 2011-06-21
Ah sorry, Chromium says 'Not default browser', I got it as 'Is default browser'.

Weird though I click "Make default browser" and it doesn't do it.
But that's another problem and there are some solutions on Google Search results.

I guess xdg-open or gnome-open will work fine after I handled Chromium's that problem.

Thanks all.

---

