---
title: "Adobe Reader won't start after SCIM installed?"
date: 2006-03-27
forum: General Help
---

### Post by hell0un1verse on 2006-03-27
Hi there,

Here's the strange thing what has happened: I installed SCIM for Chinese input method, I think I installed the following packages, scim, scim-chinese, scim-config-socket, scim-frontend-socket, scim-gtk2-immodule, scim-server-socket, scim-tables-zh. They are the main SCIM packages plus dependencies. And the Adobe Reader is 7.1 version. After the installation, the reader just won't start, when trying to load it on command line with acroread, it just returns to command prompt.

I figured that it was due to the SCIM installation, and it proved to be true because after I deinstalled SCIM packages, acroread was back again.

Why is that?

Thanks for any input:)

---

### Post by hell0un1verse on 2006-03-27
Problem solved, it's one line added to /usr/bin/acroread: export GTK_IM_MODULE=xim

Should have searched forum first, this is a common problem:p

Sorry about this redundant posting.

---

