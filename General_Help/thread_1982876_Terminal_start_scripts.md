---
title: "Terminal start scripts?"
date: 2012-05-19
forum: General Help
---

### Post by Foxboron on 2012-05-19
Helluw!
So i was looking trough a thread with screenshots of people's desktops.
I keep seeing people having some rather "fancy" startup scripts for their terminals, but i cant manage to google my way to actually figure out what kind of scripts they are running!

[http://ubuntuforums.org/attachment.php?attachmentid=216991&d=1335838153](http://ubuntuforums.org/attachment.php?attachmentid=216991&d=1335838153)
That is the one i am after. I keep seeing several people running ArchLinux displaying it on their terminal.

Thanks for the help!

---

### Post by roelforg on 2012-05-19
Modify ~/.bashrc
It runs on every terminal launch

---

### Post by Foxboron on 2012-05-19
> **roelforg said:**
> Modify ~/.bashrc
It runs on every terminal launch

Yes, i do know that. But i was wondering what scripts they are using to achive that display of system information.

---

### Post by roelforg on 2012-05-19
> **Foxboron said:**
> Yes, i do know that. But i was wondering what scripts they are using to achive that display of system information.

Then i misunderstood the question, sorry.
I think they wrote those themselves.
I'll see if i can get you something similar, give me a few minutes!

---

### Post by rubylaser on 2012-05-19
That is done with Conky.  Here are some [simple examples]("http://www.omgubuntu.co.uk/2011/05/five-beautifully-simple-conky-themes/") and some other [fancier ones]("http://www.omgubuntu.co.uk/2011/01/five-seriously-cool-conky-set-ups-for-linux-desktop/").  The terminal window is nice, but seems completely unnecessary to me and kind of defeats the purpose of a minimal terminal window.

---

### Post by Cheesemill on 2012-05-19
> **rubylaser said:**
> That is done with Conky.  Here are some [simple examples]("http://www.omgubuntu.co.uk/2011/05/five-beautifully-simple-conky-themes/") and some other [fancier ones]("http://www.omgubuntu.co.uk/2011/01/five-seriously-cool-conky-set-ups-for-linux-desktop/").  The terminal window is nice, but seems completely unnecessary to me and kind of defeats the purpose of a minimal terminal window.
I don't think that it's anything to do with conky.
Foxboron is after the script that runs when the terminal is started.

---

### Post by rubylaser on 2012-05-19
> **Cheesemill said:**
> I don't think that it's anything to do with conky.
Foxboron is after the script that runs when the terminal is started.

I re-read the first post.  You are correct, I thought the OP was asking how to setup the whole look.  Conky is used for the sidebar.  A motd is used for the terminal ascii art and the rest are just echoing system info to the window. Here are some [ideas.]("http://blog.0x1fff.com/2011/01/creating-ascii-art-motd.html")

---

### Post by roelforg on 2012-05-19
[http://ubuntuforums.org/showthread.php?t=679762&page=2](http://ubuntuforums.org/showthread.php?t=679762&page=2) (ice60's post)
Is that what you're meaning?

---

### Post by rubylaser on 2012-05-19
> **roelforg said:**
> [http://ubuntuforums.org/showthread.php?t=679762&page=2](http://ubuntuforums.org/showthread.php?t=679762&page=2) (ice60's post)
Is that what you're meaning?

No, those options are just a part of what the OP is looking for.  They're just setting aliases and terminal colors. But, those are a start :)

---

### Post by roelforg on 2012-05-19
> **rubylaser said:**
> No, those options are just a part of what the OP is looking for.  They're just setting aliases and terminal colors. But, those are a start :)

No, a start is what i've done to my terminal:
I modded the bashrc from [http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/](http://ayozone.org/2008/02/25/bash-fancy-prompt-and-improvments/)
i mostly did some colour adjustments.

---

### Post by Foxboron on 2012-05-19
I have yet to find what i am looking after, but this is atleast a great start! Now i actually KNOW what i am looking for!

I did however add a fortune | cowsay in my MOTD :)

Thanks for the help!

:popcorn: <- for you guys!

---

### Post by roelforg on 2012-05-19
I made the script for you (and for myself b/c i like it).
There are a few things about it:
You need php5 (IMO php is the king in websites and advanced string ops) and wmctrl
And it assumes a resolution of 1280x800+ and a maximized terminal (you can modify the launcher for that).

I added a screenshot (the prompt is kinda weired because i modded it, not part of the script).

Using it is simple, assuming you saved the script to ~/logo.sh and made it executable.
Append
```

~/logo.sh

```
to .bashrc

It looks kinda good, doesn't it?
The php script is a little hackish but it works.
I used jp2a to create the logo and then added the colors myself.
Adding extra info to the box is easy, the code for that kinda explains itself.

I'm kinda proud of it, though.

---

### Post by jon zendatta on 2012-05-19
[http://ubuntuforums.org/showthread.php?t=614743]("http://ubuntuforums.org/showthread.php?t=614743"):KS

---

### Post by roelforg on 2012-05-19
> **jon zendatta said:**
> [http://ubuntuforums.org/showthread.php?t=614743](http://ubuntuforums.org/showthread.php?t=614743):KS

The OP was talking about the script on the shot that printed the ubuntu logo and system info.

---

### Post by Foxboron on 2012-05-20
Thanks roelforg for writing that script :)

So after a visit on IRC i was told it was Archey!
Linkey:
[https://bbs.archlinux.org/viewtopic.php?id=87610](https://bbs.archlinux.org/viewtopic.php?id=87610)

Its written in python, and it needs a little editing to display the Ubuntu logo but wont be to hard.

Shared the result and setting this thread as solved!

---

