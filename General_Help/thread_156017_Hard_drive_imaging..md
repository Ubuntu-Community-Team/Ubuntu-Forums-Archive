---
title: "Hard drive imaging."
date: 2006-04-06
forum: General Help
---

### Post by sixteensix on 2006-04-06
Sorry if this is in the wrong place!

I have search through the forums, and done some googling but I haven't found what I am looking for... 

Has anybody come across a native disk imaging application for linux/ubuntu? I have used Ghost, Livestate and Trueimage on Windows but I have failed to find a similar application native to Linux.

Any help will be greatly appreciated.

Tim
Sixteensix

---

### Post by frodon on 2006-04-06
Just for infos, the latest release of norton ghost works with ubuntu (ext3 support) it's what i use because i prefer make make ghost with another OS.
Anyway what you're looking for is partimage i think : [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

### Post by gnu2tux on 2006-04-06
I'm sure that there are some GUI based apps out there for Linux, but to be honest, I think the old classic dd command is great:

```

sudo dd if=/dev/hda of=diskimage.img

```

That will take a complete, exact image of hda (ide disk 1) . if means input file, of means output file.

Do a man dd before using it, because it'll do what you tell it - including destroy your hard disk!

Al

---

### Post by kahping on 2006-04-06
[QUOTE=sixteensix]Sorry if this is in the wrong place!

I have search through the forums, and done some googling but I haven't found what I am looking for... 

Has anybody come across a native disk imaging application for linux/ubuntu? I have used Ghost, Livestate and Trueimage on Windows but I have failed to find a similar application native to Linux.

Any help will be greatly appreciated.

Tim
Sixteensix[/QUOTE]

You can use dd to do that. Personally, i've only used it for harddisk imaging once, and it took hours to image a 80GB harddisk :(

run from command line:

```
man dd
```

for more info on how this command works. Sorry, but since i've only used it once myself, i can't remember much about it. Also, i may have not used the command properly. In the hands of someone more experienced, it may not require such a long time to do a complete image :p

---

