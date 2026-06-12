---
title: "Don't have a modules.conf."
date: 2006-01-20
forum: General Help
---

### Post by Protex on 2006-01-20
Hi guys.

I wanted to find my modules.conf to enable Fast Writes with my nVidia card, but with a search of the system, both manually, and automatically I cannot locate my modules.conf file.

From what I understand, it's supposed to be in /etc but it's not.

I have a 'modules' file, but no modules.conf. The modules file just has a list of things like:

lp
mousedev
psmouse
nvidia
amd74xx
ide-cd
ide-disk
ide-generic

Is this the file I'm looking for?

---

### Post by Protex on 2006-01-20
Never mind.

Found out that modules.conf is really the folder modprobe.d and I found the nVidia kernel file in there, and all is fine now. Thanks again!

---

### Post by fakie_flip on 2007-05-09
> **Protex said:**
> Never mind.

Found out that modules.conf is really the folder modprobe.d and I found the nVidia kernel file in there, and all is fine now. Thanks again!

What did you really mean? A folder and file are not the same. Would you explain better?

folder != file

---

