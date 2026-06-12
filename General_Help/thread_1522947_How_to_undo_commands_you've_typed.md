---
title: "How to undo commands you've typed?"
date: 2010-07-02
forum: General Help
---

### Post by baxna on 2010-07-02
Hello, I was trying to install a particular program yesterday and couldn't get it to work. Is there a way to undo these commands that I tried (per the website's instructions)? They were from this website ([http://www.trgtd.com.au/index.php?option=com_content&view=article&id=45&Itemid=58#linux](http://www.trgtd.com.au/index.php?option=com_content&view=article&id=45&Itemid=58#linux)) for a program called "ThinkingRock." Don't know why the program didn't work, I did everything it said. Anyway here are the commands it said to type into a terminal:

> sudo -s
echo deb [http://ppa.launchpad.net/salutis/ubuntu](http://ppa.launchpad.net/salutis/ubuntu) intrepid main > /etc/apt/sources.list.d/salutis.list
aptitude update && aptitude install thinkingrock 

Thanks for your help!

---

### Post by CharlesA on 2010-07-02
You could have just used sudo instead of trying to use a root shell.

```
sudo apt-get purge thinkingrock
```

---

### Post by duanedesign on 2010-07-02
It also created a file /etc/apt/sources.list.d/salutis.list . If you no longer want to access this repository you can get rid of that file.

```
sudo rm /etc/apt/sources.list.d/salutis.list
```

---

### Post by baxna on 2010-07-02
Thanks very much. I'm still pretty new to all this & have no idea what a root shell is, but if the command window gave me this response:

> E: Couldn't find package thinkingrock

Then I guess everything's ok. I was just concerned that I enabled some obscure repository or something and I should ideally undo it.

---

### Post by CharlesA on 2010-07-02
When you typed this:

```
sudo -s
```

You started a root shell, which isn't needed when you use sudo. :)

As a new user, I would suggest sticking to the repos for the most part.

---

### Post by baxna on 2010-07-02
Thanks duanedesign, I saw your post after typing my response to CharlesA.

---

