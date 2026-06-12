---
title: "Run interactive script after login"
date: 2011-01-26
forum: General Help
---

### Post by jbchristensen on 2011-01-26
I need to run a script that prompts the user for some input and takes action based on that input. It must run at the end of the login process, after the desktop is displayed.

I tried putting it in ~/.bash_login, but it didn't run. Do I need to tell /etc/profile to run ~/.bash_login? I thought it looked for it & ran it if it was found.

A related question would be - 
  Can I make it so the terminal session that is running the script be the only thing that the user can do? In other words, they can't click on anything on the desktop or in the panels and have it run until after they respond to the input request.

Thanks!
Jon

---

### Post by pl@yer on 2011-01-26
I have seen it before where their default shell in /etc/passwd was set to be a menu based script. That is all they saw when they logged in.

That was for people logging in through ssh though.

---

