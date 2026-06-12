---
title: "php cli works in shell, not when being called"
date: 2011-02-21
forum: General Help
---

### Post by SnIpY on 2011-02-21
Hey all!

I have a certain script in my shell which works when being manually executed by using 'php bot.php'

However, when I want it to start using a website, it doesn't do anything. The website & the script are on the same shell. 

It's being called like this:
```
shell_exec('screen -dmS "bot" php ' . ROOT . '/modules/' . MODULE . '/bot.php');
```

Any ideas what might be wrong?

---

