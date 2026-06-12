---
title: "Terminal/password problem"
date: 2011-05-07
forum: General Help
---

### Post by robbie 348 on 2011-05-07
I tried Ubuntu 11.04 but didn't like it, so I re-installed 10.10. Now, when I open a terminal I can type the command no problem, but when it prompts me for my password, the cursor just blinks and won't allow me to enter anything. Any ideas other than trying another re-install? Thanks, Rob.

---

### Post by DanneStrat on 2011-05-07
> **robbie 348 said:**
> I tried Ubuntu 11.04 but didn't like it, so I re-installed 10.10. Now, when I open a terminal I can type the command no problem, but when it prompts me for my password, the cursor just blinks and won't allow me to enter anything. Any ideas other than trying another re-install? Thanks, Rob.

If you're using "sudo" for a command and

you're asked for password you won't be able

to see any characters being typed (not even a "*" character)

Just continue to type your password and press enter.

It is normal.

---

### Post by matt_symes on 2011-05-07
Hi

If you are interested in having * when you type your password characters into a terminal or console you can edit your sudoers file.

At a terminal enter

```
sudo visudo
```

Enter your password. This first time it will not be echoed to the screen.

If given the option, select nano as your default editor.

Find the line that says

```
Defaults        env_reset
```

and change to 

```
Defaults        env_reset,pwfeedback
```

Press ctrl + o to save and ctrl + x to exit. If you have made any errors visudo will not allow you to save the file until they are fixed.

You will then get output like this.

```
matthew@matthew-laptop:~$ sudo apt-get update
[sudo] password for matthew: **********
```

As has been explained, the reason nothing is echoed to the screen is for security reasons. This does confuse a lot of new users.

Kind regards

---

### Post by robbie 348 on 2011-05-07
Thanks guys, I guess I "mis-remembered"

---

### Post by DanneStrat on 2011-05-07
You're welcome!

---

