---
title: "main user not longer admin? (laguaje support not starting)"
date: 2011-11-25
forum: General Help
---

### Post by manco1911 on 2011-11-25
Hi guys, im running ubuntu 11.10 x64. 
After i installed virtualbox, i had to get my user into the vboxusers group so I could have more privileges on running virtual machines.. 

when i tried to to that, i didn't used the "-a" option, so i added myself to the vboxusers group, and deleted myself from any other group.. (yes i know.. lame.. )

I could fix things by booting on live again and modifying the /etc/groups file.. i added myself on the same groups think i was (i used my other box to use as reference)... 

But now i realized i cant launch the Language Support from my user.. first it didn't work (start/launch).. so i tried on the console so i could see what error could display, this is it:

[FONT="Courier New"]$ gnome-language-selector 
Traceback (most recent call last):
  File "/usr/bin/gnome-language-selector", line 27, in <module>
    options=options)
  File "/usr/lib/python2.7/dist-packages/LanguageSelector/gtk/GtkLanguageSelector.py", line 141, in __init__
    grp.getgrnam("admin")[2] in os.getgroups())
KeyError: 'getgrnam(): name not found: admin'[/FONT]

I really cant understand whats going on here.. 
I can start Language Support by console if i "sudo" (sudo gnome-language-selector").. 

My user is also on the same user groups as my other reference box (on wich i can launch language support without issues).. 

So, what can this be or what should i do to fix it.. ?

---

### Post by fdrake on 2011-11-25
this is strange since gnome-language-selector should be able to be run by any user. My ls -l shows:
```

ls -l /usr/bin/gnome-language-selector

```
> 
-rwxr-xr-x 1 root root 871 2011-05-25 04:09 /usr/bin/gnome-language-selector
so in the end shouldn't matter the group you belong to. check the permission of gnome-language-selector.

---

