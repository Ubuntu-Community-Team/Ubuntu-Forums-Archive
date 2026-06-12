---
title: "Randomly boots into command line?"
date: 2010-05-19
forum: General Help
---

### Post by lilwing89 on 2010-05-19
turns out this was a result of a failing PSU. has since been replaced.

---

### Post by utnubuuser on 2010-05-19
I'd try going through Startup Application/Programs in System, there is an option to "remember currently running applications/sessions".

---

### Post by lilwing89 on 2010-05-19
asdfadsafds

---

### Post by Catharsis on 2010-05-19
What happens when you type "startx"?

Also, what graphics card do you have?
```
lspci | grep VGA
```

---

### Post by Serpher on 2010-05-19
> **Catharsis said:**
> What happens when you type "startx"?

Also, what graphics card do you have?
```
lspci | grep VGA
```

startx isn't in Debian type distros. Instead of startx, use

```
sudo /etc/init.d/gdm start
```

---

### Post by Catharsis on 2010-05-19
"startx" works fine for me.

And while we're being pedantic, init.d scripts are deprecated; the preferred way is
```
sudo service gdm start
```
:P

---

### Post by tkoco on 2010-05-19
> **lilwing89 said:**
> I recently upgraded my mother's computer and I have her using Ubuntu now. I am a little nervous about this because I live kind of far away and I can't always be there to fix any problems she might have.

Problem #1 is that this morning, my mother tried to get on the computer the first time by herself. She pressed the power button on the front panel and instead of going to the graphical login, it went to a command line login.

I am on the computer right now. If it booted into command line I turned it off. After 2-3 times of manually rebooting, it went to the regular login screen. What's going on?

Not sure right off the top of my head, but if you look at the /var/log/Xorg.0.log file, you may find your answer in there. My best guess is that the GUI desktop is trying to startup, but there is some sort of problem which interferes with it. As already suggested above, you may want to try hand starting the GUI desktop and see what sort of error messages pop up in the command line screen.

---

