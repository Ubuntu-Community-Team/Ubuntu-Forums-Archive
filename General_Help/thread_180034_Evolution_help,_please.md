---
title: "Evolution help, please"
date: 2006-05-21
forum: General Help
---

### Post by drfox on 2006-05-21
A couple days ago, Evolution started freezing on my POP password screen. When I close the screen, the entire program closes. I thought it might have been an upgrade, but this am I upgraded to the latest version, and the same thing is happening, and now I think that my data got corrupted.  ](*,) 

Is there a utility that will allow me to rebuild my data?

Thanks, Larry

---

### Post by henriquemaia on 2006-05-21
[quote=drfox]A couple days ago, Evolution started freezing on my POP password screen. When I close the screen, the entire program closes. I thought it might have been an upgrade, but this am I upgraded to the latest version, and the same thing is happening, and now I think that my data got corrupted.  ](*,) 

Is there a utility that will allow me to rebuild my data?

Thanks, Larry[/quote]

I don't think so, and you'll have to do it by hand. Rename the .evolution folder to something else and create a new one with that name (.evolution). Than import things from the other folder (i.e. the renamed one).

To import, just go the preferences menu on evolution, go to Mail Accounts, choose Add, create a temporary account, giving it a suggestive name and using as Server Type select Maildir-format mail directories. Just create phony entries for everything else to get it going. After that, you'll see the entry on the side pane and you can take everything out of the old folders.

Hope this helps.

---

### Post by drfox on 2006-05-21
Perfect, Henrique. Thanks so much! Obrigado!

Larry

---

