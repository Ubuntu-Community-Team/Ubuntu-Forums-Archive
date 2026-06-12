---
title: "Multiple terminal in Server"
date: 2011-03-09
forum: General Help
---

### Post by gpdas on 2011-03-09
Hello
I am using Ubuntu 10.04 Server as my web server. I need to run Kannel for sending SMS. This require two programs i.e bearerbox and smsbox to be run. In case of Redhat I do this by opening 2 terminals. How can I do this in Ubuntu server which has no GUI.
Any help will be highly appreciated.

---

### Post by prshah on 2011-03-09
> **gpdas said:**
> do this by opening 2 terminals. How can I do this in Ubuntu server which has no GUI.

You can use Ctrl+Alt+F1..F6 to switch between virtual terminals. Another option is to use screen (especially if you are connected via ssh); get it from the repositories using ```
sudo apt-get install screen
``` and check the man page for detailed usage. Summary: the "screen" command will open a new terminal; to leave without closing, use Ctrl+A, Ctrl+D; other commands```
screen -r # open last screen session
screen -r $PID # open screen session with process ID $PID
screen -list # list active screens

```

---

### Post by gpdas on 2011-03-15
I want to do it without installing screen. I would like to run commands in the background without showing the output i.e Non-verbose mode. Pl help.

---

### Post by jerome1232 on 2011-03-15
Here's a little guide about controlling processes, you can background processes, bring them to the foreground and etc using standard gnu tools.

Forgot to link the guide!

[http://linux.about.com/od/itl_guide/a/gdeitl35t01.htm](http://linux.about.com/od/itl_guide/a/gdeitl35t01.htm)

edit: You also have multiple tty's you can use, usually ctrl+f1 - f6

---

### Post by wojox on 2011-03-15
> **gpdas said:**
> In case of Redhat I do this by opening 2 terminals.

Yes it's "screen" your running on RHEL. There is also [tmux]("http://tmux.sourceforge.net/"). As well as 
what jerome1232 posted about sending jobs to the background.

---

### Post by gpdas on 2011-03-15
If I put a  '&'  in the last, the process runs in the background. But the output lines are displayed like Pop-ups.

---

### Post by jerome1232 on 2011-03-15
You may need to redirect std output and maybe std error to /dev/null, or if you need to see the output at a later date to a file.

examples (if I remember this correctly)

```
programname > /dev/null &
```

Here's a small guide that gives more details about redirection.

[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-3.html)


You could also take advantage of your other tty's, that would be the equivalent of opening a second terminal in a gui.

---

### Post by yifangt on 2011-05-02
Click the Ubuntu logo on the left top corner, then click "More app" icon, then the "Terminal" icon, you can get as many terminals as you can. This is really inconvenient, hopefully there is a new way to do it. 

By the way, I am very surprised that "Natty Narwhal" could not create the "shortcut" and pin the shortcut in top bar of the window. In another forum it is said this is the way for Ubuntu 11.04. However, my feeling is any newer version should inherit the good part of the old version, right? I start to doubt Ubuntu is going down in the future from this little function, which disgard the good part of old versions.

---

### Post by jerome1232 on 2011-05-02
> **yifangt said:**
> Click the Ubuntu logo on the left top corner, then click "More app" icon, then the "Terminal" icon, you can get as many terminals as you can. This is really inconvenient, hopefully there is a new way to do it. 

By the way, I am very surprised that "Natty Narwhal" could not create the "shortcut" and pin the shortcut in top bar of the window. In another forum it is said this is the way for Ubuntu 11.04. However, my feeling is any newer version should inherit the good part of the old version, right? I start to doubt Ubuntu is going down in the future from this little function, which disgard the good part of old versions.

Were talking about a cli only server, as for your post you can just middle click the icon on your launcher, no need to go through menu's.

---

