---
title: "Ubuntu 9.04 Application Error"
date: 2009-09-02
forum: General Help
---

### Post by AngelTheOne on 2009-09-02
Hello i need some help everytime i try to add a application this error keeps coming up:
> 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Plz help :)

---

### Post by drs305 on 2009-09-02
Have you tried what it says:
Open a terminal (Applications, Accessories, Terminal) and type:
```

sudo dpkg --configure -a

```
It will ask for your password. You won't see it as you type. When finished typing, press ENTER.

*When your problem is solved, please mark the thread solved via the Thread Tools link near the upper right of the original post.*

---

### Post by AngelTheOne on 2009-09-02
Ok thanks it works may i ask how i accesses the application now?

---

### Post by drs305 on 2009-09-02
> **AngelTheOne said:**
> Ok thanks it works may i ask how i accesses the application now?

You will have to tell us the application you are trying to open.

If you know at least the start of the name, you can start typing in a terminal and then tab twice to see if you recognize the command to start the app. 

For instance, for gimp, you could type: gim + tab twice and it would produce commands starting with that letter combination.

You can also look in Synaptic. Use the Search window above the right panel.

You can also look through the menus, looking in the appropriate subfolders.

But if you give us the application, someone will be able to tell you where it's located.

---

### Post by AngelTheOne on 2009-09-02
Oh ok thanks a lot man :)

---

### Post by lisati on 2009-09-02
> **AngelTheOne said:**
> Ok thanks it works may i ask how i accesses the application now?

As drs305 pointed out it would be helpful for those who wish to help to know the name of the application.

In Ubuntu, the "Applications" ,many applications are started from the "Applications" menu, which is roughly equivalent to the Start menu in Windows (or the "orb" in Vista). Some things are started with the "System" menu, which is roughly equivalent to the Windows "Control Panel".

---

