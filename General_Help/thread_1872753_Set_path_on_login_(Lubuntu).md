---
title: "Set path on login (Lubuntu)"
date: 2011-10-31
forum: General Help
---

### Post by Paddy Landau on 2011-10-31
I know how to add to the path on login in Ubuntu: enter the new path in either [FONT=Fixedsys]/etc/profile[/FONT] (for all users) or [FONT=Fixedsys]~/.profile[/FONT] (for just one user). For example:```
PATH="/new/path:${PATH}"
```Neither of these files works in Lubuntu. I have tried [FONT=Fixedsys]~/.bash_profile[/FONT], but that also does not work.

How can I set the path in Lubuntu on login, please?

---

### Post by Lars Noodén on 2011-10-31
What about [FONT=Fixedsys].bashrc[/FONT] or [FONT=Fixedsys].login[/FONT]?

---

### Post by Paddy Landau on 2011-10-31
> **Lars Noodén said:**
> What about [FONT=Fixedsys].bashrc[/FONT] or [FONT=Fixedsys].login[/FONT]?
Thanks, Lars, but [FONT=Fixedsys].bashrc[/FONT] is only run when starting a terminal (and lasts only for that terminal's session), and Lubuntu runs neither [FONT=Fixedsys].login[/FONT] nor [FONT=Fixedsys].bash_login[/FONT].

---

### Post by Paddy Landau on 2011-11-07
Yippee! I have stumbled upon the answer.

The login script file is
```
~/.xsessionrc
```

---

### Post by collisionystm on 2011-11-07
You can change the login path with /etc/passwd

---

### Post by amjjawad on 2011-11-07
> **Paddy Landau said:**
> Yippee! I have stumbled upon the answer.

The login script file is
```
~/.xsessionrc
```

Glad you managed to find it :) that was faster than the reply I was waiting by email from someone :)

Hope you updated the other thread on LXDE Forum too :)

---

### Post by Paddy Landau on 2011-11-08
> **collisionystm said:**
> You can change the login path with /etc/passwd
Thanks for that information. It's not what I was asking, but it's useful to know.


> **amjjawad said:**
> Hope you updated the other thread on LXDE Forum too
Yes, I did. I was wondering whether or not this information could be added to the LXDE and Lubuntu wikis?

---

### Post by amjjawad on 2011-11-08
> **Paddy Landau said:**
> Yes, I did. I was wondering whether or not this information could be added to the LXDE and Lubuntu wikis?

Done but not by me :)

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Setting_environment_variables_upon_login](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Setting_environment_variables_upon_login)

---

### Post by Paddy Landau on 2011-11-09
> **amjjawad said:**
> Done but not by me :)

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Setting_environment_variables_upon_login](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#Setting_environment_variables_upon_login)
Well, it was not done and parts were incorrect, so I have edited it to fix it. Thanks for pointing me to the right page and section.

---

### Post by amjjawad on 2011-11-09
> **Paddy Landau said:**
> Well, it was not done and parts were incorrect, so I have edited it to fix it. Thanks for pointing me to the right page and section.

I'm actually not aware of anything related to that topic. I asked for help through mailing list to help you with your issue. I saw your topic on LXDE Forum too so I tried to help as much as possible. Two people replied me and one of them updated the Wiki.

Anyway, glad you updated it :)
You welcome and thanks for the update!

---

### Post by Paddy Landau on 2011-11-09
> **amjjawad said:**
> ... one of them updated the Wiki.
It's still not on the [LXDE Wiki]("http://wiki.lxde.org/en/LXSession"), though. I don't feel comfortable changing its Wiki.

---

