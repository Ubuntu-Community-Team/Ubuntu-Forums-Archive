---
title: "Mplayer problems"
date: 2006-05-30
forum: General Help
---

### Post by souteneur3190 on 2006-05-30
[http://www.phaeronix.net/patch/mplayer](http://www.phaeronix.net/patch/mplayer)

That is wherei got the mplayer GTk 2 plugin from, now where do i put it?  I need to know exacly which file to edit.

---

### Post by hw-tph on 2006-05-30
There is no plugin that I can see on that page. There is, however, a patch for mplayer that will enable arabic font shaping.

Untar the mplayer sources, enter the mplayer source directory and apply the patch (usually **cat filename.patch | patch -p0** or **-p1**). Then configure and build mplayer as usual. It appears you will need to pass --enable-arabic-shaping in order for the patch to actually have any effect. There is a [forum howto](http://www.ubuntuforums.org/showthread.php?t=85190) on how to build mplayer from CVS if you're not comfortable with building from source. Just ignore the CVS parts of it and grab the mplayer sources that match the version the patch is to be used against (i.e. get the mplayer 1.0pre7 sources if you want to use the patch for 1.0pre7) from the [mplayer homepage](http://www.mplayerhq.hu).


Håkan

---

