---
title: "Ubuntu Shell Scripts"
date: 2010-03-27
forum: General Help
---

### Post by mcedata on 2010-03-27
Hi, I just installed Karmic on a Vaio laptop for a bud. The controls to brighten /darken the screen don't work.  I've worked out a way to adjust the screen, but it's a bit clumsy and requires running a shell script after every reboot. I'm wondering if there's an easier way. 

One of the confounds is that root owns the file I need to write to, so I have to change the owner of that file before I can write to it.   (/sys/class/backlight/sony/brightness)

So, I created a shell script with two lines...

sudo chown howard /sys/class/backlight/sony/brightness
sudo echo 7 > /sys/class/backlight/sony/brightness

...where 7 is the maximum screen brightness.

I have this script file on the desktop; clicking on it gives me a popup about running it, running it in terminal, or opening it. Running it in terminal does what I need it to do, though the first run after a boot also opens a terminal box and I have to enter the password. 

Is there an easier /better way to do this, perhaps calling the script at bootup, that will relieve me of having to run the script after boot...and a way that does not show me the "run, run in terminal, open" dialogue box or terminal box to enter the password?

Thanks for any suggestions.

Steve

---

### Post by krismatth3 on 2010-03-27
You could put these lines in /etc/rc.local.

---

### Post by falconindy on 2010-03-27
You can put this script in /etc/rc.local and it'll be executed on bootup. As rc.local is executed by root, you won't need sudo to do it.

FYI: In your script, the first command is unnecessary if you phrase the second a little differently. You're applying sudo to echo, which has no effect on the redirection. What you probably meant to do is the following:
```
echo 7 | sudo tee /sys/class/backlight/sony/brightness >/dev/null
```
This properly grants elevated permissions for the part of the operation that writes to the brightness file.

---

### Post by mcedata on 2010-03-27
Thanks to falconindy and krismatth3. Tried both of your suggestions, and they both worked. Thanks for the help!

One tiny thing, however...falconindy, your suggestion works, but I don't know why. <g>  Could you explain what that line does?  I'm not familiar with the use of the "|" symbol, or the "tee", or >/dev/null. I've been using Ubuntu for several years, but have just started to get into the "under the hood" stuff like scripting.

echo 7 | sudo tee /sys/class/backlight/sony/brightness >/dev/null

Thanks again,

Steve

---

### Post by falconindy on 2010-03-27
| is a pipe. This redirects the output of one command to the input of another. Echo would normally output to stdout. Instead, we're sending it to the program 'tee'. Tee's job is to write to both stdout as well as a file. Here, we've chosen to write to '/sys/class/...' . I don't really care about anything being written to stdout though, so I redirect (the > character) stdout to the bit bucket /dev/null which is basically a black hole.

To learn more about Bash...
[http://www.ibm.com/developerworks/library/l-bash.html](http://www.ibm.com/developerworks/library/l-bash.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)

---

### Post by mcedata on 2010-03-28
Falconindy:

OK, I see the logic. Thanks for the explanation.

Steve

---

