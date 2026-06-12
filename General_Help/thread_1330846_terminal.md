---
title: "terminal"
date: 2009-11-18
forum: General Help
---

### Post by rbee on 2009-11-18
Copied / paste into terminal but forgot how to install--can some explain how?

---

### Post by Zoot7 on 2009-11-18
Can you provide more information please? What is it you're having trouble with? Installing Stuff?

---

### Post by rbee on 2009-11-18
I can play most dvd's but when trying to play "TRANPORTER 3" I get the message "NO URI HANDLER IMPLIMENTED FOR DVD" so I thought I needed more restricted ???? I found an  answer in the Ubuntu forum  and copied and pasted that fix into terminal but ran into another problem---how to install.  The begining of this fix starts with sudo wget then message

---

### Post by Zoot7 on 2009-11-18
Have you got a link to the fix?

You should be able to play pretty much all Dvds if you use VLC, which can be installed by using the software centre. That's assuming you're using Ubuntu 9.10.

---

### Post by JBAlaska on 2009-11-18
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by rbee on 2009-11-18
i am using vlc player with all codecs, do play dvd's but with the dvd Transporter3 iget the message  "no uri handler for dvd"---could be a bug?

---

### Post by Zoot7 on 2009-11-18
Is the DVD a different region?

---

### Post by benj1 on 2009-11-18
> **Zoot7 said:**
> Is the DVD a different region?

shouldn't matter unless you have a 'legal' decoder

---

