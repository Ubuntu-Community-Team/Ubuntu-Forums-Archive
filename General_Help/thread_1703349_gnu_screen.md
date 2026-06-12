---
title: "gnu screen"
date: 2011-03-09
forum: General Help
---

### Post by vivek.pandey on 2011-03-09
hey everyone
    i started screen by typing screen in my terminal, started another terminal by C-a C-c and started processes in various terminals like irssi in one etc . right till here... now my question is it possible to create a terminal which shows me a list of all the processes i started through screen when i type some key combo..like ls-l lists the file one in a line
please help
thanx to all

---

### Post by idoitprone on 2011-03-09
ps -ef
man ps 
ps prints processes on your computer

if you a certain process pipe it to grep
finding all process tty
ps -ef | grep tty

---

### Post by vivek.pandey on 2011-03-09
> **idoitprone said:**
> ps -ef
man ps 
ps prints processes on your computer

if you a certain process pipe it to grep
finding all process tty
ps -ef | grep tty

thanx for your reply but ps -ef lists all the processes running on my system and not the screen specific also i want that whenever i start a new process in screen it gets lisred in the terminal which lists the screen processes

---

### Post by nothingspecial on 2011-03-09
If I understand you correctly you want Ctrl-A "

If I may suggest, try byobu which is ubuntus funked up version of screen. It gives you a window list at the bottom sort of like what you get on a panel.

You can then name each window/process with the F8 button. You move between them with F3 and F4 and create a new one with F2

All the normal screen key combos work.

You can also automate this by editing your screenrc like this
```

screen -t irssi 0 irssi
screen -t squeeze 1 squeezeslave -k 10 -D 192.168.1.11
screen -t web 2 elinks
screen -t mail 3 alpine
```

The first entry after -t names the window, the second one is which number window and the third is the process you want to start in it.

[ATTACH]185547[/ATTACH]

---

### Post by vivek.pandey on 2011-03-09
> **nothingspecial said:**
> If I understand you correctly you want Ctrl-A "

If I may suggest, try byobu which is ubuntus funked up version of screen. It gives you a window list at the bottom sort of like what you get on a panel.

You can then name each window/process with the F8 button. You move between them with F3 and F4 and create a new one with F2

All the normal screen key combos work.

You can also automate this by editing your screenrc like this
```

screen -t irssi 0 irssi
screen -t squeeze 1 squeezeslave -k 10 -D 192.168.1.11
screen -t web 2 elinks
screen -t mail 3 alpine
```

The first entry after -t names the window, the second one is which number window and the third is the process you want to start in it.

[ATTACH]185547[/ATTACH]

thanx for your reply 
seems you have a pretty good knowledge about screens can you please suggest few websites or books to know more about it.. i googled but got articles which i couldnt understand.. so please
thanx again

---

### Post by nothingspecial on 2011-03-09
What do you want to do?

I use it every day :D

This will help

[http://sunsite.ualberta.ca/Documentation/Gnu/screen-3.9.4/html_chapter/screen_toc.html](http://sunsite.ualberta.ca/Documentation/Gnu/screen-3.9.4/html_chapter/screen_toc.html)

---

### Post by vivek.pandey on 2011-03-09
> **nothingspecial said:**
> If I understand you correctly you want Ctrl-A "

If I may suggest, try byobu which is ubuntus funked up version of screen. It gives you a window list at the bottom sort of like what you get on a panel.

You can then name each window/process with the F8 button. You move between them with F3 and F4 and create a new one with F2

All the normal screen key combos work.

You can also automate this by editing your screenrc like this
```

screen -t irssi 0 irssi
screen -t squeeze 1 squeezeslave -k 10 -D 192.168.1.11
screen -t web 2 elinks
screen -t mail 3 alpine
```

The first entry after -t names the window, the second one is which number window and the third is the process you want to start in it.

[ATTACH]185547[/ATTACH]

thanx for your help
i read the documentation but i found it bit tough as i am not that geeky guy and started to use screen today only.. it would be helpful if i get to start from zero level.
i tried some commands like title but its not working says title:command not found
so can you please help me out now

---

### Post by nothingspecial on 2011-03-09
To set a windows title in normal screen do Ctrl-A A

That's capital/upper case A (ie shift-A)

Then Ctrl-A " will list it

---

### Post by vivek.pandey on 2011-03-09
> **nothingspecial said:**
> To set a windows title in normal screen do Ctrl-A A

That's capital/upper case A (ie shift-A)

Then Ctrl-A " will list it

i am using byobu.to set window title i just used f8.but that still doesnt solve m problems . i havent yet understood full utility of screen and so cant make out something sugnificant from it other then startin a new window and then navigating from one to other or assigning them title..even byobu cant solve the original problem i had of listing the proesses

---

### Post by vivek.pandey on 2011-03-10
is it possible to browse net using screen?
like i wanna google or see ubuntu forum pages or my email etc?

---

### Post by nothingspecial on 2011-03-10
I think you are missing what screen is.

It is a terminal multiplexer, think of it like a desktop environment.

You can browse the internet from within screen with a text browser such a elinks. You can play music and do your irssi. You can even split it so that you can view multiple windows at once.

---

### Post by vivek.pandey on 2011-03-10
> **nothingspecial said:**
> I think you are missing what screen is.

It is a terminal multiplexer, think of it like a desktop environment.

You can browse the internet from within screen with a text browser such a elinks. You can play music and do your irssi. You can even split it so that you can view multiple windows at once.

yes you are quite right..i know very little about it..just started to learn yesterday...i searched on net but couldnt get a useful info regarding surfing net. as far as i know its quite like a terminal not big difference what i found different was all terminals are kinda attached. dont know right or wrong ..actually yesterday one of my class mates who is in one of the clubs in our college using ssh and the club server browsed net in our lab which is connected with lan to the  server..when i asked him how you did he said learn gnu screen

---

### Post by nothingspecial on 2011-03-10
Have a go at elinks. If you want to learn about text based apps I suggest you start here. 

[http://kmandla.wordpress.com/howtos/](http://kmandla.wordpress.com/howtos/)

---

