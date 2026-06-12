---
title: "Rhythmbox and ID3 tags"
date: 2009-07-15
forum: General Help
---

### Post by fwaokda on 2009-07-15
Rhythmbox works great and I just edited a few cds that were messed up, but when I went to load them to my mp3 player I noticed the edits only show up in Rhythmbox... so I assume it's not writing to the ID3 tags.  Is there a way I can transfer the information in Rhythmbox to the ID3 tags of the files? Through a plugin or another program that works with Rhytmbox or something? Thanks.

---

### Post by Kraut~salat on 2009-07-15
well, this is just a guess, but there are diferent versions if ID3 tags, i.e. ID3 and ID3v2

have you tried different programs like banshee or amarok?

---

### Post by fwaokda on 2009-07-15
I know Amarok and those will probably do it but I like Rhythmbox and want to use it.  Have not seen/heard of banshee yet though I'll look into it, and see. I was just hoping there was a plugin/software that would edit them with Rhythmbox. Thanks ;)

---

### Post by CatKiller on 2009-07-15
As I understand it, many media players keep metadata in their own database so that you can add arbitrary tags to media files - even those that don't have a mechanism for storing metadata themselves. Some media players will also write the tags to files that support them, but I don't think that most do (although Amarok, which is my preferred media player, does). Possibly this feature is already planned for implementation in Rhythmbox, but it's not something I've looked into. You could probably file a bug report requesting the feature if it isn't already planned. In the meantime, EasyTAG (which is in the repositories) is quite a useful tool for writing tags to your media files. It can, amongst other things, write tags based on the filename using the Scanner function.

---

### Post by fwaokda on 2009-07-15
Thanks I'm gonna try EasyTag out!

---

### Post by vinutux on 2009-07-16
> **fwaokda said:**
> I know Amarok and those will probably do it but I like Rhythmbox and want to use it.  [COLOR="Red"]Have not seen/heard of banshee yet [/COLOR]though I'll look into it, and see. I was just hoping there was a plugin/software that would edit them with Rhythmbox. Thanks ;)


Strange.........Banshee is the best music management app in gnome...far better than Rhythembox and amarok2...Try it

```
sudo apt-get install banshee
```

Banshee also able to efit ID3 to your mp3 (U want to eneble it in preferences..othervice it will keep data on local database not in mp3 file)



.

---

