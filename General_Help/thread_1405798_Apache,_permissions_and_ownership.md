---
title: "Apache, permissions and ownership"
date: 2010-02-13
forum: General Help
---

### Post by niiize on 2010-02-13
Hi
How shell I make Apache have proper permissions to write to the www catalogue. What I need is to have apache beeing able to work within the www catalogue freely.

Right now I have set the whole www directory recursively to the 755 permission, and the ownerships of it I'm not sure to whom I shall give.. 
Right now I set it to root using supercommand *chown -R root www*

The webpage itself dispays a php-error saying: fwrite(): reason permission denied.

Thnx

---

### Post by rnerwein on 2010-02-13
hi 
open a terminal and tpye: ps -ef | grep http ( or what apache is running ).
i am not sure, but i think it's running the user "nobody".
ciao

---

