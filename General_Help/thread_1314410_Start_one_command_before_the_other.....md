---
title: "Start one command before the other...."
date: 2009-11-04
forum: General Help
---

### Post by danill2008 on 2009-11-04
I would like to run 2 commands on Ubuntu, but the trick is they must start on boot-up and the 1 command must be launched for the second one to launch, otherwise it will fail. I searched for crons, but nothing appropriate to what im doing. Does anybody know how I can run this?

Soyry, forgot to state that I want to delay the 2 commands, not run them on the same time.

---

### Post by squaregoldfish on 2009-11-04
The file /etc/local is a script that's run on startup. You can add your two commands in here, and they should run fine.

Steve.

---

### Post by wojox on 2009-11-04
You could create a bash script and then launch it from System > Preferences > Start Up Applications.

---

### Post by danill2008 on 2009-11-04
> **squaregoldfish said:**
> The file /etc/local is a script that's run on startup. You can add your two commands in here, and they should run fine.

Steve.

But can I make a delay in them?

---

### Post by squaregoldfish on 2009-11-04
> **danill2008 said:**
> But can I make a delay in them?

As with any script, rc.local will wait for each command to return control before the next one is run. So as long as your first command does all it needs to do before it returns, you'll be fine.

---

### Post by danill2008 on 2009-11-04
> **squaregoldfish said:**
> As with any script, rc.local will wait for each command to return control before the next one is run. So as long as your first command does all it needs to do before it returns, you'll be fine.

Do u also know the command that I can add for it to run in debug mode, instead of running it in the background on startup?

---

### Post by danill2008 on 2009-11-04
> **squaregoldfish said:**
> The file /etc/local is a script that's run on startup. You can add your two commands in here, and they should run fine.

Steve.

Where can I locate it? I opened terminal and cd'ed to /etc, but I cannot find it anywhere....

---

### Post by Barriehie on 2009-11-04
Might consider putting the script in ~/.config/autostart.  See [here](http://ubuntuforums.org/showthread.php?t=331406).

Barrie

---

### Post by danill2008 on 2009-11-04
> **Barriehie said:**
> Might consider putting the script in ~/.config/autostart.  See [here]("http://ubuntuforums.org/showthread.php?t=331406").

Barrie

And will the one command start only if the other one is launched?

---

### Post by aysiu on 2009-11-04
How about use the *&&*?

```
firstcommand && secondcommand
``` That way the second command won't execute until the first one has completed.

---

### Post by Barriehie on 2009-11-04
+1

> **aysiu said:**
> how about use the *&&*?

```
firstcommand && secondcommand
``` that way the second command won't execute until the first one has completed.

---

### Post by danill2008 on 2009-11-04
> **aysiu said:**
> How about use the *&&*?

```
firstcommand && secondcommand
``` That way the second command won't execute until the first one has completed.

Thnx for everyones help! but I would still like to know if there is a command or something to put with it, so I can run it in debug mode on startup?

---

### Post by Barriehie on 2009-11-04
> **danill2008 said:**
> Thnx for everyones help! but I would still like to know if there is a command or something to put with it, so I can run it in debug mode on startup?

If these are bash commands you're talking about running I'm not sure what you mean by 'debug mode'.  What you can do is pipe STDOUT and STDERR to files like this:

***command 1** 1>/path/somefilename 2>/path/somefilename* && ***command 2** 1>/path/somefilename 2>/path/somefilename*

1>/path/somefilename will pipe STDOUT to /path/somefilename
2>/path/somefilename will pipe STDERR to /path/somefilename

Barrie

---

