---
title: "Convert VBR to CBR"
date: 2006-03-17
forum: General Help
---

### Post by souled on 2006-03-17
Hello. I am in need of a program that will mass convert VBR mp3's to CBR. If possible, I would like to be able to tell easily if an mp3 is VBR or CBR. I can't really find a program that will do this. Does anyone know of any?

---

### Post by luna6 on 2006-03-17
soundconverter (gnome) or soundkonverter (kde) will do the mass convert from vbr to cbr, but curious why you would want to do that? The soundquality will take a significant hit from the conversion.
I don't know of a program that will tell you if if everything is vbr or cbr, but of course you can play the song in a program like xmms and see if the bitrate changes. Another way you could check is to use Amarok, right click at the top column bar and add "Bitrate" to the column tables, then you will see a list of the bitrates for all your music. Not 100% accurate but most of the variable bit rate files should have something other then 128, 160, 192, 256, or 320....

---

### Post by dpaint4 on 2006-03-17
It's a really really bad idea to do that. It'd be better to re-encode to CBR from source, but it's also be a better idea not to do it at all, and to be happy that you have some nice, good quality VBR files.

Converting them to CBR is like making a photocopy of a photocopy, with two generations of loss. Also, VBR is proven to be more efficient and sound better than CBR for the same file size.

I can't think of anything that dosen't support VBR, if that's your concern. You should post and explain why you think you need to do this, and people will probably be able to explain to you why you really don't need to.

---

### Post by souled on 2006-03-17
My phone doesn't support VBR. That's why I want to do this.

---

### Post by Jose Catre-Vandis on 2007-06-03
> **dpaint4 said:**
> I can't think of anything that dosen't support VBR, if that's your concern. You should post and explain why you think you need to do this, and people will probably be able to explain to you why you really don't need to.

The icecast server from the repos doesn't like VBR encoded mp3

It's the finding of the vbr ones in your collection that's the fun part :-)

---

