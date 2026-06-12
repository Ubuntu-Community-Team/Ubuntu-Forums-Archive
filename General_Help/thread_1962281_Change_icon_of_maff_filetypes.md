---
title: "Change icon of maff filetypes"
date: 2012-04-20
forum: General Help
---

### Post by majidkamali on 2012-04-20
Hi.
I want to change icon of maff file format.
I googled and found a thread in this forum. I did following steps, but icons did not change.
What's the problem?

1. I found maff mime type from maff specification. (application/x-maff)
2. I added "application/x-maff maff" to file /etc/mime.types using gedit and sudo through terminal.
3. I downloaded a svg format of firefox icon and put it into desktop and changed its name to "application-x-maff.svg"
4. I copied icon from desktop to /usr/share/icons/gnome/scalable/mimetypes using cp and sudo through terminal.
5. Logout and login again to linux, but did not changed.

*: I should mention that, by default, file roller, opened maff files, I changed that to firefox. furthermore, while extension is maff, in properties window, it is of type application/zip.

---

### Post by bolocholo on 2013-02-11
Hi. Here's how I did it:

1) Install assogiate (it's available at Synaptic).

2) Open assogiate and create a new type with the following values:

General tab:
- Category: Multipurpose file
- Name: application/x-mozillarchive
- Description: Mozilla Archive Format
- Default icon: (path to downloaded Firefox icon .svg file)*

Tab Related types:
- Add in the "Aliases" box: application/x-maff

Tab Filenames:
- Add this pattern: *.maff

3) Restart.


* This file I downloaded from <http://en.wikipedia.org/wiki/File:Firefox-logo.svg> and saved it to </usr/share/icons/gnome/scalable/mimetypes/gnome-mime-application-maff.svg>.

---

### Post by majidkamali1370 on 2013-02-12
Thanks

---

### Post by bolocholo on 2013-02-12
You're welcome. 

I added a third step, restart, because I was having problems with Firefox not opening the .maff file but instead a bunch of empty tabs. 

Here ([https://addons.mozilla.org/es/firefox/addon/mozilla-archive-format/reviews/295814/](https://addons.mozilla.org/es/firefox/addon/mozilla-archive-format/reviews/295814/)) I found I had to update MIME type database and then restart X (they give a whole different step-by-step solution to this same problem), but just restarting the computer did the trick for me.

I'm really new to Linux (came from Mac and Windows), so I couldn't explain why this works, but it does seem to be a good solution to open .maff files directly with Firefox and specially to have them show the Firefox icon.

---

