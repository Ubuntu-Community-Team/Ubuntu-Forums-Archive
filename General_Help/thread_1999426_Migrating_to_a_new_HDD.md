---
title: "Migrating to a new HDD"
date: 2012-06-08
forum: General Help
---

### Post by Kain000 on 2012-06-08
Hey everyone, 
I am about to ship out to Afghanistan and just wiped my laptop for a fresh install of 12.04.  I've gotten all the packages and codexs' that I think I will need (many emulators lol) only to find that my laptop's hard drive is showing the first signs of failure. I ordered a new 1 TB seagate drive that will be here tomorrow and am in need of a migration solution.  I just want to basicly ghost my drive over to the new one including all files applications and tweaks included.  I've noticed the new backup feature included in 12.04 and without playing with it yet I assume it allows me to make an image? If this assumption is correct will that be my ticket? If not any suggestions?
Thanks alot
-Sean

---

### Post by kanikilu on 2012-06-08
I don't believe Deja Dup (backup tool in Ubuntu) will save an image.

My only cloning/imaging experience is a "one-to-many" scenario using udpcast. For a "one-to-one" clone, personally, I'd probably boot up with the Parted Magic ([http://partedmagic.com](http://partedmagic.com)) live CD/USB. From there, you can try the disk imaging with Clonezilla. 

You can also use the clonezilla live cd, but I already have the parted magic cd in my arsenal, so that's what I'd use.

For some examples using Clonezilla: [http://clonezilla.org/clonezilla-live-doc.php](http://clonezilla.org/clonezilla-live-doc.php)

If you're up to the challenge, you could always just boot up with any old Ubuntu live CD and use *dd*:

[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

Good luck!

---

### Post by Kain000 on 2012-06-09
Thanks so much, DD worked like a charm :)

---

