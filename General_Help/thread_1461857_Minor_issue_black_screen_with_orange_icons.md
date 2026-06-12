---
title: "Minor issue: black screen with orange icons"
date: 2010-04-24
forum: General Help
---

### Post by paulvic on 2010-04-24
About two of every three times I go to "Places" and then click on "Documents" or "Pictures" or whatever, I get a black screen with orange instead of a white screen.  None of the icons have titles, and clicking on them produces the same mess.

I have to close the window and start over, that is, go to Places, then Documents. 

Any way to avoid this?

Paul

---

### Post by garyedwardjohnston on 2010-04-24
Never heard of this...it might be a nautilus problem if it only happens there...try reinstalling it.

---

### Post by paulvic on 2010-04-25
> **garyedwardjohnston said:**
> Never heard of this...it might be a nautilus problem if it only happens there...try reinstalling it.

Yes, I suspect a Nautilus problem.  How do I reinstall?

Paul

---

### Post by ciaopaulo on 2010-04-25
You can reinstall via Synaptic Package Manager. Search for nautilus, click on the (green) box and select reinstall from the pop up menu.

Alternatively

$sudo apt-get remove --purge nautilus
$sudo apt-get install nautilus

from a terminal window.

---

### Post by paulvic on 2010-04-25
> **ciaopaulo said:**
> You can reinstall via Synaptic Package Manager. Search for nautilus, click on the (green) box and select reinstall from the pop up menu.

Alternatively

$sudo apt-get remove --purge nautilus
$sudo apt-get install nautilus

from a terminal window.


Okay, will do.  Thanks.

Paul

---

