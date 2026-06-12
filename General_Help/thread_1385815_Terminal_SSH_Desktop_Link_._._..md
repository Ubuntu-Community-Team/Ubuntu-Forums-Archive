---
title: "Terminal SSH Desktop Link . . ."
date: 2010-01-20
forum: General Help
---

### Post by misteralexander on 2010-01-20
Hello.

I've seen a few archived posts about making an SSH shortcuts.  The problem, they tell you to create a link through Nautilus.  That opens the remote server in a GUI view, I need a "Shortcut" as it were I can click & have it open up in Terminal.

Thanks!

-Alex.

---

### Post by Brandon Williams on 2010-01-20
If I understand what you're looking for, you want an icon on the desktop and/or a menu item that, when clicked, will launch a terminal running an ssh session to some specific remote machine. To do that, create a .desktop file that includes the following parameter setting:
```
Exec=gnome-terminal -e "ssh hostname"
```
where 'hostname' is the hostname or address of the machine you want to connect to.

I am more inclined to create aliases in bash for the hosts that I connect to frequently, something like this:
```
alias hostname='ssh hostname'
```
This way, I simply open a terminal and then type the name of the host I want to connect to. I find this more convenient than having lots of icons or menu entries.

Yet another alternative is to use an ssh client like putty, which has session support, which will keep track of the connection details for the machine you regularly connect to.

---

### Post by nothingspecial on 2010-01-20
Do you need an alias?

I have ```
alias server='ssh -X rob@192.168.2.10'
```

in my .bashrc

is that what you mean?

I just open a terminal and type server

obviously I have left out the important bit, but what I have shown you will let you do it within a home network.

---

### Post by synapsys on 2010-01-20
You could of course also make a bash script.

```
#!/bin/bash
ssh name@server
```

---

### Post by misteralexander on 2010-01-20
Thanks everyone for your help, but I actually figured it out shortly after posting my request.

This is what I needed & got 100% to a T.

[LIST]
[*]Right click the desktop (i'm using 9.10)

[*]Choose "Create Launcher"

[*]The "Create Launcher" box appears & you're able to fill in all sorts of info.

[*]At the very top, "Type", is a pull down menu.  Pull it down & choose "Application In Terminal".

[*]Name is whatever you'd like

[*]On the "Command" line type this:  ssh [email]username@server.com[/email]

[*]Comment it however you'd like.

[*]Click OK & yer done!
[/LIST]

You can also change the icon it has.  I made mine a computer hooked up to a globe.

Now, as I wanted, I have an icon on my desktop that I can double click and it lauches an SSH Session in Terminal.

PERFECT :KS

Thanks for all the hlep!

-Alex.

---

