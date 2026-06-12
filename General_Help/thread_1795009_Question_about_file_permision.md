---
title: "Question about file permision"
date: 2011-07-01
forum: General Help
---

### Post by theWman on 2011-07-01
I'm new to ubuntu, and I've been trying to get shockwave running on firefox using the instructions here: 

[https://help.ubuntu.com/community/Shockwave](https://help.ubuntu.com/community/Shockwave)

However, when i try to open firefox with wine, i get this message. 

"The file '/home/Downloads/Firefox Setup 5.0.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

i looked into this, but i don't understand what i'm doing well enough to assign file permission to this program. can anyone help me out here?

---

### Post by freebeer on 2011-07-01
Command line is easiest.

```

cd /home/Downloads
chmod +x /Firefox\ Setup\ 5.0.exe

```

I hope I didn't introduce any typos. :P

You can also do it the gui way.  Locate the file with your file manager, right click on Properties, then select the permissions tab.  You should then be able to toggle on the "execute" property from there.

---

### Post by linuxuser12345 on 2011-07-01
Wait, you shouldn't need Wine to run Shockwave. If I were you, I would remove Wine as it creates a security risk: It gives you system the chance to run viruses.

---

### Post by linuxuser12345 on 2011-07-01
> **freebeer said:**
> Command line is easiest.

```

cd /home/Downloads
chmod +x /Firefox\ Setup\ 5.0.exe

```I hope I didn't introduce any typos. :P

You can also do it the gui way.  Locate the file with your file manager, right click on Properties, then select the permissions tab.  You should then be able to toggle on the "execute" property from there.

Don't think he already knows about the terminal if he is new to Ubuntu.

Do this: Right-click on the file, go to "Properties", then "Permissions". Click "Mark file as executable". You should be good to go!

But still, if you don't need Wine, remove it! Trust me, it is better to be safe than sorry! :)

---

### Post by nitstorm on 2011-07-01
> **freebeer said:**
> Command line is easiest.

```

cd /home/Downloads
chmod +x /Firefox\ Setup\ 5.0.exe

```

I hope I didn't introduce any typos. :P

You can also do it the gui way.  Locate the file with your file manager, right click on Properties, then select the permissions tab.  You should then be able to toggle on the "execute" property from there.

Ummm... you forgot the $USER part after /home. Correcting the code,
```
cd ~/Downloads
chmod +x /Firefox\ Setup\ 5.0.exe
```

---

### Post by freebeer on 2011-07-03
> **nitstorm said:**
> Ummm... you forgot the $USER part after /home. Correcting the code,

oops. my bad.  Thanks for correcting it!  :oops:

---

### Post by nerdy_kid on 2011-07-03
isn't shockwave the same thing as flash (which doesn't need wine..)?

---

