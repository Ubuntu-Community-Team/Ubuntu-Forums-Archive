---
title: "Do not persist changes"
date: 2010-06-10
forum: General Help
---

### Post by zelkova on 2010-06-10
Hi everybody, I would like to know how to make it so that a limited user profile does not persist changes that are made to its desktop/interface during any given session.  

To help with this, I'l explain why I need this. Im a tech assistant working in a school and we allow the students to use limited accounts, which are more than enough to get  their work done. However, sometimes students will for example, drag the taskbar below the sight of the monitor and cause havok for the rest of the students who cannot find their programs. How can this be avoided.

---

### Post by Rubi1200 on 2010-06-10
Hi,
I am not sure what type of setup you have there, but it might be worth checking out sabayon and pessulus. Both are available via the Ubuntu Software Center and are used to configure desktop settings etc in a kiosk-like environment.

Hope this helps.

---

### Post by WorMzy on 2010-06-10
A possible solution would be to use chmod to change the permissions on the contents of the home folder. Setting them to to 555 would grant read and execute privileges to everyone, but no one would have write permissions. Just remember to change the permissions of documents and document folders back to 755, or else they won't be able to save their work.

---

### Post by zelkova on 2010-06-24
Aright, thanks for the help. Il go ahead and try it.

---

