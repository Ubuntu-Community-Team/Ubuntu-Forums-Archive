---
title: "apt-get problem &gt;:O!!"
date: 2006-05-09
forum: General Help
---

### Post by richard0012sX on 2006-05-09
when i do apt-get update or apt-get upgrade there's an error that says 

[http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz)  404 Not Found  

is the server down or what?

---

### Post by aysiu on 2006-05-09
[QUOTE=richard0012sX]
is the server down or what?[/QUOTE] Yes, the server's down.

---

### Post by deanjm1963 on 2006-05-09
seems the URL has changed

try this link

[http://theli.free.fr/packages/_breezy_obsoltete/Packages.gz]("http://theli.free.fr/packages/_breezy_obsoltete/Packages.gz")

hope this helps

---

### Post by richard0012sX on 2006-05-12
ok.. but what do i do with it?

---

### Post by brossatscu on 2006-05-12
1. Open the terminal
2. 'sudo gedit /etc/apt/sources.list' in terminal
3. Find the line with 'http://theli.free.fr/packages/breezy/'
4. Change it to 'http://theli.free.fr/packages/_breezy_obsoltete/'
5. Save
6. 'apt-get update' in terminal

Still have problems? Post new errors.

---

### Post by richard0012sX on 2006-05-12
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz)  404 Not Found

Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz)  404 Not Found

what's the new urls for those?

---

