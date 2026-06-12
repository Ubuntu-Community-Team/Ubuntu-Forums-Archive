---
title: "Am I safe?"
date: 2011-11-09
forum: General Help
---

### Post by ki4jgt on 2011-11-09
OK, so I installed LAMP. I wanted to host a website. Seeing as I can't get it working. I want to uninstall it. I go to a website which has this BIG blue commmand right in the center. I type it in. After it starts getting packages, I read in small print. "This is what most websites tell you to do. DO NOT DO IT. It erases part of your desktop." WHY IN THE WORLD WOULD ANYONE DO THAT&#8253; I exit the terminal. Am I safe?

Also, how do I completely remove LAMP. When I tried to reinstall Apache earlier, it wasn't fresh. Instead, it had all the mistakes I had gotten into from my earlier install. I've tried:

```
sudo apt-get remove --purge apache2 apache2-commons
```

I know this is complex but is there no way to do a complete reinstall without wiping my entire system?

---

### Post by Dangertux on 2011-11-09
The command you entered will fully remove apache and its components. 

That being said, what was the command you entered that you think deleted some of your desktop?

---

### Post by ki4jgt on 2011-11-09
> **Dangertux said:**
> The command you entered will fully remove apache and its components. 

That being said, what was the command you entered that you think deleted some of your desktop?

```
sudo apt-get remove lamp-server^
```

---

### Post by ki4jgt on 2011-11-09
And now that I've logged in, it's asking me to do a distrobution upgrade :-(. Why do people have to go off the grid for uninstalling :-( why can't you just enter one command to do what you need!?!?!?!?!?!?!?!?!?!?!?!?!?! Sorry for the rant. I'm going insane.

---

### Post by Dangertux on 2011-11-09
That command shouldn't remove any part of your desktop. The notice for distro upgrade probably has nothing to do with lamp but more the fact that you probably ran

```

sudo apt-get update

```

prior to installing lamp.

Hope this helps.

---

