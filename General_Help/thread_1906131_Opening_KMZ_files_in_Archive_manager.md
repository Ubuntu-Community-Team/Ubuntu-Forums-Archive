---
title: "Opening KMZ files in Archive manager"
date: 2012-01-08
forum: General Help
---

### Post by pgdave on 2012-01-08
I bought a new machine, and installed Ubuntu 11.11 fresh.

Now I cannot open .KMZ files in archive manager. I just get an 'archive type not supported' message.

Any solutions? I know I can open them in Google Earth, but I'm developing applications that write them, and I want to see what's written in the enclosed KML file.

There was no problem in the previous version (10.04) that I had installed.

---

### Post by pbrane on 2012-01-08
You should be able to associate the .kmz extension with archive manager using nautilus. If I remember correctly you would right-click on the file and choose the application to open it with. My understanding is that kmz files use a standard zip format so archive manager should open one just fine.

```

cat /usr/share/applications/defaults.list | grep file-roller

```
will show you what you have associated with archive manager. To see if you have a local defaults.list do this:

```

cat ~/.local/share/applications/defaults.list

```

---

### Post by pbrane on 2012-01-08
delete-able double post. Sorry.

---

### Post by pgdave on 2012-01-08
Archive manager is already the default file opener - double-clicking the file invokes archive manager - which then complains.

As you say, KMZ files are just KML(plus possibly graphics files) zipped together.

---

### Post by pbrane on 2012-01-08
Archive manager is the default for kmz files? Actually I just downloaded a kmz file and I see what you mean, double clicking it results in archive-manager starting and then saying archive type not supported. If I change the extension to .zip it opens just fine. I'm going to research this and if I find a solution I will post back.

---

