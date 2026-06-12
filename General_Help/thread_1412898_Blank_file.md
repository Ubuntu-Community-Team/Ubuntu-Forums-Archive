---
title: "Blank file?"
date: 2010-02-21
forum: General Help
---

### Post by eminembdg on 2010-02-21
If I open a system file, specifically I need to open alsa-base.conf, with sudo the file is blank?

But if I open it and it&#347; read only then I CAN see whats written. Very odd, or maybe im just really missing something. 

Words are there in read only mode, no words there if I open it for editing.

Anyone know what&#347; going on? Thanks in advance for any help

---

### Post by eminembdg on 2010-02-21
just an update. Ive tried changing themes , thinking that maybe the text color was white on white background, but thats not the case. 

Also tried highlighting all text and that doesnt help either. The text just doesnt exist in the editor with sudo command.....

---

### Post by eminembdg on 2010-02-21
and it being moved to alsa-base.conf is not the problem. No matter what .conf file i open with the sudo command with gedit or using terminal the file is blank

---

### Post by falconindy on 2010-02-21
Maybe you should post how you're opening the file...

---

### Post by mr clark25 on 2010-02-21
you might try doing it all via a GUI.

```

gksu nautilus

```

try to find it graphicly and see if the contents are there.


you may have had a typo in the filepath somewhere.

---

### Post by eminembdg on 2010-02-21
> **mr clark25 said:**
> you might try doing it all via a GUI.

```

gksu nautilus

```

try to find it graphicly and see if the contents are there.


you may have had a typo in the filepath somewhere.

YAY! That seemed to work. I can now open the alsa-base.conf and see it , now to see if I can edit it. But at least I can see it lol.

Thank you Thank you Thank you so much

---

### Post by eminembdg on 2010-02-21
> **mr clark25 said:**
> you might try doing it all via a GUI.

```

gksu nautilus

```

try to find it graphicly and see if the contents are there.


you may have had a typo in the filepath somewhere.

could you real quickly explain what the command gksu is please?

EDIT**** Nevermind, I did a google search and found my answer. Again thank you for quick and short reply to my problem

---

