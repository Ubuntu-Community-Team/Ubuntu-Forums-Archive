---
title: "Random files being clobbered by browser-related databases"
date: 2011-08-05
forum: General Help
---

### Post by teich on 2011-08-05
Where to start? This is an odd one.  Over the last several days I've seen five apparently random files on my hard disk turn into Firefox & Chrome databases.

System details below. I'm on Ubuntu 10.04.


========================================
== Firefox-related corruptions
========================================

First, a .o file turned into a SQLite database containing "moz" and "formhistory"; I assume this is formhistory.sqlite.

```

00000000 53 51 4c 69 74 65 20 66 6f 72 6d 61 74 20 33 00 |SQLite format 3.|
00000010 04 00 01 01 00 40 20 20 00 00 17 e7 00 00 01 4f |.....@ .......O|
00000020 00 00 00 65 00 00 00 1d 00 00 00 03 00 00 00 01 |...e............|
00000030 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00 02 |................|
00000040 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00000050 00 00 00 00 00 00 00 00 00 00 00 00 00 00 17 e7 |................|
00000060 00 2d e2 1c 0d 00 00 00 03 02 3d 00 03 37 02 c3 |.-........=..7..|
00000070 02 3d 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |.=..............|
00000080 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
00000230 00 00 00 00 00 00 00 00 00 00 00 00 00 81 03 03 |................|
00000240 07 17 49 2b 01 81 1f 69 6e 64 65 78 6d 6f 7a 5f |..I+...indexmoz_|
00000250 66 6f 72 6d 68 69 73 74 6f 72 79 5f 6c 61 73 74 |formhistory_last|

```

Second, the file ~/.local/share/gnome-do/plugins/addin-db-001/fdb-lock became a SQLite database, version 10, containing URLs that I visited when using Firefox.

```

$ hd fdb-lock | head
00000000 53 51 4c 69 74 65 20 66 6f 72 6d 61 74 20 33 00 |SQLite format 3.|
00000010 10 00 01 01 00 40 20 20 00 00 07 88 00 00 0f 71 |.....@ .......q|
00000020 00 00 0b 17 00 00 00 73 00 00 00 19 00 00 00 01 |.......s........|

```

Perhaps this is places.sqlite, as file (the program) reports that this is the only SQLite file that Firefox maintains that is user version 10.

Third, my .bashrc turned into what I believe is cookies.sqlite.

```

$ hd .bashrc | head -n11
00000000 53 51 4c 69 74 65 20 66 6f 72 6d 61 74 20 33 00 |SQLite format 3.|
00000010 04 00 01 01 00 40 20 20 00 00 07 fa 00 00 02 8b |.....@ ........|
00000020 00 00 01 3a 00 00 00 20 00 00 00 01 00 00 00 01 |...:... ........|
00000030 00 00 00 00 00 00 00 00 00 00 00 01 00 00 00 02 |................|
00000040 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
00000050 00 00 00 00 00 00 00 00 00 00 00 00 00 00 07 fa |................|
00000060 00 2d e2 1c 0d 00 00 00 01 03 31 00 03 31 00 00 |.-........1..1..|
00000070 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
00000330 00 81 4c 01 07 17 23 23 01 82 5f 74 61 62 6c 65 |..L...##.._table|
00000340 6d 6f 7a 5f 63 6f 6f 6b 69 65 73 6d 6f 7a 5f 63 |moz_cookiesmoz_c|

```

========================================
== Chrome-related corruptions
========================================

First, I found an apparently random text file with some of my notes became an exact copy of Last Tabs, confirmed with diff.

```
$ hd 02-04-2011.txt | head
00000000 53 4e 53 53 01 00 00 00 11 00 04 02 00 00 00 01 |SNSS............|
00000010 00 00 00 d5 d2 88 0b 13 08 2e 00 ed 00 01 e8 00 |................|
00000020 00 00 02 00 00 00 00 00 00 00 10 00 00 00 63 68 |..............ch|
00000030 72 6f 6d 65 3a 2f 2f 6e 65 77 74 61 62 2f 07 00 |rome://newtab/..|
00000040 00 00 4e 00 65 00 77 00 20 00 54 00 61 00 62 00 |..N.e.w. .T.a.b.|
00000050 00 00 a8 00 00 00 a4 00 00 00 0a 00 00 00 20 00 |.............. .|
00000060 00 00 63 00 68 00 72 00 6f 00 6d 00 65 00 3a 00 |..c.h.r.o.m.e.:.|
00000070 2f 00 2f 00 6e 00 65 00 77 00 74 00 61 00 62 00 |/./.n.e.w.t.a.b.|
00000080 2f 00 20 00 00 00 63 00 68 00 72 00 6f 00 6d 00 |/. ...c.h.r.o.m.|
00000090 65 00 3a 00 2f 00 2f 00 6e 00 65 00 77 00 74 00 |e.:././.n.e.w.t.|

```

Second, an apparently random image file turned into something that starts with SNSS and has a number of URLs that I've visited recently in it, among other things. I'm not sure what this one is, but the only other files I can find starting with SNSS are {Current, Last} {Session, Tabs} in Chrome, so presumably it is one of those.


```
00000000 53 4e 53 53 01 00 00 00 11 00 04 01 00 00 00 01 |SNSS............|
00000010 00 00 00 2a 39 45 8c da 07 2e 00 05 a5 01 00 a5 |...*9E..........|
00000020 00 00 01 00 00 00 00 00 00 00 16 00 00 00 68 74 |..............ht|
00000030 74 70 3a 2f 2f 77 77 77 2e 67 6f 6f 67 6c 65 2e |tp://www.google.|

```

========================================
== Other notes
========================================

* I've been searching for additional corrupted files with {{{for file in `find -type f -ctime -20`; do echo $file `hd $file | head -n1` | grep SNSS; echo `file $file` | grep SQL; done}}}. Nothing else has come up.
* I've been searching for non-browser-related corruptions with {{{find -type f -ctime -1}}} or similar; there are a lot of changes, but nothing is obviously a corruption. Also, I keep a large portion of my data synchronized with unison, and two of the above corruptions were found by unison; nothing else has come up while synchronizing.
* Some of the corrupted files I touch a lot (.bashrc, gnome-do fdb-lock), and others I haven't touched in ages.
* I've seen about one clobbered file produced per day in the last few days.
* Chrome was updated on 7/26, and the first corruption I saw was on 7/30. I don't use Chrome that frequently, so it's possible that 7/30 was the first time I had used it since the update. Synaptic: google-chrome-stable (12.0.742.112-r90304) to 12.0.742.124-r92024
* Last Firefox update was 7/04.
* rkhunter and chkrootkit don't report anything particularly concerning. They both spit out a number of "suspicious" files, out of date programs, etc., but I get similar warnings on another Ubuntu machine that is not experiencing symptoms.
* My taskbar has mysteriously become small and moved to the top left of the desktop.
* fsck: At some point during the last few days as this has been evolving, fsck ran on startup, said something about drive errors and /tmp not ready yet or not present. Unfortunately I didn't get the details. Just now I've tried it manually, and it reports no errors.


========================================
== System details
========================================

I'm on Ubuntu 10.04, Firefox 3.6.18.

```

$ uname -a
Linux ferox 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 x86_64 GNU/Linux

```

```
Google Chrome 13.0.782.107 (Official Build 94237)
OS Linux
WebKit 535.1 (branches/chromium/782@91776)
JavaScript V8 3.3.10.22
Flash 10.3 r181
User Agent Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/13.0.782.107 Safari/535.1
Command Line /usr/bin/google-chrome --flag-switches-begin --flag-switches-end
Executable Path /opt/google/chrome/google-chrome
Profile Path /home/teichman/.config/google-chrome/Default

```

========================================
== So...
========================================

Clearly, I'm going to wipe the system clean and start over.... but this is so completely bizarre and mysterious that I cannot bring myself to wipe the evidence without figuring out what is going on first.

What could this be? Hypotheses:
* Bug or corruption in a program or shared library that both Chrome and Firefox use
* A malfunctioning SSD
* Bug in one of Chrome or Firefox, which also happens to sniff around in the other browers' data, and somehow accidentally sprays these files randomly around the hard disk
* Hackers

Do you have additional hypotheses? Thoughts on further tests I should run?

---

### Post by AlphaLexman on 2011-08-05
What do you get if you run 'file' on the infected files?
```
file ~/.bashrc
```

---

### Post by teich on 2011-08-05
In the order of the original post (first three are from Firefox, last two are from Chrome):

```


$ file brute.o 
brute.o: SQLite 3.x database, user version 2

$ file addin-db-001/fdb-lock 
addin-db-001/fdb-lock: SQLite 3.x database, user version 10

$ file .bashrc
.bashrc: SQLite 3.x database, user version 2

$ file 02-04-2011.txt 
02-04-2011.txt: data

$ file Screenshot-Untitled\ Window.png 
Screenshot-Untitled Window.png: data


```

---

### Post by AlphaLexman on 2011-08-05
That's NOT right!!

Look at 'top' and 'ps ax' for any weirdness

---

### Post by AlphaLexman on 2011-08-05
I googled the chrome snss filetype and got this: [http://virus-com.com/viruscom/viruscom_88446.html]("http://virus-com.com/viruscom/viruscom_88446.html")

---

### Post by teich on 2011-08-06
Fortunately snss.exe does not appear to have anything to do with Chrome or Ubuntu.

The SNSS files I'm referring to are those that begin with "SNSS":

```

$ hd 02-04-2011.txt | head
00000000  53 4e 53 53 01 00 00 00  11 00 04 02 00 00 00 01  |SNSS............|
00000010  00 00 00 d5 d2 88 0b 13  08 2e 00 ed 00 01 e8 00  |................|
00000020  00 00 02 00 00 00 00 00  00 00 10 00 00 00 63 68  |..............ch|
00000030  72 6f 6d 65 3a 2f 2f 6e  65 77 74 61 62 2f 07 00  |rome://newtab/..|
00000040  00 00 4e 00 65 00 77 00  20 00 54 00 61 00 62 00  |..N.e.w. .T.a.b.|
00000050  00 00 a8 00 00 00 a4 00  00 00 0a 00 00 00 20 00  |.............. .|
00000060  00 00 63 00 68 00 72 00  6f 00 6d 00 65 00 3a 00  |..c.h.r.o.m.e.:.|
00000070  2f 00 2f 00 6e 00 65 00  77 00 74 00 61 00 62 00  |/./.n.e.w.t.a.b.|
00000080  2f 00 20 00 00 00 63 00  68 00 72 00 6f 00 6d 00  |/. ...c.h.r.o.m.|
00000090  65 00 3a 00 2f 00 2f 00  6e 00 65 00 77 00 74 00  |e.:././.n.e.w.t.|

```

---

