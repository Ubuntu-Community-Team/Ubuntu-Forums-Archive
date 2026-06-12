---
title: "PLEASE help!"
date: 2006-01-29
forum: General Help
---

### Post by thepocketdrummer on 2006-01-29
Ok, I've tried two different ways to get Firefox working, and I still can't get it to work. I read the website on Ubuntu, but one is how to install 1.5 if you have an older version, and the site for 64-bit doesn't work.

When I typed this, it said, "permission denied"
```
mkdir /usr/local/firefox32
```

this installation is -->:evil: 

Can someone help me out or at least tell me how to get rid of /opt/firefox. I can navigate to it with Konqueror, but when I right click there isn't an delete option.

---

### Post by johannes on 2006-01-29
Have you tried [Automatrix]("http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatrix")? That worked fine for me. Use the one for Kubuntu.

If you use Automatrix you won't need to do it, but to make a folder in /usr/local/, you need to use "sudo":

```
sudo mkdir /usr/local/firefox32
```

To remove /opt/firefox, write:

```
sudo rm -rf /opt/firefox
```

---

