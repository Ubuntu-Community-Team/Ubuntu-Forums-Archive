---
title: "newbie trying to get Tor HELP!!!"
date: 2010-07-13
forum: General Help
---

### Post by machinanoctua on 2010-07-13
hey guys, im new here and i have only been using ubuntu for around 3 months, but i love it ! my only problem so far is that i really need Tor, but i just keep messing up the download in the terminal. it asks me if im the root user but i dont know the password or anything and the present walk-throughs are confusing. i just need some advice about the root prob and then i'll take another stab. thank you for any advice !!!;)

---

### Post by dtrot55 on 2010-07-13
You probably didn't set a password for the root user...try this:

In terminal

```

sudo passwd root

```

This should allow you to create a password for the root user

If you want to be the root user then just switch over using this:

```

su root

```

Then to switch back to your login just do

```

su "your username"

```

Hope that helps!

---

### Post by confused57 on 2010-07-13
Maybe this will help:
[https://help.ubuntu.com/community/Tor?action=show&redirect=TOR](https://help.ubuntu.com/community/Tor?action=show&redirect=TOR)

---

### Post by machinanoctua on 2010-07-14
yes!!! it worked thanks guys i really appreciate it , i have learned something new !

---

