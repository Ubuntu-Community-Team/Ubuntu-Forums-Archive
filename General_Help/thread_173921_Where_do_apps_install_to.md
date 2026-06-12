---
title: "Where do apps install to?"
date: 2006-05-11
forum: General Help
---

### Post by electroconvulsive on 2006-05-11
I have downloaded and installed bit defender linux edition on my ubuntu machine. Now I want to run the program and even though it has been installed I cant seem to find the program so i can launch it or add it to the application menu. Can anyone tell me where it installed or how to run it because the bitdefender website only has windows documentation. Is there a sudo command I can use to find out where it installed or to run it in console or whatever?

---

### Post by kabus on 2006-05-11
First I'd open a terminal, enter 'bit' and hit the <Tab> key.
If that turns up something that looks like bitdefender you can use the 'which' command to get the full path to the executable.
If tab-completion doesn't find anything you could try :

```

sudo updatedb
locate bitdefender

```

---

### Post by bikeboy on 2006-05-11
Sometimes things don't get put into the menus, not sure why.

There are a few things you can try in the console.

Typing bitdefender (might need sudo) will probably launch it, but if the binary isnt called that it won't work. So try:

"sudo find / -name bitdefender" without the quotes.

Or even try typing "bit" then pressing tab. This does auto complete, if nothing shows up press tab again and it will show all the possibilities.

edit: beaten to it, and "which" is very handy but I forgot about it :)

---

