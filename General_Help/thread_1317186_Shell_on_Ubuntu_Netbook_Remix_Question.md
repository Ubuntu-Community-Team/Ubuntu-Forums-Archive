---
title: "Shell on Ubuntu Netbook Remix Question"
date: 2009-11-06
forum: General Help
---

### Post by lancevo3 on 2009-11-06
Hey Guys,

I recently installed ubuntu netbook and was having some trouble running a script I wrote that was written for bash. I was wondering what shell does the netbook remix have? And if I could change it to bash?

---

### Post by Brandon Williams on 2009-11-06
A standard ubuntu install (UNR included) will have both bash and dash. The default login shell will be bash, and /bin/sh will be dash. If the #! line in your script says to run it with /bin/bash, you should be fine. If the #! line says /bin/sh, you'll get dash.

---

