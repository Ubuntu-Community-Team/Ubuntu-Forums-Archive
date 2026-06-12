---
title: "part01.rar ???"
date: 2009-07-13
forum: General Help
---

### Post by FetalShinobi on 2009-07-13
hey all i am running ubuntu 9.04 and im loving it. i just got an ebook that was split into two (filename.part01.rar and filename.part02.rar) i know that they have to be merged or whatever its called but im not sure on how to do it....can anyone please help? thank you :-)

---

### Post by PurposeOfReason on 2009-07-13
I'm skeptical that this is an ebook as many torrents for games are done in this fashion and ebooks are so small it isn't justified. To do it though, you just extract the first file in the list, IE
```

unrar e file01.rar

```

---

### Post by FetalShinobi on 2009-07-13
i dont bother with game torrents cause i dont have the hardware needed to burn the games and such. what i am is a little embarrased cause of the contents of the ebook lol. anyways it is a torrent but i dont understand why it was split cause its barely 20 mb. its a kama sutra book lol. anyways let me see if i get this straight i got these files,

kama sutra- ebook.nfo
kama sutra- ebook.sfv
kamasutra - sex positions (ebook).part1.rar
kamasutra - sex positions (ebook).part2.rar

do i still extract part one only and im fine?

---

### Post by jocko on 2009-07-13
> **FetalShinobi said:**
> i dont bother with game torrents cause i dont have the hardware needed to burn the games and such. what i am is a little embarrased cause of the contents of the ebook lol. anyways it is a torrent but i dont understand why it was split cause its barely 20 mb. its a kama sutra book lol. anyways let me see if i get this straight i got these files,

kama sutra- ebook.nfo
kama sutra- ebook.sfv
kamasutra - sex positions (ebook).part1.rar
kamasutra - sex positions (ebook).part2.rar

do i still extract part one only and im fine?
Yep. You may need to install the package unrar first:
```
sudo apt-get install unrar
```
Then any archive manager should be able to extract it for you. Just right click one of the .part*.rar files and choose "extract here", and both of them will be extracted.

---

### Post by FetalShinobi on 2009-07-13
thank you all done! :-D now how do i put this issue as solved? lol

---

### Post by doas777 on 2009-07-13
> **PurposeOfReason said:**
> I'm skeptical that this is an ebook as many torrents for games are done in this fashion and ebooks are so small it isn't justified. To do it though, you just extract the first file in the list, IE
```

unrar e file01.rar

```


It's not really bad content that is packaged that way, but stuff that started or ended on usenet. posters use that approach for multipart binaries because of the 1.5MB message limit. Not really an indication of illegal activity.

---

### Post by leguman on 2009-08-15
in xubuntu, a right-click suffices to extract, in ubuntu probably too

just need to have unrar intalled from the non-free repositories

---

