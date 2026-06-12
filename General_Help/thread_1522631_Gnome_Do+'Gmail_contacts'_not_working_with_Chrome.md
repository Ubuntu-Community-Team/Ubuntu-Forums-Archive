---
title: "Gnome Do+'Gmail contacts' not working with Chrome"
date: 2010-07-02
forum: General Help
---

### Post by miesogeno on 2010-07-02
with the "gmail contacts" plugin, I can find my contacts with Gnome Do, but can't do anything with them. I select "send email" and nothing happens.

in my system->preferences->preferred applications, I have gmail for a default email application opening in Chrome (links to email adresses on webpages work fine), but if I change that to Firefox, the gmail contacts plugin will work with Gnome Do. otherwise, it doesn't.

does anyone know how to fix that? I dont even know if the problem is in Gnome Do or on my command for the preferred email client which is:

perl -MURI::Escape -e '$to= shift; if ($to =~ /^([^\?]+)\?(.*)$/){$to=$1;$args="&".$2;$args=~s/\&subject=/&su=/};$to =~ s/^mailto://i; exec("chrome","https://mail.google.com/mail/?ui=2&fs=1&view=cm&to=".URI::Escape::uri_escape($to).$args);' %s

thanks in advance.

---

### Post by miesogeno on 2010-07-02
it would be helpfull to know where that particular plugin can be tweaked.

---

### Post by miesogeno on 2010-07-03
nobody?

---

### Post by miesogeno on 2010-07-04
anybody..?

i'm feeling a bit of a robinson crusoe here. but more inapt.

---

