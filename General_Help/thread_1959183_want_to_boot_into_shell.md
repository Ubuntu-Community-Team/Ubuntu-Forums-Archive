---
title: "want to boot into shell"
date: 2012-04-15
forum: General Help
---

### Post by nepalnt21 on 2012-04-15
well im trying to get lubuntu to allow me to boot into the shell instead of going into the gui login screen immediately upon booting. 

ive tried removing gdm, lightdm, and lxdm using

**update-rc.d -f ?dm remove**

which works in debian

lxdm still shows up in the init.d directory.

how can i rename the file?

what other ways are there of getting my lubuntu to boot into the command line upon start up?

thanky

---

### Post by sisco311 on 2012-04-15
What version are you running?

---

### Post by nepalnt21 on 2012-04-15
11.10

---

### Post by sisco311 on 2012-04-15
You can use an [.override]("http://upstart.ubuntu.com/cookbook/#override-files") file to disable the lxdm [Upstart job]("http://upstart.ubuntu.com/"):
```
echo "manual" | sudo tee /etc/init/lxdm.override
```

If you want to re-enable the Upstart job, then delete the file:
```
sudo rm -i /etc/init/lxdm.override
```

---

### Post by nepalnt21 on 2012-04-15
are 

**echo "manual**

and **sudo tee /...**

seperate commands?

---

### Post by jerome1232 on 2012-04-15
Yes, but they are on the same line, the "|" symbol is a pipe. It directs the output of one command to the input of another.

---

### Post by ajgreeny on 2012-04-15
They are separate commands but typed in the way shown, in a single command with the | in between, the word **manual** is "piped" to the tee command and added to the file shown [B]/etc/init/lxdm.override.

[/B]The| is the pipe character.

---

### Post by nepalnt21 on 2012-04-15
i dont think my computer has that symbol...

i tried the "tee etc..." command by itself and the terminal froze

---

### Post by jerome1232 on 2012-04-15
shift+ the key above enter on a standard US keyboard.

You could just copy and paste it.

---

### Post by nepalnt21 on 2012-04-15
ah ok it is that key... now that ive gotten the command to work, my machine boots to a black screen

---

### Post by sisco311 on 2012-04-15
> **nepalnt21 said:**
> ah ok it is that key... now that ive gotten the command to work, my machine boots to a black screen

Try to press Ctrl+Alt+F1 (or Ctrl+Alt+F2), in order to switch to a virtual terminal.

---

### Post by nepalnt21 on 2012-04-15
ah too late im already installing lubuntu again... i had everything i wanted, i think im just gonna suck it up and use it like it wants to be used for now

---

