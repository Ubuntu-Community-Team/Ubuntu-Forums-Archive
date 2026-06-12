---
title: "Edit Root Files?"
date: 2010-06-15
forum: General Help
---

### Post by GrantStoner on 2010-06-15
I'm wondering how to go about editing files where the "owner" is root. I have a few files I've opened, edited, and clicked the "close" button - it's at this point it asks me to "save as", so I do. Then I tell it to replace the existing one, but it comes up with an error telling me I can't because I don't have the permissions to change the file. How do I edit a file as root?

---

### Post by oldos2er on 2010-06-15
Which editor are you using? If it's gedit, use ```
gksu gedit /etc/foo
```

---

### Post by GrantStoner on 2010-06-15
Thaks, this is exactly what I was looking for. When I read this I hit myself on the forehead *coulda had a v-8*

---

### Post by Iowan on 2010-06-15
If it's **nano**, this should work just fine:```
sudo nano /etc/foo
```

---

### Post by GrantStoner on 2010-06-15
Thanks, but I am using gedit. Is nano just another text editor?

---

### Post by oldos2er on 2010-06-16
nano is a CLI text editor.

---

