---
title: "Banshee opens when I open &quot;Pictures&quot; from menu"
date: 2009-11-06
forum: General Help
---

### Post by tylerannosaurus on 2009-11-06
So I click on the Ubuntu main menu and go to Places>Pictures and Banshee opens. If I go to any of the files, Banshee opens (whether minimized or not). If I click on "Computer" or anything other than a folder, it works fine...

I'm not sure how to open a file in terminal or I could do that and give you the output.

I have no idea why it suddenly started doing this. I might try reinstalling Banshee.

I'm running 9.10 Karmic Koala right now.

---

### Post by tylerannosaurus on 2009-11-06
Update: I tried uninstalling Banshee, logging out, reinstalling, logging out and tried to open "Pictures" again. Same thing happened!

---

### Post by MelDJ on 2009-11-06
type this in terminal /home/usr/Pictures/apicture.jpg

replace apicture with the name of any picture you have and usr  with your user name.

see if banshee opens

---

### Post by tylerannosaurus on 2009-11-06
I tried it, this is what it gave:

[HTML]$ /home/ty/Pictures/Astronomy/Aurora.jpg
bash: /home/ty/Pictures/Astronomy/Aurora.jpg: cannot execute binary file[/HTML]

---

### Post by tylerannosaurus on 2009-11-21
I've found a solution:

[http://ubuntuforums.org/showpost.php?p=6102124&postcount=20]("http://ubuntuforums.org/showpost.php?p=6102124&postcount=20")

Apparently it had been marked to open with Banshee. This fixed it though...I only had to do it with one folder and it takes care of the rest of those types.

---

