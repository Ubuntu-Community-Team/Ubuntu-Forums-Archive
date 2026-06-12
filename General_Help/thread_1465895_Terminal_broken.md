---
title: "Terminal broken"
date: 2010-04-29
forum: General Help
---

### Post by resnak on 2010-04-29
Well, I think this is all my fault but I hope someone can help me sort this out.  It all started when I was trying to build a uClinux image and I was getting a problem where "make" couldn't open the .config file.  Based on previous similar issues it looked like my problem was that Ubuntu changed the symlink /bin/sh to point to /bin/dash instead of /bin/bash.  So, I decided to change it back to /bin/bash to solve this issue.

Shortly after this my computer slowed to a crawl and even moving the mouse was painfully slow.  However, I had several programs running including VMWare and Firefox with about 15 different tabs so I thought it might be one of them that was taking up too many resources.  When closing everything didn't solve the problem I decided to reboot the computer.

That's when the problem showed up.  When I open a terminal (gnome-terminal) my prompt is only "$" and when I enter commands and then press up or down arrows to go through the history, it just prints "^]]A" (or similar) instead.

I have been searching around and here is a summary of what I've determined so far:

/bin/sh points to /bin/dash after the reboot
echo $SHELL prints /bin/sh
ps $$ says "COMMAND" is "dash"

I have tried several fixes at this point and I've tried to remember to put everything back the way I found it when something didn't work but I can't guarantee I didn't forget some.

Any ideas??!

---

### Post by findspiderweb on 2010-04-29
As far as I know, bash and dash interpret things very differently. Your original problem with uClinux could probably have been solved by replacing /bin/sh with /bin/bash in the build scripts. 

As for your terminal, what happens when you do this? ```
$ bash
```

---

### Post by resnak on 2010-04-30
Yeah, I found Ubuntu's [wiki page]("https://wiki.ubuntu.com/DashAsBinSh") about why they use dash and how to fix scripts that don't specifically call bash when they should but I found it a little too late.

When I just type bash at the prompt and hit enter nothing happens.  It just returns back to an empty prompt with no errors or messages.

---

### Post by findspiderweb on 2010-05-01
If you type "bash" it should give you the bash shell. So,

ps $$ should say "bash"
up/down arrows should work here

If thats the case, you can make it permanent by running "ypchsh" and tell it to use /bin/bash. 

But the original bash shell doesn't do things like display your current directory on each prompt and doesn't have smart tab auto-complete. That happens through the .bashrc file under your home directory. Make sure its there and still has its contents. There's also a system-wide bash.bashrc in /etc. 

You can try messing with them to see if they're being run (ie. inserting an "echo hello world" in the beginning of the scripts).

---

