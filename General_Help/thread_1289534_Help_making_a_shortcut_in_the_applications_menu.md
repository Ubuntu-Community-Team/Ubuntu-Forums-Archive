---
title: "Help making a shortcut in the applications menu"
date: 2009-10-12
forum: General Help
---

### Post by JigglyWiggly_ on 2009-10-12
Ok so I made a basic sh file
```

cd /home/jigglywiggly/eclipse
sudo ./eclipse

```

It works if I run like in a terminal ```

sh /home/jigglywiggly/eclipse.sh
```
Works so I go to the edit menu thing create something called eclipse with the command "sh /home/jigglywiggly/eclipse.sh"

Then it says failed to execute child process no such file or directory...?

---

### Post by DeMus on 2009-10-12
> **JigglyWiggly_ said:**
> Ok so I made a basic sh file
```

cd /home/jigglywiggly/eclipse
sudo ./eclipse

```

It works if I run like in a terminal ```

sh /home/jigglywiggly/eclipse.sh
```
Works so I go to the edit menu thing create something called eclipse with the command "sh /home/jigglywiggly/eclipse.sh"

Then it says failed to execute child process no such file or directory...?

When you made the "menu thing", did you choose Application in Terminal?
You use the command line code to start it, so it should be started in terminal.
Or you can probably just use eclipse as command in your launcher.

---

### Post by Giblet5 on 2009-10-12
Change the "sudo" to "gksudo".

If it still doesn't work, there's a typo in the menu launcher.

---

### Post by Giblet5 on 2009-10-12
And why in the world would you do development as root?

I've been coding for a loooooooooooong time and I would never trust myself to remember that 'This one window runs as superuser!'

---

### Post by kanikilu on 2009-10-12
Rather than using a shell script, couldn't you just make a shortcut like so: ```
gksu /home/jigglywiggly/eclipse/eclipse
```

---

### Post by JigglyWiggly_ on 2009-10-12
> **Giblet5 said:**
> And why in the world would you do development as root?

I've been coding for a loooooooooooong time and I would never trust myself to remember that 'This one window runs as superuser!'
I tried running it as not root and then it couldn't go into my dropbox folder for whatever reason?

---

### Post by JigglyWiggly_ on 2009-10-12
> **kanikilu said:**
> Rather than using a shell script, couldn't you just make a shortcut like so: ```
gksu /home/jigglywiggly/eclipse/eclipse
```

Oh and that works nicely, danke.

---

### Post by CatKiller on 2009-10-12
> **JigglyWiggly_ said:**
> I tried running it as not root and then it couldn't go into my dropbox folder for whatever reason?

It's probably more sensible to sort that out than to run applications as root all the time.

---

