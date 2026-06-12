---
title: "Extracting zip files"
date: 2010-01-08
forum: General Help
---

### Post by boarder428 on 2010-01-08
I'm trying to install a 3rd party screenlet that downloaded as a zip file (I'm using Linux Mint 7) and of course the screenlet manager won't install it due to the file type.  I'm not quite sure how to extract files from the command prompt and I get the following error when trying to extract using Nautilus ```
You don't have the right permissions to extract archives in the folder "file:///usr/share/screenlets/Clock/themes"

```

---

### Post by lisati on 2010-01-08
Quite often you'll need admin privileges to extract to your choice of destination.
Try from the terminal:
```
gksudo nautilus
```
**Caution:** Be careful to get the target of your copy correct!

---

### Post by steveneddy on 2010-01-08
You could right click the file on your desktop and select "Extract Here", then in terminal open up Nautilus as root

```
gksudo nautilus
```

then simply drag the file into the folder you need it to go into

or

after extracting the file to your desktop

```
cd ~/Desktop
```

then

```
sudo mv **nameoffile** usr/share/screenlets/Clock/themes
```

EDIT:

lisati beat me to my main point.

Let us know how this works for you.

---

### Post by boarder428 on 2010-01-09
thanks, that worked great!

---

