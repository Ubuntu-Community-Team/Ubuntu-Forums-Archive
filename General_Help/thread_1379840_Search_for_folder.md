---
title: "Search for folder"
date: 2010-01-13
forum: General Help
---

### Post by hhh on 2010-01-13
How do you search for folders in Ubuntu? The find function is great at locating files, but is ignoring folders that I know exist on my computer, even when I add the "Show hidden files" option to search. Same with entering find or locate in terminal.

---

### Post by Darce on 2010-01-13
What flavour/version are you running ?

I just tried in Ubuntu 9.10, and folders are found as well as files with default settings

---

### Post by cong06 on 2010-01-13
and you tried:
```

find /path -name "name" -type d

```
the "-type d" searches for directories.

Maybe list the actual find commands that you used to make sure that there's not a typo?
I'm not sure how to go about debugging nautilus...

---

### Post by hhh on 2010-01-13
Running Karmic. Say I have a hidden directory in /home/hhh named .icons, it doesn't turn up, even if I add "Show hidden and backup files" to Places>Search for files...>hhh>.icons

The terminal command works if I enter find .icons -type d, but not if I just enter find icons -type d. But I know there is a folder named icons in /usr/share, so what gives? I thought everything in Linux was a file?

-edit- So terminal does find /usr/share/icons if I enter find -name "icons" -type d, but it finds so many other "icon directories that I have to go into terminal preferences to set scroll options way high to be able to find it. I know Linux users hate when Windows comparisons are made, but if you search for icons in XP you would find all directories for icons and .icons right off the bat, if there were any.

---

### Post by cong06 on 2010-01-13
> **hhh said:**
> Running Karmic. Say I have a hidden directory in /home/hhh named .icons, it doesn't turn up, even if I add "Show hidden and backup files" to Places>Search for files...>hhh>.icons
Actually, I just noticed I'm getting the same response. I know I have a ".mozilla/firefox" folder, but searching in nautilus for "mozilla" ".mozilla" and "firefox" don't give any results...

With find:
> **hhh said:**
> The terminal command works if I enter find .icons -type d, but not if I just enter find icons -type d. But I know there is a folder named icons in /usr/share, so what gives? I thought everything in Linux was a file?
It sounds like you're opening a terminal and writing:
```

find .icons -type d
find icons -type d

```
In which case, you're searching only your home directory, and only searching inside the "~/.icons" and "~/icons" folder (respectively).
If you want /usr to be included you'd have to do something like:
```

find /usr -name "icons" -type d

```

Like I said, I have no idea what's up with nautilus. I'm using jaunty.

---

### Post by hhh on 2010-01-13
Thanks for the feedback. There is a big filed somewhere about wonky search behavior in Nautilus when searching outside of the home directory, I think. Frustrating...

-edit- is there really so little documentation on this that querying 'ubuntu "search for folders"' on Google is already bringing this thread up as the number 2 search result? After 2 hours?

---

