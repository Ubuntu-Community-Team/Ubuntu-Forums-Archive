---
title: "Updating WINE from ppa"
date: 2010-02-10
forum: General Help
---

### Post by kolo-01 on 2010-02-10
Hi,
I have uploaded a newer edition of WINE through a ppa to 'sysyem-admin-software sources', but would like to know how to update wine so that it utilises this ppa upgrade as i cannot get linux to recognise the update. hope you can help, many thanks.

---

### Post by jken146 on 2010-02-10
Does ```
sudo apt-get update
``` return any errors?

If not, does ```
sudo apt-get upgrade
``` do anything with wine?

---

### Post by kolo-01 on 2010-02-10
hi,

in the end i found that you can put ppa's in the synaptic package manager, press refresh, then mark for install and it will update it that way, thanks for your reply though

---

