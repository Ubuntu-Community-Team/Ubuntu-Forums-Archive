---
title: "Teminal recursively"
date: 2012-06-22
forum: General Help
---

### Post by shashanksingh on 2012-06-22
I have a strange situation here.

when I type "gnome-terminal" in he terminal,new terminals keep on coming like a recursive call.

Why is it so?

---

### Post by vasa1 on 2012-06-22
I get just one new terminal. What desktop environment are you in? Mine is an Xfce 4.10 session.

---

### Post by raja.genupula on 2012-06-22
> **shashanksingh said:**
> I have a strange situation here.

when I type "gnome-terminal" in he terminal,new terminals keep on coming like a recursive call.

Why is it so?

what you got with this

```
gksu gnome-terminal
```

---

### Post by WorMzy on 2012-06-22
Are you using a custom script or alias to launch gnome-terminal? ```
type gnome-terminal
```

Can you launch xterm correctly?

---

### Post by vasa1 on 2012-06-22
> **raja.genupula said:**
> what you got with this

```
gksu gnome-terminal
```

Can you please explain what [FONT="Courier New"]gksu gnome-terminal[/FONT] will do?

---

### Post by prshah on 2012-06-22
> **shashanksingh said:**
> when I type "gnome-terminal" in he terminal,new terminals keep on coming like a recursive call.

More information, please: Do they keep coming, or do they stop (say after 5-10 terminals)?

Did you make any changes to your ".bashrc", especially ones that include "xterm" or "gnome-terminal"?

As you have mentioned, it is a strange situation and not one that should happen.

---

### Post by raja.genupula on 2012-06-22
> **vasa1 said:**
> Can you please explain what [FONT=Courier New]gksu gnome-terminal[/FONT] will do?

Yes I do . Its going to open a terminal with root . 

what i want to know is its behavior  with different commands which can open a terminal .So i gave gksu terminal and i want to know how the system going to behave for that action belongs to terminal .

---

### Post by shashanksingh on 2012-06-22
> **prshah said:**
> More information, please: Do they keep coming, or do they stop (say after 5-10 terminals)?

Did you make any changes to your ".bashrc", especially ones that include "xterm" or "gnome-terminal"?

As you have mentioned, it is a strange situation and not one that should happen.
Actually I made a modification in the .bashrc file.
I appended this line to the last
'gnome-terminal &'

I had done so in the earlier versions of ubuntu and it made the terminal come up automatically on startup. Now what happens is that the terminal doesnt launch at startup, but whenever I launch the terminal, it keeps opening a new one and stops when I type Ctrl+c.
I guess each time .bashrc is executed. Is it so?

> **vasa1 said:**
> I get just one new terminal. What desktop environment are you in? Mine is an Xfce 4.10 session.
Unity 3d (Gnome I guess)

> **raja.genupula said:**
> what you got with this

```
gksu gnome-terminal
```
I get the terminal with a hash prompt

> **WorMzy said:**
> Are you using a custom script or alias to launch gnome-terminal? ```
type gnome-terminal
```

Can you launch xterm correctly?
I get the exact same thing with xterm. One plaintext black terminal and then multiple terminals.

type gives me /usr/bin/gnome-terminal

---

### Post by hakermania on 2012-06-22
> **shashanksingh said:**
> Actually I made a modification in the .bashrc file.
I appended this line to the last
'gnome-terminal &'

I had done so in the earlier versions of ubuntu and it made the terminal come up automatically on startup. Now what happens is that the terminal doesnt launch at startup, but whenever I launch the terminal, it keeps opening a new one and stops when I type Ctrl+c.
I guess each time .bashrc is executed. Is it so?


Unity 3d (Gnome I guess)


I get the terminal with a hash prompt


I get the exact same thing with xterm. One plaintext black terminal and then multiple terminals.

type gives me /usr/bin/gnome-terminal

The .bashrc file loads and executes every command there, before you are able to insert input to your terminal.
So, it executes gnome-terminal, which reloads the .bashrc file and re-executes gnome-terminal and so on.

Remove that line from your .bashrc file.

To open the gnome-terminal every time you login, place this file to ~/.config/autostart (create directory if it doesn't exist) :
```

[Desktop Entry]
Type=Application
Exec=gnome-terminal
Hidden=false
NoDisplay=false
Name=Gnome Terminal

```

---

### Post by vasa1 on 2012-06-22
> **raja.genupula said:**
> Yes I do . Its going to open a terminal with root . 

what i want to know is its behavior  with different commands which can open a terminal .So i gave gksu terminal and i want to know how the system going to behave for that action belongs to terminal .

Thanks :) and that's why OP doesn't have a problem with gksu gnome-terminal because the mod to his .bashrc was responsible.

---

### Post by shashanksingh on 2012-06-22
I removed the terminal entry from bashrc and the problem seems to have gone.

I thought it was for startup.
Does it execute the scripts there before launching each terminal instance?

---

### Post by prshah on 2012-06-25
> **raja.genupula said:**
> what you got with this
```
gksu gnome-terminal
```

Asking someone to experiment (and performing such an experiment) with a command where you are not sure about the problem is bad form, especially when you ask them to perform the command with elevated priviliges.

I suggest that you avoid this kind of trouble shooting, since you are trampling over the security of superuser mode.

It is better to gather information about his specific setup (eg, in this case, the ".bashrc") before suggesting superuser commands which will yield a largely unknown result.

This is just a suggestion.

---

### Post by prshah on 2012-06-25
> **shashanksingh said:**
> I removed the terminal entry from bashrc and the problem seems to have gone.
Does it execute the scripts there before launching each terminal instance?

Commands within the .bashrc are executed each time a terminal emulator is launched (Even new tabs).

---

