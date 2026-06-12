---
title: "Moving folders between Users"
date: 2009-09-06
forum: General Help
---

### Post by onespeedbiker on 2009-09-06
When I loaded Ubunto 9.04 I transferred my wife's folders from her user account on XP. I have now created a user account for her in Ubuntu and would like to move her files to her account. How do I do that?

---

### Post by alejaaandro on 2009-09-06
just put them under /home/"your_wife's_username" and let her sort how she want's it organized.. 

you will need root privileges to do that.. simple way:
press ALT+F2
type "gksu nautilus"

you will be asked for the root's password (which should be the same as the password for the default account you created when installing ubuntu)

now you can manage all the files and folders in your system (so be cautious!!!)

in order to make it easier, install nautilus scripts.. that way, by right clicking in the file manager you'll be able to run some commands like opening a window with root privileges..

(tip: while in root nautilus, go to edit->backgrounds and emblems.. then go to colors and drag a color to your file manager.. that way, when you open a root windows you'll be reminded and you'll be more cautious with what you do)

---

### Post by orlox on 2009-09-06
In any case, copying the files as root, as described on the previous post, will might leave permission issues. After copyign the files, I reccomend you to open up a terminal and set the owner of those files to your wifes username:

```

sudo chown -R /home/your_wife_username your_wife_username

```

Just run that and replace your_wife_username with what corresponds. This will set all files contained under her folder to belong to her.

---

### Post by alejaaandro on 2009-09-06
you are right!!

copying them will indeed change owner and permissions.. moving them, though, won't..

---

### Post by orlox on 2009-09-06
> **alejaaandro said:**
> you are right!!

copying them will indeed change owner and permissions.. moving them, though, won't..

Though, the permissions issue is a bit more tricky than it seems. First, I dont think there's a way that permissions are correct right from the beggining, these are copied from an XP partition that doesnt even support unix permissions...

In any case, the most simple solution is to leave the files in a place that can be accessed by his wife account, and copy them using her account. That will inmediately leave her as the owner of the files.

---

### Post by Slim Odds on 2009-09-06
> **alejaaandro said:**
> copying them will indeed change owner and permissions.. moving them, though, won't..

Depends on how you copy it.

---

### Post by onespeedbiker on 2009-09-08
Found a much easier way. If one clicks Places/Home Folder/File System/Home you end up with a folder that shows both Users. You can now switch files at will.

---

