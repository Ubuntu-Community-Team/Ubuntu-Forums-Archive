---
title: "Workgroups - How can I do this?"
date: 2009-09-23
forum: General Help
---

### Post by sim085 on 2009-09-23
Hi,

At work, when I switch on my computer I have to insert a username and password. Through this account I can access resources such as a printer, and I can also share files with other colleagues. 

However the username and password I use to access my computer are the same as the username and password of my work email account (changing the password of one would automatically change the password of the other) and also of the file server. 

My question is; how can I build the same setup using Linux and Open Source technology? 

Regards,
Sim085

---

### Post by badger_fruit on 2009-09-23
What you describe is a typical Active Directory and Exchange domain.

Samba will turn a PC into a PDC (Primary Domain Controller), LDAP will provide Active Directory like services and there's a good selection of free, open source email servers which can hook into the configuration (openxchange is the first that pops into mind but I don't think it's free).

Have a look here --> [http://www.steve-lacey.com/blogarchives/2006/11/linux_as_a_wind.shtml](http://www.steve-lacey.com/blogarchives/2006/11/linux_as_a_wind.shtml)

Should give you more info for your needs :)
Good luck and PLEASE, post back with your progress as this is something I've considered doing myself but never got around to!

---

### Post by sim085 on 2009-09-23
> **badger_fruit said:**
> What you describe is a typical Active Directory and Exchange domain.

Thanks :) I'll read that article and try to build one and see how it goes. In my design I would like to allow both Windows and Linux based computers.

---

### Post by badger_fruit on 2009-09-23
> **sim085 said:**
> Thanks :) I'll read that article and try to build one and see how it goes. In my design I would like to allow both Windows and Linux based computers.

As far as I know this is not a problem; the PDC/LDAP will be able to authenticate both Windows and Linux users - after all, the directory doesn't really care too much about the OS used, just confirms (at a basic level that is!) the username and password are correct.

As for Zander Mort's post ... I suspect that was meant to be somewhere else lol!

---

