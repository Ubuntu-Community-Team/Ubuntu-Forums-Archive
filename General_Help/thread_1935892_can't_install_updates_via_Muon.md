---
title: "can't install updates via Muon"
date: 2012-03-05
forum: General Help
---

### Post by princeofnam on 2012-03-05
I always get this error "This operation cannot continue since proper authorization was not provided"

I either have to sudo update via terminal or go into Ubuntu.  I have no idea why this occurs.  Does anyone have a fix?

---

### Post by whatthefunk on 2012-03-05
When you try to update via Muon, does it ask for your password?  Have you altered your sudoers file or turned off password protection for anything?

---

### Post by princeofnam on 2012-03-05
ah. solved. fixed it by installign the polkit-kde repository.

---

### Post by raja.genupula on 2012-03-05
Thats good news please mark the thread as solved from thread tools.

Thank you .

---

