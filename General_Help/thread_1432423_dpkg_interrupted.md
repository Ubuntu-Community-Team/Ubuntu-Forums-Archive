---
title: "dpkg interrupted"
date: 2010-03-17
forum: General Help
---

### Post by ronc69 on 2010-03-17
In attempting to install updates recently, I received the following message:

E: dpkg was interrupted. You must manually run "dpkg-configure-a" to correct the problem.

E:cache - > open ( ) failed, please report.

I would appreciate advise on how to deal with this. Be advised that I am a 75 year old amateur so no big words or jargon.       Many thanks   ronc69

---

### Post by llamabr on 2010-03-17
Just follow the advice it gave you.  From a terminal:

```
sudo dpkg-configure-a
```

---

### Post by stoneage on 2010-03-17
Usually entering > sudo dpkg -configure -a in a Terminal fixes it. You have tried this?

---

### Post by audiomick on 2010-03-17
Hi,
The suggested action is in the error message:

> **ronc69 said:**
> In attempting to install updates recently, I received the following message:

```
E: dpkg was interrupted. [COLOR=Blue]You must manually run "[COLOR=Red]dpkg-configure-a[/COLOR]" to correct the problem.[/COLOR]

E:cache - > open ( ) failed, please report.
```

That means:
go to the menu "applications" then "accessories" and select "terminal"
(that is usually written something like this
applications> accessories> terminal
you may have seen that already somewhere)

A window will open up that looks a bit like this
[ATTACH]150452[/ATTACH]

type this in, or copy it from here and paste it into the terminal
```
sudo dpkg --configure -a
```
note: to paste in the terminal you must use "shift + ctrl + v", not just "ctrl + v" like in most other programs. Or you can choose "paste" out of the edit menu.

When you have the command in the terminal, hit enter.
You will be asked for a pass word. The one you need is the one you log on with when you start the computer.
You will not see what you are typing when you type in your password at the prompt. Just type it in (correctly!! ;)) and hit enter again.

If the error message was right, this should sort out your problem.

---

### Post by nerdopolis on 2010-03-17
That last command should be:
```
sudo dpkg-configure -a
```

---

### Post by oldos2er on 2010-03-17
The correct command is ```
sudo dpkg --configure -a
```

---

### Post by audiomick on 2010-03-17
oops, you are right, of course, Ann. I copied it out of the OP's first post without thinking about it...:redface:

edit: I went back and corrected it.

---

### Post by lisati on 2010-03-17
:popcorn:

---

