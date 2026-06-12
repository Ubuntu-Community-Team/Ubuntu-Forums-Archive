---
title: "Changing file encoding in Gedit"
date: 2011-12-03
forum: General Help
---

### Post by tamerucar on 2011-12-03
Hi,

How can I change the file encoding in Gedit? Kate has a simple option for that, but I couldn't find something like that for Gedit. And I don't believe that there isn't one. So maybe is it a system-wide setting?

---

### Post by mikewhatever on 2011-12-03
In Gedit, click the 'Open' button. A file browser window should open with encoding selection at the bottom.

---

### Post by tamerucar on 2011-12-03
> **mikewhatever said:**
> In Gedit, click the 'Open' button. A file browser window should open with encoding selection at the bottom.

Yes, I saw it but how do I set it as default? Because when I open files directly from nautilus, Gedit applies the default encoding which does not fit my need.

---

### Post by mikewhatever on 2011-12-03
Check out gconf-editor, /appt/gedit2/preferences/encodings. Try adding the desired encoding to the 'auto_detected' line.

---

### Post by tamerucar on 2011-12-04
> **mikewhatever said:**
> Check out gconf-editor, /appt/gedit2/preferences/encodings. Try adding the desired encoding to the 'auto_detected' line.

There is no "encodings" entry under /apps/gedit2/preferences/
Should I look under a different path?

---

### Post by mikewhatever on 2011-12-04
Sure, please do. 
I've checked gconf-editor on Lucid and Maverick should have the same options available, but given the overlay scrollbars in your screenshot, you probably run Oneric, don't you. I'll check my Oneiric installation as well.

---

### Post by tamerucar on 2011-12-05
> **mikewhatever said:**
> Sure, please do. 
I've checked gconf-editor on Lucid and Maverick should have the same options available, but given the overlay scrollbars in your screenshot, you probably run Oneric, don't you. I'll check my Oneiric installation as well.

Yes, I am using Ubuntu 11.10 Oneiric Ocelot. And I couldn't spot the "encodings" entry that you mentioned.

---

### Post by mikewhatever on 2011-12-06
Hm..., not sure why there is no 'encodings' for Gedit in your installation. Below is a screenshot of mine.

---

### Post by tamerucar on 2011-12-06
> **mikewhatever said:**
> Hm..., not sure why there is no 'encodings' for Gedit in your installation. Below is a screenshot of mine.

Did you take this screenshot from an 11.10 installation?

---

### Post by mikewhatever on 2011-12-06
Yes, of cause.

---

### Post by tamerucar on 2011-12-06
> **mikewhatever said:**
> Yes, of cause.

That's interesting.
Does anybody have any idea about this?

---

### Post by sakirasci on 2012-03-18
I also have Oneiric installed. I want Gedit to recognize Turkish texts (ISO 8859-9) as default but I don't have *encodings* directory either.

---

### Post by Vaphell on 2012-03-18
install **dconf-editor** and try again with it, afaik dconf is kosher now.

---

### Post by sakirasci on 2012-04-02
> **Vaphell said:**
> install **dconf-editor** and try again with it, afaik dconf is kosher now.

[B]dconf-editor>org>gnome>gedit>preferences>encodings:
[/B]
I added the value 'ISO-8859-9' to the beginning of auto-detected and ya&#351;as&#305;n! Now, it recognizes Turkish characters as default.
@Vaphell, thank you for dconf-editor suggestion :-)

---

