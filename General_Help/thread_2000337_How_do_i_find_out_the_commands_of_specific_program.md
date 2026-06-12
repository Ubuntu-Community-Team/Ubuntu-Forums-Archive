---
title: "How do i find out the commands of specific program actions?"
date: 2012-06-09
forum: General Help
---

### Post by Macfunky on 2012-06-09
I want to find out the commands for specific program actions eg. what command is used to open a new tab in firefox etc. I stumbled upon a feature in myunity today in which you can customise quicklists which is why i am looking to find out how to do this. I thought that opening a program in the terminal would do this with the command of every action thereafter printed. How can i achieve this?

---

### Post by forrestcupp on 2012-06-09
Well, you can't just control every action in every app out there with a terminal command. They usually have all their actions hardcoded into their code.

But *some* programs let you include parameters when you run them. Usually, for apps that let you do this, you can get a list of parameters by typing
```
*appname* --help
```And usually you can get a more in depth explanation about how to use an app by typing
```
man *appname*
```Not all apps let you manipulate them from the terminal, and usually you can't do anything from the terminal after it is already running. If an app isn't made to let you add parameters in the terminal, then you'd have to actually modify the program's code, or learn to program with its plugin api, if it happens to support that.

---

### Post by Macfunky on 2012-06-09
> **forrestcupp said:**
> Well, you can't just control every action in every app out there with a terminal command. They usually have all their actions hardcoded into their code.

But *some* programs let you include parameters when you run them. Usually, for apps that let you do this, you can get a list of parameters by typing
```
*appname* --help
```And usually you can get a more in depth explanation about how to use an app by typing
```
man *appname*
```Not all apps let you manipulate them from the terminal, and usually you can't do anything from the terminal after it is already running. If an app isn't made to let you add parameters in the terminal, then you'd have to actually modify the program's code, or learn to program with its plugin api, if it happens to support that.

Thought that the terminal would be the way to do this. What other ways are there to find out what command to use for specific actions?

---

### Post by philinux on 2012-06-09
> **Macfunky said:**
> I want to find out the commands for specific program actions eg. what command is used to open a new tab in firefox etc. I stumbled upon a feature in myunity today in which you can customise quicklists which is why i am looking to find out how to do this. I thought that opening a program in the terminal would do this with the command of every action thereafter printed. How can i achieve this?

Do you mean keyboard shortcuts. In firefox ctrl t opens new tab. Mouse to top left to reveal the global menu and look under File etc etc.

---

### Post by zombifier25 on 2012-06-09
No better way to do it than studying the manpages, like forrestcupp said. they should give you most, if not all, the parameters available for a command. Useful for quicklist editing.
EDIT: You did not say exactly which are the "commands", so I presumed you meant the terminal commands, since you mentioned quicklist editing.

---

### Post by Macfunky on 2012-06-09
> **philinux said:**
> Do you mean keyboard shortcuts. In firefox ctrl t opens new tab. Mouse to top left to reveal the global menu and look under File etc etc.

I'm probably not explaining it as well as i could :P 

Myunity allows you to add custom quicklists. You add the name and then the command to execute it and it'll show up as a quicklist. I am wondering how to find out the commands to actions that i would like to add as quicklists. To find out the command to start up an application is easy, i just go to alacarte and can find it there but i am looking to find out the commands to things such as actions within an application. I don't know how to find out what commands to use for these and i'm wondering the easiest way to find them out. I was just using opening a tab as an example but it would be actions like this i would be looking to figure out the commands to so i can use them as quicklists.

---

### Post by Macfunky on 2012-06-09
> **forrestcupp said:**
> Well, you can't just control every action in every app out there with a terminal command. They usually have all their actions hardcoded into their code.

But *some* programs let you include parameters when you run them. Usually, for apps that let you do this, you can get a list of parameters by typing
```
*appname* --help
```And usually you can get a more in depth explanation about how to use an app by typing
```
man *appname*
```Not all apps let you manipulate them from the terminal, and usually you can't do anything from the terminal after it is already running. If an app isn't made to let you add parameters in the terminal, then you'd have to actually modify the program's code, or learn to program with its plugin api, if it happens to support that.

Actually this is what i was looking for. Didn't realise it at first. Thank you :)

---

