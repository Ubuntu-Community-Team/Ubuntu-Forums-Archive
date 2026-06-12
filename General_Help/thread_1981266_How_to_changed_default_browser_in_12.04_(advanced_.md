---
title: "How to changed default browser in 12.04 (advanced way)"
date: 2012-05-16
forum: General Help
---

### Post by ebu on 2012-05-16
Hi,

I need to change default browser to 

[PHP]gksu -w -u chromium chromium-browser[/PHP].

The problem is that there is no "command option" like shown [here]("http://tips.webdesign10.com/how-to-change-the-default-browser-in-ubuntu-linux") in 12.04.

I tried to change handlers as described [here]("http://askubuntu.com/questions/18418/how-to-set-which-application-is-launched-by-xdg-open") too but it didn't work.

Then I also saw  [this]("http://askubuntu.com/questions/38565/cant-set-chromium-as-default-browser") post, but I'd really try to avoid doing any "alternative" updates as much as possible. I just do not want to break the idyll I got with 12.04 after almost two years of worries and wonders with non-LTS versions.

So it it possible to do just by tweaking some config, without major changes to the system?

Best regards, Eugene.

---

### Post by Cheesemill on 2012-05-16
Why are you running your browser as root?

Do you know how dangerous that is :-?

---

### Post by ebu on 2012-05-16
> **Cheesemill said:**
> Why are you running your browser as root?

Do you know how dangerous that is :-?

I am not running my browser as root. And I even do not want to run it under my normal user account. And that's why I need gksu.

---

### Post by Cheesemill on 2012-05-16
Sorry, I didn't see the -u switch.

Anyway, fire up gconf-editor (you may have to install it first) and edit the following key:

/desktop/gnome/applications/browser

---

### Post by ebu on 2012-05-17
> **Cheesemill said:**
> 
and edit the following key: /desktop/gnome/applications/browser

didn't help.

---

