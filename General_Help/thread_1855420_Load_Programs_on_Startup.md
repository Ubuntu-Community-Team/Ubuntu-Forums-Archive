---
title: "Load Programs on Startup"
date: 2011-10-06
forum: General Help
---

### Post by daquietmonkey on 2011-10-06
Greetings All

I am a developer and mostly use Netbeans and Chrome. Is there some way I can make these programs to automatically be loaded into memory on system startup and then when I launch them they will start immediately?

Also whenever I start my system I need to run some commands to stop apache and start xampp server like this:

```
sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 stop
```

Is there some way to automatically do that on startup?

Thanking you

---

### Post by arzali on 2011-10-06
I use e4rat [http://e4rat.sourceforge.net/wiki/index.php/Main_Page](http://e4rat.sourceforge.net/wiki/index.php/Main_Page) to preload apps like firefox on boot.
just open Netbeans and Chrome within two minutes in the first step (e4rat-collect) and e4rat will preload them for you too.

---

### Post by roadkillguy on 2011-10-06
What about System->Preferences->Startup Applications?  You can enter a specific command to run.

---

### Post by popper668 on 2011-10-07
[ATTACH]203759[/ATTACH]

what would i add at the command line?
thanks in advance

---

