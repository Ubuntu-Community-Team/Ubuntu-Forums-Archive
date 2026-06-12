---
title: "ubuntu 9.04 root-owned-directories! how to copyinto or delete files/directories?"
date: 2009-10-03
forum: General Help
---

### Post by yellowtab.org on 2009-10-03
how to install a new font if font-file is available? in which directory to copy it? and overall how to copy/delete files in root-owned directories anyway?
 
is there a way to login as root in ubuntu?

---

### Post by akakingess on 2009-10-03
there is not a way to log in as root (not that is mentionable on the forums for security reasons, anyway), but if you need temporary root control, you can run commands with the word "sudo" without the quotes, obviously, before the command, at which point it will ask for your password/root password. This again is all for security and to keep a lot of mistakes being made so be forwarned, but if you wanted to copy something to a folder owned by root, I believe sudo cp filetobemoved directorywhereyouwantit would suffice.

---

### Post by hal10000 on 2009-10-03
> how to install a new font if font-file is available?
There is an invisible directory called /home/yourname/.fonts in your home-diretory, where all your own fonts can be copied without root access

btw. you should avoid to delete files or drectories owned by root if you don't know **exactly** what you are doing. You might mess up your whole system.

---

