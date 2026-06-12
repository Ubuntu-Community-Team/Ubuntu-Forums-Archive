---
title: "firefox terminal command"
date: 2009-10-03
forum: General Help
---

### Post by mcp_ri on 2009-10-03
I have two versions of Firefox installed on my ubuntu: 3.0 and 3.5.
I installed 3.0 from repository and 3.5 manually from mozilla web site. Now I have a problem. When I type firefox into terminal it starts the one installed from repo, but I want it to start 3.5 which I manually installed into my /home folder. The main reason I want this is when I type firefox into Gnome-Do it starts 3.0 and I want it to start 3.5.

I'm new to linux and ubuntu so I don't know all the terminologies, but I hope you understood the question.

---

### Post by Primefalcon on 2009-10-03
firefox-3.5

---

### Post by mcp_ri on 2009-10-03
When I type firefox-3.5 I get an error:
```

The program 'firefox-3.5' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.5
bash: firefox-3.5: command not found

```

---

### Post by akakingess on 2009-10-03
that might be because it is called Shireteko, or whatever, but there should be a way to change the default web browser for the OS, I just can't remember where it is and I am not in front of my machine right now, will let you know if I can find the answer.

---

### Post by Primefalcon on 2009-10-03
> **akakingess said:**
> that might be because it is called Shireteko, or whatever, but there should be a way to change the default web browser for the OS, I just can't remember where it is and I am not in front of my machine right now, will let you know if I can find the answer.
doubt it, might be firefox-3.6 now.

Anyhow for the command just go to system->preferences->main menu

thats a listing of all your menu items just find the browser in there and right click properties, it'll tell you the command to open that browser from the terminal

---

### Post by mcp_ri on 2009-10-14
I created alias for firefox to run my manually installed firefox 3.5

[http://ss64.com/bash/alias.html](http://ss64.com/bash/alias.html)

---

