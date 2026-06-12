---
title: "MediaTomb"
date: 2010-02-24
forum: General Help
---

### Post by Sirsteveo on 2010-02-24
I have no idea where to ask these questions about mediatomb but hopefully someone can help me here. MediaTomb is very very cool and I am very new to it as I am very new to Ubuntu and I really dont understand terminal quite yet either but lets get me to know mediatomb first. I was told to open terminal and type mediatomb i guess to activate it but im not really sure what it does when i type it in there all i know is it gives me and http and some numbers that i put in my url that takes me to some mediatomb page to setup what i want. so what does typing mediatomb into terminal do and do you only need to do it the original time or everytime you want to use it. Does terminal need to be open to have the server up or does the webpage with all thoes numbers need to be open? To make it even simpler do all i need to do to get the server up is type in the numbers into the url that i originally got and set all my preferences for? Im sorry this is confusing i know i suck at asking questions but if anyone can answer without confusing me more i would really appreciate it i love to learn about this stuff.

---

### Post by buntunoob on 2010-02-24
1. what does typing mediatomb into terminal do and do you only need to do it the original time or every time you want to use it?....well typing mediatomb is kind of like .exe a program. with that Said, there are different options on how you run it you can run it thru that Terminal or run it as a daemon, to do so start it like so...
  ```
mediatomb -d
```  Probably one of the harder things you'll have to do with this is to get it to start at boot as there are a few things that mess it up, myself mediatomb was trying to start before the network was up so it would fail,
      first off I had to make sure my Startup script was working

```
/etc/init.d/mediatomb start
```or
```
sudo /etc/init.d/mediatomb start
```  [FONT=&quot]I don't rember its been a while[/FONT]
  [FONT=&quot]now if that does work it's most likely the network that's stopping you from starting at boot, and the log file should confirm this with a error.[/FONT]
  
  [FONT=&quot]this changes the run lvl of mediatomb[/FONT]
  
```
sudo update-rc.d -f mediatomb remove
sudo update-rc.d mediatomb defaults 99

```

---

### Post by 3rdalbum on 2010-02-24
I'm pretty sure that Mediatomb both starts at startup, and when you install the package. So you don't need to explicitly start it by typing its name into the terminal.

Mediatomb runs in the background, doing nothing until another program (usually on another computer) tries to discover it or wants to play some files.

Mediatomb is basically set-and-forget.

---

### Post by Sirsteveo on 2010-02-24
Why does mediatomb sometimes ask me for username and password?

---

