---
title: "HELP! What did I do?"
date: 2010-03-21
forum: General Help
---

### Post by Colo2 on 2010-03-21
I clicked on something and my desktop kinda crashed. So I restarted, Logged into my user, and the login screen background remains, the login boxes disappear and a white console terminal appears in the top left of the screen.

So its a white terminal box, about 9cm height and 9cm length in the top left of the screen.  .. thats it.

It wont load anything else. How can I fix this? :(

Please help

Thanks

---

### Post by patchwork on 2010-03-21
You're logged into an xterm session.  Type
```
killall -u user_name
``` to get back to the login screen.

Enter your login information, but before signing in, go to the Session box on the bottom of the screen.  Choose GNOME (or whatever desktop manager you're using), and then complete the login.

---

### Post by Colo2 on 2010-03-21
Hey, thanks for the reply. I dont see a session box at the bottom of the screen.

I have Language, keyboard and date and time. Theres also an button to bring up options such as on screen keyboard etc..

---

### Post by sandyd on 2010-03-21
type in your username, whack enter, and look again.

---

### Post by Colo2 on 2010-03-21
I clicked on my username in the list, and it asked me to type in my password. but never a session box

---

### Post by Colo2 on 2010-03-21
Oh crap.

I think something has gone terribly wrong...

[IMG]http://farm3.static.flickr.com/2454/4011216629_05ca3c7458.jpg[/IMG]

I pulled that picture from the internet. I can see the sessions box on that one, but mine doesn't have it!!! :(

---

### Post by Colo2 on 2010-03-21
Eugh, What do I do? :(

---

### Post by 98cwitr on 2010-03-21
can you access recovery mode in the grub menu @ boot? If so, you can run the command posted above from it, and then attempt to log in that way. Start your gui by running *sudo startx* once you have logged in from terminal.

---

### Post by Colo2 on 2010-03-21
I got into recovery console. I selected root   Drop to root shell prompt
Now I have a console. I typed - as you said - the command "killall -u tom"
I tried startx which created a black screen with just my cursor in the middle.

What to do now? :P

---

### Post by Colo2 on 2010-03-21
Ok.
Doing all that just produces a black screen with a cursor. No GNOME. I've also tried repairing broken packages, didn't work.


Any other ideas? :( I have spent hours working on this, I can't loose it, please :(

---

### Post by 98cwitr on 2010-03-21
what happens when you type in *sudo login tom* and enter your password? Also try running this command to make sure you have no gui errors ```
sudo apt-get install ubuntu-desktop
```

[http://ubuntuforums.org/showthread.php?t=66935](http://ubuntuforums.org/showthread.php?t=66935)

---

