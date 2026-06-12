---
title: "how can you access the middle mouse button buffer?"
date: 2012-04-15
forum: General Help
---

### Post by F.G. on 2012-04-15
hi all,

so, this isn't really a support question, but didn't seem like a cafe question either. in my office there are ubuntu installations everywhere, on laptops and desktops alike. i use the middle mouse button buffer all the time to copy and paste things but have no idea how to access it on a laptop without a middle button. does anyone know if there is out of the box functionality to do this? or any other way to do this?

thanks for any replies.

ps. also, by any chance, does anyone know a way to access the output to a terminal, after it has been displayed? i keep finding that there is output that i can't easily recreate that i either want to keep, or to grep through, that kind of thing. any thoughts?

---

### Post by F.G. on 2012-04-16
bump: ..·'·..

seriously though, surely someone has had this issue before? it seems like the answer should be super simple (yet i have no idea what it is).

---

### Post by nothingspecial on 2012-04-16
On a laptop you would click both right and left click at the same time to replicate middle click.

You can redirect the output of terminal commands to a text file like so
```

my_fancy_terminal_command > output.txt 
```

---

### Post by F.G. on 2012-04-16
thanks for your reply, i'll try the left/right click the next time i have a chance, if it works that will be great (as i keep finding myself highlighting stuff, going to past it before realizing that i can't).

my question about the teminal buffer is slightly different, though. i want to access it *after* it has been outputted to the terminal. < and | work fine, but you need to know beforehand that this is what you need to do. if i'm looking at the output of a queue table, which is cleared every two minutes, decide that i want to grep through it however the data is no longer there, but is *it* still being displayed on my terminal i want to figure out how to access it. that is the kind of scenario i'm wondering about.

anyhow, thanks for the double button click tip. that will come in very handy.

---

### Post by nothingspecial on 2012-04-16
Maybe setting up tmux would help if I understand you correctly. Have a look at this

[http://blog.sanctum.geek.nz/vi-mode-in-tmux/](http://blog.sanctum.geek.nz/vi-mode-in-tmux/)

Of course you have to remember to run tmux :)

---

### Post by coldraven on 2012-04-16
This is not what you want but it might come in handy
[http://www.omgubuntu.co.uk/2012/04/how-to-record-and-share-terminal-screencasts-quickly/](http://www.omgubuntu.co.uk/2012/04/how-to-record-and-share-terminal-screencasts-quickly/)

---

### Post by evilsoup on 2012-04-16
I use xdotool. I can't remember if it was installed as default, but you should be able to get it with:

sudo apt-get install xdotool

From the commandline, this simulates the middle-click button with:

xdotool click 2

What I did (because the buttons on my trackpad are linked together, making it hard to press them both at the same time) was map a button (the 'menu' button in my case, being close to the trackpad) to use that command. In my version I had to go through 'SYSTEM->PREFERENCES->KEYBOARD SHORTCUTS', but I'm not sure how you get to it through Unity.

---

### Post by F.G. on 2012-04-18
hey all, sorry it took me a while to get back to you, thanks for the posts. the middle two buttons work perfectly for my purposes (don;t know how i didn't come across this before). i think tmux looks exactly like what i need for the other thing. just need to figure out if/how i can use it (eg. if you've ssh'ed to another machine will it work? (i assume no), also i don't have sudo access on most of the computers in question).  
anyhow thanks for all the advice.

---

### Post by ozviking on 2012-06-25
> **F.G. said:**
> hi all,

so, this isn't really a support question, but didn't seem like a cafe question either. in my office there are ubuntu installations everywhere, on laptops and desktops alike. i use the middle mouse button buffer all the time to copy and paste things but have no idea how to access it on a laptop without a middle button. does anyone know if there is out of the box functionality to do this? or any other way to do this?

thanks for any replies.

ps. also, by any chance, does anyone know a way to access the output to a terminal, after it has been displayed? i keep finding that there is output that i can't easily recreate that i either want to keep, or to grep through, that kind of thing. any thoughts?
 
Just press both left and right at the same time and you will paste,  just have what you like to copy highlighted

---

