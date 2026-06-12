---
title: "Web Browser problems. Please Help!"
date: 2009-07-26
forum: General Help
---

### Post by AmericanPrincess109 on 2009-07-26
For some reason whenever I try to run Web Browser it doesn't come up.
When I click on it, it says "Starting Web Browser" but after a few seconds it goes away.
It was working earlir but I spent most of the evening installing Wine (which, of course isn't working) and now I can't get on the internet. (I'm using another computer).
 
I'm connected to the internet, but I just can't run Web Browser. Please help.

---

### Post by Ravernomina on 2009-07-26
in terminal try running this command

```
sudo Firefox
```

Type in your password and see if it brings it up

---

### Post by QIII on 2009-07-26
Just "firefox".   Don't use sudo.

When you do use sudo, it's small "s".

sudo

---

### Post by Ravernomina on 2009-07-26
darn english classes :L

---

### Post by raronson on 2009-07-26
You could have a stuck instance of firefox.  To check:

```
ps aux | grep firefox
```

If it shows up on the list, but not on your desktop, then you need to kill the process:

```
killall firefox
```

Check again with 'ps' (to confirm, if you like).  Then start it normally.

---

### Post by AmericanPrincess109 on 2009-07-26
I don't have firefox. I just have Web Browser-the program that came with the computer.

---

### Post by QIII on 2009-07-26
Is it launched by the icon that looks like a blue ball with an orange smudgy "flame" around it?

---

### Post by AmericanPrincess109 on 2009-07-26
No it's launched by a blue Globe. I've tried installing Firefox, but it didn't work.

---

### Post by QIII on 2009-07-26
If the icon is not on a panel, but is still in the menus, right click on it and click "Add this launcher to panel"

When it is on a panel, right click on the "blue globe" (which sounds like Firefox Shiretoko to me) and click Properties.

Tell me what it says in the "Command" box.


Edit -- just happened to think.  Is the icon you are clicking in the menu say "Epiphany web browser"?

---

### Post by AmericanPrincess109 on 2009-07-26
It worked! Thank you so much!
You saved my life, thank you!

---

