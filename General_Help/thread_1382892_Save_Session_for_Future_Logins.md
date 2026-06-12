---
title: "Save Session for Future Logins"
date: 2010-01-16
forum: General Help
---

### Post by kbot on 2010-01-16
I have a few questions related to the 'Save Session for Future Login' option you can check (and is checked by default) when you go to shutdown/restart/etc. 

1) What exactly does checking this option and shutdown/restarting do?

2) Is there any way to have it unchecked by default?

3) Is there any way to completely remove the option?

Thanks!

---

### Post by Brandon Williams on 2010-01-16
The XFCE session manager will "remember" the applications that are left running when you logout if you click "Save Session for Future Login". Those applications will be restarted automatically the next time you log in. If you uncheck the box once, then it should be unchecked every time unless, at some point in the future, you check the box again on logout.

You can open the 'Session and Startup' configuration dialog and the 'Prompt on Logout' box. However, this simply makes the logout dialog stop appearing altogher. There is no way to make the logout dialog show up without the checkbox on it except by choosing to automatically save sessions. So if you don't want to save sessions and you do want to see the logout dialog, then you will just have to accept the presence of the checkbox.

---

