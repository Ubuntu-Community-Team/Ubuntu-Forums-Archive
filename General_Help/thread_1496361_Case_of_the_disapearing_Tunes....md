---
title: "Case of the disapearing Tunes..."
date: 2010-05-29
forum: General Help
---

### Post by jv2112 on 2010-05-29
Since my last install of Linux Mint 9 I have ripped a # of CD's using Banshee & Rythhmbox. They turn out fine & I can listen to them. 

Then later same day or days later the mp3 files disappear. The folders & album art is still in place though. I have also seen prior rips to this OS install go off to never never land as well.

At first I thought it was my wife just doing in error but I have also seen when nobody had access to the machine.....

 ... Is there a ghost of deceased penguin in my box......... ...am I insane.... or is there a bug out there...  :confused: :mad::(

---

### Post by eev2 on 2010-05-29
Have you tried a search? Like find / -name "*.mp3"

---

### Post by mjneil.81 on 2010-05-29
i have alot of albums on a 500 Gb external drive and have noticed the same thing happening to me but i located the missing files in a folder called "found.000".
it seems as if the files are being sorted....maybe we share a similar problem?

---

### Post by WorMzy on 2010-05-29
Are you storing them on an NTFS partitions, and do you boot into Windows? Mjneil's suggestion of [found.000 folders]("http://techsalsa.com/what-are-found000-folders-and-why-are-they-created/") is worth considering. Linux allows certain characters to appear in filenames, which Windows doesn't. If chkdsk finds files with illegal characters, it'll rename them and move them to a found folder; if you don't run chkdsk, then the files will just be invisible (not hidden) on Windows.

---

### Post by mjneil.81 on 2010-05-29
worMzy's explanation seems to make sense to me cause at the time i used the drive on windows and ubuntu and since using the drive on ubuntu only no files have been moved around. mystery solved for me a least thanks for the info.

---

### Post by jv2112 on 2010-05-30
Yes.... They are just gobbled up :(

---

