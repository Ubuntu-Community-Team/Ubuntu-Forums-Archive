---
title: "How to set folder read-only without its subfolders"
date: 2010-10-10
forum: General Help
---

### Post by griffonn on 2010-10-10
Hi,

I am looking for solution to set folder read-only excluding its subfolders, that means I cannot create new files/folders in current folder, but I can in subfolders. Is this possible and how?

Thanks in advance.

---

### Post by mike2357 on 2010-10-10
If I understand your question, it's pretty easy:

chmod 555 <folder_name>

Or from Nautilus, right-click on the folder, select Properties and then the Permissions tab.

To learn more about the "chmod" command, run "man chmod".  Instead of "chmod 555" you might prefer to use 550 or 500.

---

### Post by griffonn on 2010-10-10
ok, but if I do this, if the subfolders will be writable?

---

### Post by d.atanasov on 2010-10-10
> **griffonn said:**
> ok, but if I do this, if the subfolders will be writable?
Yes, very nice and elegant way is to change permissions by "chmod". I`ll advise you to do everything from terminal, where is a lot faster then "the folder way". :P

---

### Post by griffonn on 2010-10-10
Thank you all for answers.

I am working with remote server without ssh access, so I made that by their file manager.

---

