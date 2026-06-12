---
title: "File format .url and Chromium/Firefox"
date: 2011-06-19
forum: General Help
---

### Post by RichardC400 on 2011-06-19
I recently changed my XP Desktop to Ubuntu 10.10 for my parents.
Everythings going fine so far, however i have a slight problem with Chromium and Firefox.
I copied a favourites folder that kept all favourites in file a format called .url
neither Chromium or FF will recognise them as Bookmarks.
Is there a way to get them in to bookmarks?

When I open the files in ubuntu it opens them with gedit and i get:

```

[DEFAULT]
BASEURL=http://www.aaireland.ie/routes/
[InternetShortcut]
URL=http://www.aaireland.ie/routes/
IDList=
IconFile=http://www.aaireland.ie/favicon.ico
IconIndex=1
[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,2

```

---

### Post by kreemoweet on 2011-06-19
.url files are a Windows thing. You can use Internet Explorer to export the Favorites
folder as an .html file, which can be imported by most browsers in Ubuntu. The Windows
version of Firefox can also directly import them into its bookmark system, and then
export them in either .html or .json format. The latter can be imported by the Linux
version of Firefox, I don't know about other browsers.

---

