---
title: "Problem removing program"
date: 2009-09-29
forum: General Help
---

### Post by t4ggs on 2009-09-29
Hi, I installed picasa and wanting to remove it i went to the folder in opt/google and removed it..now im not able to uninstall it via add/remove...any  idea how to do that?


thanks

---

### Post by mike2357 on 2009-09-29
You could try re-installing it and then removing it using add/remove.  I'm taking a guess but I don't think it would make anything worse, and there's a good chance it would work.

---

### Post by oboedad55 on 2009-09-29
> **mike2357 said:**
> You could try re-installing it and then removing it using add/remove.  I'm taking a guess but I don't think it would make anything worse, and there's a good chance it would work.

This should work. It's never a good idea to go and start removing things before you uninstall them. Always go to add/remove or synaptic to uninstall.

---

### Post by t4ggs on 2009-09-30
i cant, when i try to remove it in synaptic it gives me this error: E: picasa: subprocess pre-removal script returned error exit status 1

---

### Post by cgroza on 2009-09-30
wait a minute...you unistaled the program by deleting a folder?

---

### Post by credobyte on 2009-09-30
Why you can't uninstall it via Add/Remove ? What's the error ? Also, how did you installed Picasa ?

---

### Post by t4ggs on 2009-09-30
Thats how i Installed [http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html)

its the same error, i unchek picasa and when i apply it starts to uninstall but then says that theres is an error


and yeah i erased the folder??? why it cannot be undone...even in windows when you uninstall a program by ereasing the folder u r still able to uninstall it and reinstall

---

### Post by credobyte on 2009-09-30
> **t4ggs said:**
> Thats how i Installed [http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-picasa-3-5-in-ubuntu.html)

its the same error, i unchek picasa and when i apply it starts to uninstall but then says that theres is an error


and yeah i erased the folder??? why it cannot be undone...even in windows when you uninstall a program by ereasing the folder u r still able to uninstall it and reinstall


```
sudo dpkg -r picasa
```

P.S. - stop associating everything with Windows ( just a friendly advice ).

---

### Post by t4ggs on 2009-09-30
> **credobyte said:**
> ```
sudo dpkg -r picasa
```


```
(Reading database ... 175416 files and directories currently installed.)
Removing picasa ...
/var/lib/dpkg/info/picasa.prerm: 608: /opt/google/picasa/3.0/bin/killpicasa: not found
picasa.prerm:error: could not find xdg-desktop-menu in PATH or '/opt/google/picasa/3.0'
dpkg: error processing picasa (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 picasa
```



> **credobyte said:**
> P.S. - stop associating everything with Windows ( just a friendly advice ).


Hahahahaha

---

