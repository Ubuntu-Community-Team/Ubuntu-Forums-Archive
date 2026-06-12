---
title: "Can't login with password"
date: 2011-06-21
forum: General Help
---

### Post by micha8l on 2011-06-21
I can't login with my password any more, here's what I did to mess this up:

[COLOR=Red][FONT=Arial Black][I][B]!!!WARNING DO NOT RUN THIS COMMAND!!!

[/B][/I][COLOR=Black][FONT=Arial]I ran this command, to get rid of the user list on login:
[/FONT][/COLOR][/FONT][/COLOR]```

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gdm/simple-greeter/disable_user_list [COLOR=Red]true[/COLOR]

```

When I logout I see a password box asking me for my password, I enter it, but it does not validate. I restart my PC and I'm presented with the same login, but luckily I had auto-login enabled, if it wasn't for this I would not be able to login.

I'm trying to undo the above command now, so I run:
```

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gdm/simple-greeter/disable_user_list [COLOR=Green]false[/COLOR]

```

When I logout I'll see the normal Ubuntu 10.04 login screen and everything works fine, but when I restart my PC it reverts back again!

How can I fix this please :/

---

### Post by wildmanne39 on 2011-06-21
> **micha8l said:**
> I can't login with my password any more, here's what I did to mess this up:

[COLOR=Red][FONT=Arial Black][I][B]!!!WARNING DO NOT RUN THIS COMMAND!!!

[/B][/I][COLOR=Black][FONT=Arial]I ran this command, to get rid of the user list on login:
[/FONT][/COLOR][/FONT][/COLOR]```

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gdm/simple-greeter/disable_user_list [COLOR=Red]true[/COLOR]

```

When I logout I see a password box asking me for my password, I enter it, but it does not validate. I restart my PC and I'm presented with the same login, but luckily I had auto-login enabled, if it wasn't for this I would not be able to login.

I'm trying to undo the above command now, so I run:
```

sudo gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --type bool --set /apps/gdm/simple-greeter/disable_user_list [COLOR=Green]false[/COLOR]

```

When I logout I'll see the normal Ubuntu 10.04 login screen and everything works fine, but when I restart my PC it reverts back again!

How can I fix this please :/
Hi, this might help it is for resetting passwords.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

