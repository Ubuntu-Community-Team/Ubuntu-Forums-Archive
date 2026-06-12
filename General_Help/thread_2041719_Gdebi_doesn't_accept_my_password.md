---
title: "Gdebi doesn't accept my password"
date: 2012-08-13
forum: General Help
---

### Post by sonnet on 2012-08-13
I installed a command line system from the Ubuntu Server 12.04 image.
Then I installed on the top of it Gnome-shell along with the applications I wanted to install. Everything is fine with the exception of Gdebi.

When I click on a .deb package to install it, and insert my password I get the message:
[B]"incorrect password...try again".
[/B]

Does anybody have an idea why Gdebi doesn't get my password?

---

### Post by Paddy Landau on 2012-08-19
What do you get from other programs that ask for your password? You can try the following command (from the Dash or a Terminal):
```
gksudo :
```

---

