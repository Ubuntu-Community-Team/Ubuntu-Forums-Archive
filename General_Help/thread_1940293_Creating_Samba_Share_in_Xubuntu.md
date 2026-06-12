---
title: "Creating Samba Share in Xubuntu"
date: 2012-03-13
forum: General Help
---

### Post by AlphaLupi on 2012-03-13
Is it possible to create Samba shares in Xubuntu?

Is it just like doing it in stock Ubuntu, i.e. just editing /etc/samba/smb.conf?

---

### Post by Roasted on 2012-03-13
Pretty much. You could also hit up the basic Samba gui from the repos, known as system-config-samba. It's pretty nice for doing simple tasks like adding shares and setting who can access what.

---

### Post by Morbius1 on 2012-03-13
Once upon a time there was a package called thunar-shares-plugin that allowed you to do in Thunar what nautilus-share does in Nautilus - right click a file and say "share this folder". It was an implementation of Samba's Usershare that allowed any user to share anything he owned. 

Sadly, that package is gone now but you can still create Usershares from the command line and you can even create a Thunar Custom Action that comes part of the way to the way it used to work: [http://ubuntuforums.org/showpost.php?p=11505823&postcount=7](http://ubuntuforums.org/showpost.php?p=11505823&postcount=7)

---

### Post by AlphaLupi on 2012-03-13
Thanks guys, that exactly what I needed to know.

---

