---
title: "nVidia driver installation"
date: 2010-06-29
forum: General Help
---

### Post by DeMus on 2010-06-29
Hi, I downloaded the latest nVidia run file, nr. 256.35 and want to install it. My videocard can work with this driver.
When I do the normal things to install the driver, ctrl-alt-F1, log in and try to stop gdm (/etc/init.d/gdm stop) I get a (for me) vague message that things have changed. I use Lynx btw.
I now have to use another instruction to stop the graphic system. Can somebody tell me exactly how to do that, or maybe show me another way to install the new driver?

Thanks.

---

### Post by Serpher on 2010-06-29
Put that driver script (.run) in your home folder and go to tty1 (Ctrl + Alt + F1). Execute the following commands:

```
sudo /etc/init.d/gdm stop
ls|grep *.run
sudo sh <output of last command>
```

---

### Post by DeMus on 2010-06-29
> **Serpher said:**
> Put that driver script (.run) in your home folder and go to tty1 (Ctrl + Alt + F1). Execute the following commands:

```
sudo /etc/init.d/gdm stop
ls|grep *.run
sudo sh <output of last command>
```

This is what I have used but then I get the vague message that I need to use another instruction to stop the graphic system.
I'm looking for the exact syntax for that instruction.

---

### Post by Serpher on 2010-06-29
> **DeMus said:**
> This is what I have used but then I get the vague message that I need to use another instruction to stop the graphic system.
I'm looking for the exact syntax for that instruction.

What does the message say? After you execute that command when pressing 'Ctrl + Alt + F7' bring you back to your graphical desktop?

---

### Post by DeMus on 2010-06-29
> **Serpher said:**
> What does the message say? After you execute that command when pressing 'Ctrl + Alt + F7' bring you back to your graphical desktop?

The message says:

Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service gdm stop. [COLOR="Blue"]This gets me: stop: unknown instance[/COLOR]

Since the script your are attempting to invoke has been converted to an Upstart job, you may also use the stop(8) utility, e.g. stop gdm  gdm stop/waiting.
[COLOR="Blue"]Stop gdm gets me: stop: unknown instance[/COLOR] 
gdm stop/waiting gave me too much text to write down.

Then ctrl-alt-F7 didn't work so I had to hard-reset the computer.

---

### Post by confused57 on 2010-06-30
I thought in Lucid it was:
```
sudo service gdm stop
sudo service gdm start
```

---

### Post by Serpher on 2010-06-30
> **confused57 said:**
> I thought in Lucid it was:
```
sudo service gdm stop
sudo service gdm start
```

Both do the same thing.
If Ctrl + Alt + F7 didn't do anything, X11 which is what needs to be shut down is. What does the driver installer tell you when you try to install it after disabling X11?

---

### Post by Finalfantasykid on 2010-06-30
You could always use a PPA

[http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

---

### Post by DeMus on 2010-06-30
> **confused57 said:**
> I thought in Lucid it was:
```
sudo service gdm stop
sudo service gdm start
```

I typed what you wrote and now it worked. So this is the new syntax. Is there some info somewhere about this? I mean, I am probably not the only one who has problems with this.

Thanks for your help, it's great to have a forum like this.

---

### Post by Serpher on 2010-06-30
This is why I left Ubuntu for Fedora. The message seems to be in the error message the previous script gave.

---

