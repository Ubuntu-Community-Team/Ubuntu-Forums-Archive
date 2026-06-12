---
title: "Show history of reboots on login"
date: 2010-06-15
forum: General Help
---

### Post by braunshedd on 2010-06-15
I was wondering if there was a script that would run on log in telling me the history of when the server was rebooted or such, along with the last user and motd (which is a roflcopter in my case:lol:)

---

### Post by iponeverything on 2010-06-15
```
last -20
```

will show the last 20.

---

### Post by braunshedd on 2010-06-15
yes, but how do i make it show that automatically when i log in, like when it displays the last logged on user?

---

### Post by Smart Viking on 2010-06-15
> **braunshedd said:**
> yes, but how do i make it show that automatically when i log in, like when it displays the last logged on user?

You go to "startup applications" or whatever it's called and you press "add", and where it says "command" you type: "last -20". :)

---

### Post by braunshedd on 2010-06-15
> **Smart Viking said:**
> You go to "startup applications" or whatever it's called and you press "add", and where it says "command" you type: "last -20". :)
but i'm not using gnome or kde, just the base shell. I guess i should have mentioned i'm using the server edition.

---

### Post by howefield on 2010-06-15
> **braunshedd said:**
> I guess i should have mentioned i'm using the server edition.

You did, it was presumtuous to assume that you were running a GUI.

I don't know much about the server edition, but how about something like this ?

[http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://embraceubuntu.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

It is an old page but looks relevant with current comments.

---

### Post by renkinjutsu on 2010-06-15
put your script in the file ```
/etc/profile
```
or put your script into the directory ```
/etc/profile.d
```

---

### Post by braunshedd on 2010-06-15
as you can tell, i'm a newbie, so i will need some more help. i put last -20 into the profile file and it didn't do anything, and i put a file in the profile.d that was the same thing, but once again, there was no difference. What am i doing wrong?

---

### Post by renkinjutsu on 2010-06-21
You put the file into the profile.d directory, but you probably have to make it an executable file too.. ```
chmod +x /etc/profile.d/yourfile
```
You may have to use 'sudo' for that

```
sudo chmod +x /etc/profile.d/yourfile
```

---

