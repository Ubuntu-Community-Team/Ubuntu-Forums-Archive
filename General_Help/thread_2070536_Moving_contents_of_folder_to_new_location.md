---
title: "Moving contents of folder to new location"
date: 2012-10-13
forum: General Help
---

### Post by Herbon on 2012-10-13
Greeting all

  I'mtrying to move the contents of folders (mp3 file) to my Music folder.
When I run the command found below, I get  a "find: missing argument to `-exec'
" error

WTF

> find ./ -iname *".mp3" -exec mv {} ./home/imhotep/Music


---

### Post by papibe on 2012-10-13
Hi Mr_Imhotep.

Try this:
```
find ./ -iname **[COLOR="Red"]'*.mp3'[/COLOR]** -exec mv **[COLOR="Red"]'{}'[/COLOR]** ./home/imhotep/Music **[COLOR="Red"]\;[/COLOR]**
```

Let us know how it goes.
Regards.

---

### Post by Herbon on 2012-10-13
> **papibe said:**
> Hi Mr_Imhotep.

Try this:
```
find ./ -iname **[COLOR=Red]'*.mp3'[/COLOR]** -exec mv **[COLOR=Red]'{}'[/COLOR]** ./home/imhotep/Music **[COLOR=Red]\;[/COLOR]**
```Let us know how it goes.
Regards.

New error

> mv: cannot move `./repost Rasdragon VLS-12\'\' _7 [460+524] - \'Write Sounds WTS 1004-A Revelation - With You Boy.mp3\' yEnc (1+30)/Write Sounds WTS 1004-A Revelation - With You Boy.mp3' to `./home/imhotep/Music': No such file or directory


The folder's contents still remain.

---

### Post by Herbon on 2012-10-13
> **papibe said:**
> Hi Mr_Imhotep.

Try this:
```
find ./ -iname **[COLOR=Red]'*.mp3'[/COLOR]** -exec mv **[COLOR=Red]'{}'[/COLOR]** ./home/imhotep/Music **[COLOR=Red]\;[/COLOR]**
```Let us know how it goes.
Regards.

This works!

I had to remove "[COLOR=Red]**.**[/COLOR]" before "/home/imhotep/Music \;"

Thanks!!!!!!!!!!

---

### Post by papibe on 2012-10-13
:) glad is working!

---

