---
title: "Nautilus embedded terminal"
date: 2009-07-14
forum: General Help
---

### Post by sirjoebob on 2009-07-14
First, I am NOT trying to embed a terminal to my desktop.

I am looking for something that will embed a terminal into a nautilus file browsing window that will "follow" where I browse to. Meaning I want it to update the directory to current Nautilus working directory. I often have to go to command for doing root-level file actions and don't want to have to use "open terminal here." Does anyone know if this is possible? Would be a fun tool for me to have.

---

### Post by juancarlospaco on 2009-07-14
**[nautilus-gksu]("apt:/nautilus-gksu")**

---

### Post by wojox on 2009-07-14
Why don't you just

```
gksudo nautilus
```

---

### Post by sirjoebob on 2009-07-14
I would rather do some operations from terminal. Just preference I guess....

---

### Post by prshah on 2009-07-14
> **sirjoebob said:**
> 
I am looking for something that will embed a terminal into a nautilus file browsing window that will "follow" where I browse to.

I don't know about nautilus, but the dolphin file browser in KDE4.1 has this feature.. can you install dolphin in your Gnome installation and see if it works for you? (See attached screenshot, along the bottom. Note the "cd /bin" command was automatically placed by Dolphin when I changed folders by clicking on /bin")

---

### Post by sirjoebob on 2009-07-14
> **prshah said:**
> I don't know about nautilus, but the dolphin file browser in KDE4.1 has this feature.. can you install dolphin in your Gnome installation and see if it works for you?

I may give that a try. I do rely on some nautilus integration stuff though... Great suggestion.

---

### Post by Operan on 2009-07-14
> **sirjoebob said:**
> First, I am NOT trying to embed a terminal to my desktop.

I am looking for something that will embed a terminal into a nautilus file browsing window that will "follow" where I browse to. Meaning I want it to update the directory to current Nautilus working directory. I often have to go to command for doing root-level file actions and don't want to have to use "open terminal here." Does anyone know if this is possible? Would be a fun tool for me to have.

You should use Ubuntu Tweak or Nautilus Action Configuration to add Open Terminal to context menu.

---

### Post by sirjoebob on 2009-07-14
> **Operan said:**
> You should use Ubuntu Tweak or Nautilus Action Configuration to add Open Terminal to context menu.

I have this already but would like an in-window terminal for quick and dirty tasks.

---

### Post by kogger on 2009-07-14
Let me know if you get this to work. It sounds awesome.

---

### Post by anton_mellit on 2010-05-20
Hey, I was thinking about what I waste my time on and realized that it is very inconvenient that terminal and nautilus are not integrated. 

Normally I have lots of terminal tabs and windows and lots of Nautilus ones, and I use terminal history a lot, and sometimes some open ssh sessions, so I cannot close terminal, but also sometimes I copy files by nautilus, or open them from nautilus for editing. It is so annoying to type "cd blah-blah-blah" in terminal or when I see a file in Nautilus to copy and paste its name/full path to the terminal. And I have to keep track of which terminal tabs are open in which directories.
So I was thinking about it, recalled good old times of Norton commander, tried Midnight commander, so I had this ideas: 

[LIST]
[*]The best things in NC/MC were Ctrl+O to switch from panels to shell and back and Alt+Enter to copy file name to the command line
[*] The two-panelness of NC/MC is not good - with time people started to use single-panel file managers, which effectively is multi-panel because now you can have as many directories open as you want, not just two
[*] MC cannot have drag-and-drop for files. Also it doesn't know gnome's file associations. Also it is text-mode.
[/LIST]
 
So I got an idea very similar to yours. I was happy that I found your post but unhappy that nobody implemented it. 

I spent yesterday evening on playing with nautilus sources and made some "mock/up" thing - I modified nautilus to include an input box below the main view:
[ATTACH]157653[/ATTACH]

As you see I type "make". If I press "Enter" the command executes. I can see the result if I press Ctrl+o:
[ATTACH]157654[/ATTACH]

I don't know how to handle switching of directories better. If I change directory in the nautilus it doesn't change directory in the terminal. I may simply send "cd <directory>" to the terminal, but if the terminal is running a program this program will receive just the string "cd <directory>", which is not what we want. 

Is anyone still interested in this?

---

### Post by ubun_two on 2010-05-20
I would definitely find this useful!

---

### Post by fmoralesc on 2010-05-20
Yes, this would be super useful. Thanks for the effort!

---

### Post by Looney on 2010-05-30
Me too! Me too! I've searched entire internet for this, so I would be very grateful if you could share the solution. :)

---

### Post by vodsdarov on 2010-07-12
I would love to have a terminal integrated in Nautilus, like Krusader does.

[IMG]http://www.freesoftwaremagazine.com/files/www.freesoftwaremagazine.com/nodes/3030/Krusader_with_embedded_terminal.jpg[/IMG]

---

### Post by clockworkpc on 2010-08-26
I'd find this very useful too!  Please let us know if something like this is developed.

---

### Post by Vaphell on 2010-08-26
agreed, that would be an awesome feature to have. Even stupid gedit can get embedded terminal with plugin.

---

### Post by FLOZz on 2010-09-07
I am working on a plugin that provides an embedded terminal for nautilus.

**Screenshot:** *(click for enlarge)*

[[IMG]http://software.flogisoft.com/nautilus-terminal/img/screenshot_nautilus_thumb.png[/IMG]]("http://software.flogisoft.com/nautilus-terminal/img/screenshot_nautilus.png")

**Project page on launchpad:** [https://launchpad.net/nautilus-terminal](https://launchpad.net/nautilus-terminal)
**Project website:** [http://software.flogisoft.com/nautilus-terminal/](http://software.flogisoft.com/nautilus-terminal/)

If it can be useful for someone :)

---

### Post by Smart Viking on 2010-09-07
> **FLOZz said:**
> I am working on a plugin that provides an embedded terminal for nautilus.

**Screenshot:** *(click for enlarge)*

[[IMG]http://software.flogisoft.com/nautilus-terminal/img/screenshot_nautilus_thumb.png[/IMG]]("http://software.flogisoft.com/nautilus-terminal/img/screenshot_nautilus.png")

**Project page on launchpad:** [https://launchpad.net/nautilus-terminal](https://launchpad.net/nautilus-terminal)
**Project website:** [http://software.flogisoft.com/nautilus-terminal/](http://software.flogisoft.com/nautilus-terminal/)

If it can be useful for someone :)
Looked like an interresting project, translated to norwegian. :)

---

### Post by FLOZz on 2010-09-07
> **Smart Viking said:**
> Looked like an interresting project, translated to norwegian. :)

Thank you for the translation :)

---

### Post by FLOZz on 2010-09-09
Version 0.1 released !

You can download the source code, and get informations about the ppa here:
[http://software.flogisoft.com/nautilus-terminal/en/#download](http://software.flogisoft.com/nautilus-terminal/en/#download)

:)

---

### Post by FLOZz on 2010-09-15
Nautilus Terminal 0.5 is out today :
[https://launchpad.net/nautilus-terminal/+announcement/6752](https://launchpad.net/nautilus-terminal/+announcement/6752)

And for users of Nautilus Elementary, a good news too:
[http://www.webupd8.org/2010/09/nautilus-elementary-gets-embedded.html](http://www.webupd8.org/2010/09/nautilus-elementary-gets-embedded.html)

:)

---

### Post by Vrroom on 2010-09-16
Embedded terminal come with nautilus elementary now. Check this out: [http://www.ubuntuvibes.com/2010/09/nautilus-elementary-is-ready-for.html](http://www.ubuntuvibes.com/2010/09/nautilus-elementary-is-ready-for.html)

---

### Post by randoer on 2010-09-21
> **sirjoebob said:**
> First, I am NOT trying to embed a terminal to my desktop.

I am looking for something that will embed a terminal into a nautilus file browsing window that will "follow" where I browse to. Meaning I want it to update the directory to current Nautilus working directory. I often have to go to command for doing root-level file actions and don't want to have to use "open terminal here." Does anyone know if this is possible? Would be a fun tool for me to have.
+++++


Check the following web site
[http://software.flogisoft.com/nautilus-terminal/en/](http://software.flogisoft.com/nautilus-terminal/en/)
This embeds a terminal in each open pane of nautilus and follows as you change folders...

---

