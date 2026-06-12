---
title: "I need a script for copy to terminal"
date: 2011-01-25
forum: General Help
---

### Post by Johnny420 on 2011-01-25
I found this great script that let me add a open as admin option to my right click

[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s02.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/ch12s02.html)

so I was wondering if anyone knows of or can whip up a script that would let me highlight text for example on a web page right click and have an option to open and terminal and paste the text with one click.
Instead of highlighting text right clicking selecting copy, then opening terminal and pasting manually.
 just an idea I had for a time saver but what I have tried didnt work right

---

### Post by Vaphell on 2011-01-25
why don't you skip the right-click/copy and right-click/paste? they are not necessary you know
1. open terminal
2. highlight a command on a web page (i guess that's what you need the script for - to follow tutorials using the terminal)
3. middle-click paste the highlighted text in the terminal window
4. ???
5. profit

if you have browser and terminal windows side by side you can copy-paste dozens of commands line by line in a matter of seconds so your script won't save you much time to be worthy the effort.

it's a system wide feature and 99% of software supports highlight/middleclick. as long as you don't unselect the text, you can paste it pretty much everywhere. In fact the lack of it is killing me when i use windows from time to time.

---

### Post by Johnny420 on 2011-01-25
your right this is an easy way to do things but I do a lot of reading and some times I see something I want to try and I dont have a terminal open plus I am lazy

I also find myself middle clicking when I am on a windows machine...lol

---

### Post by Vaphell on 2011-01-25
> I dont have a terminal open

you are doing it wrong then ;P
Yes i am joking but only a little :) I like gui as much as the next guy but having a terminal open all the time is a real timesaver once you know the useful shortcuts.
Why bother clicking your way to the system monitor when ps/top/htop will tell you all you need to know about the apps and workload plus it won't skew the results of cpu%?
sudo apt-get install <name> is also faster than click, click, click, type password, scroll, click, click, click, apply. In fact i stopped using gui package managers because they have incoherent workflow - switching from mouse (run) to keyboard (password) to mouse (navigate) to keyboard (filter by keyword) to mouse (scroll/select/apply) takes a long time and it annoys me.
Terminal also has a history so rerunning a command (eg testing a program, playing with system settings or whatever) is all about tapping up arrow once or twice. Double-clicking/launcher stand no chance in such situations.

---

