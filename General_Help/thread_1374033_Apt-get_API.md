---
title: "Apt-get API"
date: 2010-01-06
forum: General Help
---

### Post by Stas_Kh on 2010-01-06
Hi
Is it exist API to apt-get (or may be to aptitude or dpkg)?
For example I want to check through API does package installed or not?
Thanks

---

### Post by prem1er on 2010-01-06
I think you mean you want to see if a package is installed on your system? You can just open synaptic package manager and search in there.

---

### Post by Stas_Kh on 2010-01-06
> **prem1er said:**
> I think you mean you want to see if a package is installed on your system? You can just open synaptic package manager and search in there.
Thank you for the answer. I know about synaptic, but I want to check this through program (script) per [API]("http://en.wikipedia.org/wiki/Api").

---

### Post by slakkie on 2010-01-06
uhh.. dpkg -l <pacakgename> ?

Otherwise have a look at libapt :)

---

### Post by Stas_Kh on 2010-01-09
It seems I've found what I looked for: [http://search.cpan.org/~wilsond/Linux-APT-0.02/lib/Linux/APT.pm]("http://search.cpan.org/~wilsond/Linux-APT-0.02/lib/Linux/APT.pm")

---

