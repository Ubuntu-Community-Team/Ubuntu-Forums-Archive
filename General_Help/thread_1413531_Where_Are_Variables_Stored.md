---
title: "Where Are Variables Stored"
date: 2010-02-22
forum: General Help
---

### Post by Chamillionaire2 on 2010-02-22
What's Up?

So if you used```
call=pwd
```
It would be stored so whenever you typed $call the command you entered would be executed, But where does ubuntu store these variables?

Thanks Bye.

---

### Post by Intrepid Ibex on 2010-02-22
Most likely in RAM. The size of /tmp didn't increase when I did a test.

---

### Post by mcduck on 2010-02-22
RAM. The variables aren't stored anywhere if you log out or boot the machine.

If you wihh the variable to work after a boot you need to define it in some of the configuration files that are executed when you log in, like ~/.bashrc or ~/.profile

..actually defining a variable that way doesn't even make it work anywhere else than in your current session, for example if you have two terminal windows open and you define a variable like that in one terminal it won't work in the other terminal window. You need to export the variable to make it a global variable:
```
export call=pwd
```

anyway, if you just want to make a certain command to execute by typing something else in command line, then variables aren't really the right tool. Instead you want to create an alias:
```
alias call='pwd'
```
(you'll have to do this in ~/.bashrc just like with variables to make it always available.

---

