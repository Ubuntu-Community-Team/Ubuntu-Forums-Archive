---
title: "Acidentally changed primary group?"
date: 2010-05-20
forum: General Help
---

### Post by Lucky75 on 2010-05-20
Hi,

I think I accidentally changed by default/main user's primary group my doing usermod -g <some other group> <username>.

Is that bad? What should the primary group be for my user? The same name? So If my user was lucky75, do I do "usermod -g lucky75 lucky75" to change it back? Do I need to do anything else?

Thanks for the help!

---

### Post by bodhi.zazen on 2010-05-20
Yes, use -g

[http://manpages.ubuntu.com/manpages/lucid/en/man8/usermod.8.html](http://manpages.ubuntu.com/manpages/lucid/en/man8/usermod.8.html)

You probably should change it back, depending on what you changed it too (system accounts such as root would be less then ideal).

---

### Post by cariboo on 2010-05-20
Use the groups command to see what groups your user is a member of.

If you aren't a member of the Lucky75, you can use:

```
sudo gpasswd -a Lucky75 Lucky75
```

like you asked.

---

### Post by Lucky75 on 2010-05-20
Thanks :) I was worried that I had to do something else like re-add myself to all other groups or something, but I guess not :)

---

