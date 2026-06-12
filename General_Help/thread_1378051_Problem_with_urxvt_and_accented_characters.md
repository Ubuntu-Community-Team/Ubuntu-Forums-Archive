---
title: "Problem with urxvt and accented characters"
date: 2010-01-10
forum: General Help
---

### Post by gnuvince on 2010-01-10
Hello everyone,

I installed Ubuntu Server 9.10 amd64 on my laptop this weekend.  During installation, I accidentally selected C as my preferred locale instead of English.

In my window manager (Openbox), when I open a urxvt terminal and try to type accented characters (é, è, à, etc.) they do not appear and when I cat a file with accents, they display incorrectly, as if I were in ISO-8859-1.

However, if I start urxvt from another urxvt, accented characters work without any problem, and displaying them works great too.

Can anyone tell me in which file I can change the C locale global setting?  And can anyone explain why launching from the Openbox menu causes my term to be in the wrong encoding?

Thanks,

Vincent.

---

