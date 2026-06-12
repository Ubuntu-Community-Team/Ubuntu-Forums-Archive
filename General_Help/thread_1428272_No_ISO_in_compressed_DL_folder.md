---
title: "No ISO in compressed DL folder"
date: 2010-03-12
forum: General Help
---

### Post by ifunky2 on 2010-03-12
Ok I am frustrated...

I am trying to create an Ubuntu install disk from a downloaded ISO.
Evrey time I have tried (3 or 4 times now) to DL the iso I get a compressed folder with a zillion files (including WUBI installer). However there is no actual iso in the compressed folder any where.
I have tried DL'n it from the direct link as a windows handled DL and I have DL'd it using BitTorrent.

I am trying to DL and burn the iso on a Window$ XP box. 
Could my problem be that my browser is auto detected and I get the wubi install DL?
Is WinRar messing with me?
Am I just lame and even though when I launch 'Infra Recorder' and it can't see any ISO's anywhere in the decompressed Ubuntu, install/iso download, there is a magic manner in which you burn the image that I just don't get?

I just want to install Ubuntu on an older box and play with it. Then I am thinking I might like to reformat my laptop and make it dual boot with ubuntu as default load.
But I can't even seem to figure out how to burn an install disk ?

---

### Post by sisco311 on 2010-03-12
Yep, WinRar is messing with you. :)

The compressed file you downloaded IS the .iso file. It's recognized by WinRar as an archive, but you DON'T have to extract it. Just use InfraRecorder to burn the image.

For detailed instructions, see:
[http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)

---

### Post by jocko on 2010-03-12
The "compressed folder" you talk about IS the iso. You probably run windows and have winrar installed? In that case the windows file associations are set to open .iso files with winrar (and the file will have an archive icon instead of a cd icon).

You should NOT unpack it, just tell your cd burning software to burn an image and when it asks for the file, browse to where you downloaded the iso.

If you don't believe me, just check the full name of the file you downloaded (you may need to set windows not to hide the extension).

---

### Post by ifunky2 on 2010-03-12
Coo guys:
Thankz for the quick response.
<Off to try those suggestions...

(post edit)

Yep got it.
I is dat lame-o.
Merely switching file handling in WinXp did the trick.
Got it burning now.

See maybe you guys have another convert from the darkside back too the light ;)

---

### Post by lisati on 2010-03-12
Have a look here: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

