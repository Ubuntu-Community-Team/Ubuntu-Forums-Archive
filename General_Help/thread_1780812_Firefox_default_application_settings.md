---
title: "Firefox default application settings"
date: 2011-06-12
forum: General Help
---

### Post by wizardus13 on 2011-06-12
Ever since I installed ghex, it's become the default in Firefox for opening many applications (like .txt files) that I want to open with other programs. In Preferences->Applications, txt doesn't show up and I can't add it or anything.

Whenever I download something like a text file, it says "ghex2 (default)". If I add another application, like /usr/bin/gedit, the next time I download a text file it disappears from the list.

I tried deleting mimeTypes.rdf, but it didn't do anything and ghex2 was still this default application. Then I tried deleting the entire .mozilla directory, but it still had no effect. I couldn't find the base mimeTypes.rdf, if it exists.

---

### Post by philinux on 2011-06-12
> **wizardus13 said:**
> Ever since I installed ghex, it's become the default in Firefox for opening many applications (like .txt files) that I want to open with other programs. In Preferences->Applications, txt doesn't show up and I can't add it or anything.

Whenever I download something like a text file, it says "ghex2 (default)". If I add another application, like /usr/bin/gedit, the next time I download a text file it disappears from the list.

I tried deleting mimeTypes.rdf, but it didn't do anything and ghex2 was still this default application. Then I tried deleting the entire .mozilla directory, but it still had no effect. I couldn't find the base mimeTypes.rdf, if it exists.

In firefox prefs>apps use text as the filter not txt.

---

### Post by wizardus13 on 2011-06-12
text/plain isn't showing up anywhere in the applications. But I don't think that's the problem; before I reset all the Firefox settings, it did show up, but I still couldn't remove the (default) because it was the system default or something. Before, it would show only a choose button, and then after choosing something that would be set as the default for the application and it would show up in preferences.

Also, uninstalling ghex only makes Firefox unable to open it.

---

### Post by wizardus13 on 2011-06-13
By the way, I am using Ubuntu 11.04. I also have another problem where the "Launch web browser" actually opens up a new tab with a ten-digit number that seems to increase over time. I solved that by adding a new keyboard shortcut that just opens Firefox.

---

### Post by wizardus13 on 2011-10-07
I finally figured out how to fix the problem... essentially, I followed the steps at [http://www.johannes-eva.net/change-the-default-application-ubuntu-linux](http://www.johannes-eva.net/change-the-default-application-ubuntu-linux) and deleted all of the entries with ghex2 in them. I think the problem was with the mime-type used to include files for downloading in web applications.

---

