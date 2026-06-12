---
title: "SFX rar"
date: 2010-01-17
forum: General Help
---

### Post by Chamillionaire2 on 2010-01-17
What's Up?

OK, So I'm trying to make a SFX file that will extract it's files your home folder, But I can't seem to figure out how.

First you have to make an archive,
```
rar a Zipper.zip txt.txt
```
Then you have to make the sfx.
```
rar s Zipper.zip
```

But they still get extracted wherever the sfx volume is.

Anyone know?

Thanks Bye.

---

### Post by jamesisin on 2010-01-17
I can't say specifically to your application.  I use 7zip.  The 7zip command looks like this:

7z x [file to extract] -o[path to extract into]

You can see more about this here:

[http://www.soundunreason.com/InkWell/?p=450](http://www.soundunreason.com/InkWell/?p=450)

---

