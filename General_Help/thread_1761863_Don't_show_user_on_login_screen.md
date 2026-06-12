---
title: "Don't show user on login screen"
date: 2011-05-18
forum: General Help
---

### Post by mooseman123 on 2011-05-18
How do I control which users are seen from the login screen?

Thanks!
:popcorn:

---

### Post by MartyBuntu on 2011-05-18
What do you mean? Wouldn't all users be available?

---

### Post by aphatak on 2011-05-18
System accounts don't show up on the log-in screen.  If you want to create a system account, you would have to enter the command -
```
sudo useradd -r <username>
```and then set the password with ```
sudo passwd <username>
```However, these accounts do not have a home directory and the related infrastructure that facilitates session set-up.  So even if you selected 'Other ...' at the log-in screen, and entered the username and password, a GUI session will not be set up.  In fact, you could do nothing useful - not even log out!

I don't see the utility of such a user account (except to run system processes!).  You *can* create such an account, but my advice would be "***Professional driver on isolated course - do not try this at home***".

---

### Post by sisco311 on 2011-05-18
Check out the documentation of GDM:

[http://library.gnome.org/admin/gdm/2.32/gdm.html](http://library.gnome.org/admin/gdm/2.32/gdm.html)

[http://library.gnome.org/admin/gdm/2.32/configuration.html.en#greetersection](http://library.gnome.org/admin/gdm/2.32/configuration.html.en#greetersection)

[http://library.gnome.org/admin/gdm/2.32/configuration.html.en#greeterconfiguration](http://library.gnome.org/admin/gdm/2.32/configuration.html.en#greeterconfiguration)

---

### Post by mooseman123 on 2011-05-18
Is there any way to do this outside of a terminal? I noticed "other" on the login menu and I wanted to make some of the rarely-used accounts not show up.

---

### Post by sisco311 on 2011-05-18
You have to edit the /etc/gdm/custom.conf file:
```
gksu gedit /etc/gdm/custom.conf
```

to look like this:
```
[greeter]
Exclude=**user1,user2**,bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator
,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap
```

where **user1** and **user2** are the users you want to exclude from the list.

---

### Post by mooseman123 on 2011-05-18
So you're saying there is no graphical settings area for this?

---

### Post by wildmanne39 on 2011-05-18
> **mooseman123 said:**
> So you're saying there is no graphical settings area for this?

Hi, I went and looked at the log in screen from the menu and you can uncheck show a list of users. It is under administration.

---

