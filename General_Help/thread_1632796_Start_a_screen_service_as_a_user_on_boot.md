---
title: "Start a screen service as a user on boot"
date: 2010-11-28
forum: General Help
---

### Post by Pezmc on 2010-11-28
Is there a way on ubuntu server (10.4) to start a service automatically on boot but for a particular user and within screen?

On my web server I host a game server for a local group, but I often have to reboot my server and I often forget to change to their user and start a screen for them.

I would like the system to; change to the user gs, open a screen called l4d2 and then run ./start

Is this possible? I couldn't find the answer in google (I may have been searching for the wrong thing xD)

---

### Post by nothingspecial on 2010-11-28
I`ve never done this so proceed with caution ... this is theory only

edit /etc/init/tty1.conf

and change the last line to
```

exec /bin/login -f user < /dev/tty1 > /dev/tty1 2>&1
```

Change user to the username of the user.

Then, instead of screen, use byobu (which is screen with added extras)

Start byobu as that user then press F9 for the settings menu

Select to start byobu at login

Then edit that users ~/.screenrc

and add a line

```
screen -t title 1 command
```

where title is the title of the window and command is what you want executed in in.

Like I say, this is theory only.

---

### Post by Pezmc on 2010-11-29
Is this the only way to do it? It seems very complex and I have no idea what it is doing!

---

### Post by nothingspecial on 2010-11-29
I tried it out of curiosity and it seems to work well.

The first command invokes the login utility that you would normally see when you login. The -f option tells login to not ask for the password, which it is able to do because root is running the script at boot. It is logging on a tty1. All the other ttys will remain as they were, in that a user will have to login with a password.

I used the byobu method because you can set it to autologin without editing anything, you just select the option from the settings menu.

The .screenrc  (amongst many things) can be used to autostart things when screen/byobu starts running. The format is

screen -t <name> <window> <command>

the -t option sets the "window name", then you which number window you would like starting from 0, then the command to start the program. Here is the relevant section of one of my .screenrcs
```

screen -t elinks 0 elinks
screen -t alpine 1 alpine
screen -t cmus   2 cmus
```and this is what it looks like

[ATTACH]176903[/ATTACH]

Yes, I am sure there are security implications, enabling auto login on a server, but that was your question.

I hope that clears iy up a bit.

---

