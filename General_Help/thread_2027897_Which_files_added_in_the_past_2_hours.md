---
title: "Which files added in the past 2 hours?"
date: 2012-07-17
forum: General Help
---

### Post by PDA1 on 2012-07-17
How can you determine which files have been downloaded to your computer in the past 2 hours if you don't know the names of the files or where they might have been placed?

---

### Post by F W Adams on 2012-07-17
I think you need to use the terminal for that and the find command.

Open a terminal, Applications->Accessories->terminal under gnome.

Type in:

```
man find
```

to get the manual, or more precisely this seems to do it:

```
find -cmin 120
```

---

### Post by steeldriver on 2012-07-17
I think you would probably want -mmin rather than -cmin but I may be wrong about that; also to get results **newer** than 120 minutes the syntax is -mmin **-**120

If the file really could be anywhere (i.e. system dirs as well as user dirs) then you're probably going to need to search right from the filesysem root (i.e. / ) in which case you're going to get a LOT of results - you probably want to 'prune' things like /proc and /sys and you will need to be sudo if you think the file may in a user-unreadable directory

Something like this will find and then do a 'ls -l' so you can check the timestamps + ownership:

```
sudo find / \( -path '/proc/*' -o -path '/sys/*' -o -path '/run/*' \) -prune -o \( -type f -mmin -120 \) -exec ls -l {} \; 2>/dev/null
```Really it all depends on WHY you need to find it (is it just a regular download - or do you suspect something malicious?) and WHO/HOW it was downloaded ( was it with super user privileges e.g. a sudo apt-get or sudo wget?)

---

