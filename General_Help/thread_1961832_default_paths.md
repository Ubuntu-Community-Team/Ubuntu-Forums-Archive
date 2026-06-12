---
title: "default paths"
date: 2012-04-19
forum: General Help
---

### Post by geiserich on 2012-04-19
Hi guys! My problem in short. It seems, any application can't locate any files by default. I mean, eg. start a media player, transmission, etc... ,it can't locate files (eg. a saved playlist) automatically. If i browse the full path, it works.
The error occured after the battery completly discharged, and the laptop switched off. After restart, the disk tests ran without any errors.
Also the bookmarks in places menu is messed, it shows the content of  ~/.gtk-bookmarks file directly as menu entries. 
I run lucid.
Any suggestions?

---

### Post by matt_symes on 2012-04-20
Hi

Please post the output of

```
echo $PATH
```This is mine```


matthew@matthew-Aspire-7540:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
matthew@matthew-Aspire-7540:~$
```You will not have lightdm as i am using Precise.

Check your paths first.

Also, please post the output of

```
cat ~/.gtk-bookmarks
```Here is mine

```
matthew@matthew-Aspire-7540:~$ cat ~/.gtk-bookmarks
file:///home/matthew/Documents
file:///home/matthew/Music
file:///home/matthew/Pictures
file:///home/matthew/Videos
file:///home/matthew/Downloads
matthew@matthew-Aspire-7540:~$
```

Kind regards

---

### Post by geiserich on 2012-04-20
Hi!

PATH seems ok to me:
```

gszabo@zion:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/mcnpx/bin:

```


~/.gtk-bookmarks content:
```

gszabo@zion:~$ cat /home/gszabo/.gtk-bookmarks 
<?xml version="1.0"?>
<gconf>
	<entry name="current" mtime="1334745626" type="string">
		<stringvalue>/usr/bin/metacity</stringvalue>
	</entry>
	<entry name="default" mtime="1333052880" type="string">
		<stringvalue>/usr/bin/metacity</stringvalue>
	</entry>
</gconf>

```

As i mentioned, this appears as menu entries in places menu and nautilus windows. I've made a screenshot.

Thanks!

---

### Post by matt_symes on 2012-04-20
Hi

Your .gtk-bookmarks file is corrupted. It needs to look like mine (i.e. same format). 

Make a backup of your existing file and then change so it is the same format as mine.

ie 

```
file:///path/to/folder
```As for your paths, they look fine. Fix the above issue with Nautilus and then we will have a look at the second issue. Make sure the two are not connected by checking to see if apps can find files after fixing the .gtk-bookmarks file.

Kind regards

---

