---
title: "Search/find files in lubuntu"
date: 2011-12-17
forum: General Help
---

### Post by rng on 2011-12-17
I want to use lubuntu so I downloaded iso file and ran the livecd. It worked very well but in the file manager (pcmanfm?) I could not find option to search/find files. How do I find/search files in lubuntu? Can I install konqueror in lubuntu? Will it need to download a lot of support files?

---

### Post by whatthefunk on 2011-12-17
You can use the terminal.  The easiest command to use is "locate."  For example, if you wanted to find a file called "Summer_Pictures" you would open a terminal and do this:

```
locate Summer_Pictures
```

It will give you the location of the file, if it exists.  The only problem with locate is that it uses info gathered at startup to find files so if you have moved things around in the current session, it will give you incorrect search results.

You could also use the command "find."  Its a bit more complex than locate but can be tweaked a lot to give more precise results.

---

### Post by rng on 2011-12-18
bump

---

### Post by Telengard C64 on 2011-12-18
The answer you already got (post #2) looked pretty legit to me.

> **rng said:**
> in the file manager (pcmanfm?) I could not find option to search/find files. How do I find/search files in lubuntu? 

[How to Search for Files in Lubuntu using GUI application - Community Ubuntu Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_Search_for_Files_in_Lubuntu_using_GUI_application)

> Can I install konqueror in lubuntu?

I don't see why not. Have you tried?

> Will it need to download a lot of support files?

Seems likely.

**_EDIT_**

If all else fails, this should work 100% of the time.

```
find /PATH/TO/SEARCH/ -iname '*FILE-NAME*'
```

Substitute:
[list]
[*]**/PATH/TO/SEARCH** is the full path to the directory you want to search in. The search will automatically recurse into all subdirectories.
[*]**FILE-NAME** is some part of the name of the file (the basename).
[/list]

For more information:
```
man find
```

---

### Post by Rodney9 on 2011-12-18
You could use 'Catfish'


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by SteveDee on 2011-12-19
> **rng said:**
> ...How do I find/search files in lubuntu? ...

Open Synaptic Package Manager, then search for, and install: gnome-search-tool

---

### Post by rng on 2011-12-19
Thanks for your replies. Catfish looks good and is small. I don't know why it is not included in lubuntu by default.

---

