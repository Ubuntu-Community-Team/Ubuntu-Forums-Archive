---
title: "making background apps persist even after terminal has closed"
date: 2010-03-16
forum: General Help
---

### Post by yawnmoth on 2010-03-16
If you open a new terminal, do "firefox &" and then close the terminal Firefox will close, as well.  Is there a way to make background apps persist even if the terminal has closed?

---

### Post by bodhi.zazen on 2010-03-16
You can try :

disown
screen
nohup
dtach

screen is uses most often when connecting via ssh.

nohup and dtach are probably easiest.

nohup firefox &

dtach -c /tmp/firefox firefox &

See :

[http://www.pixelbeat.org/docs/screen/](http://www.pixelbeat.org/docs/screen/)

[http://www.nslu2-linux.org/wiki/HowTo/KeepRemoteConsoleSessionRunning](http://www.nslu2-linux.org/wiki/HowTo/KeepRemoteConsoleSessionRunning)

[http://www.digipedia.pl/man/doc/view/dtach.1/](http://www.digipedia.pl/man/doc/view/dtach.1/)

---

### Post by yawnmoth on 2010-03-16
When I do "bash -c "nohup ping 127.0.0.1 &"" in one Terminal window I see it in another by doing "ps -a".  I then close the terminal window I did ping in and do "ps -a" in the second terminal window and now no longer see ping.

After installing dtach, "dtach -c /temp/foozle -Ez "ping 127.0.0.1"" produces the following error message:

dtach: could not execute ping 127.0.0.1: No such file or directory

---

### Post by bodhi.zazen on 2010-03-16
These tools are used for different things, so pick a tool you wish for the task you wish.

```
nohup ping localhost &
```works.

```
nohup xeyes &
nohup firefox &
```all work.

Do you need assistance with dtach ?

```
dtach -c /tmp/ping -z ping localhost
```

Then hit Ctrl - \

close the terminal

---

