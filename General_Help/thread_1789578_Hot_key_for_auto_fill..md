---
title: "Hot key for auto fill."
date: 2011-06-24
forum: General Help
---

### Post by FrankenCub on 2011-06-24
I am an administrator on another site and frequently add a short html script to new members profiles. Is there a way I can set a key to automatically post the saved script without having to constantly copy/past or writing it ?

---

### Post by Vaphell on 2011-06-24
what does the procedure look like when done manually? probably you can write a script to automate the task.

---

### Post by FrankenCub on 2011-06-24
The code itself is pretty simple...
```
<b>Hello and welcome to the site :). Below are a couple of links to get you started if you need assistance:</b><br />
<br />
<a href="http://######.net/page/new-member-guide-getting">http://######.net/page/new-member-guide-getting</a>;<br />
<br />
<a href="http://######.net/group/newtothissite">http://######net/group/newtothissite</a>;;<br />
<br />
<b>Please make yourself at home!</b><br />
<br />
<p style="text-align: left;"><img src="http://api.ning.com/files/erTcJ*TVkzfvTn7tNSxFAg1dI1K9JlPHlrfCa5Fn6FldnZHzRocH1wN0GgfD3jmzi2rZRZqwiYQX9ItGCSLk*7ZzFMafWRXz/sunheart.jpg" /></p>
```

I would imagine I would have to save it to a text file but beyond that I'm not to familiar with doing the rest.

---

### Post by Vaphell on 2011-06-24
content of the hmtl file itself is not important, what you do to put it in user's profile is - how do you access the remote server and how do you modify the contents of user account?

---

### Post by FrankenCub on 2011-06-24
I just copy it from a private page in my profile then past it into a comment box on their profile. No different than posting a comment here in this discussion. If that's what you mean...

---

### Post by Vaphell on 2011-06-24
at first i thought it's about copying some html file to some user dir, now it's clear.

i played a little with it and i think i have found a way
1. install xdotool and xclip
```
sudo apt-get install xdotool xclip
``` 
2. create a html file with the welcome message and a script doing the actual magic
```
#!/bin/bash

#copy html file to clipboard 
cat /home/username/welcome.html | xclip -i

#simulate middle-click (paste)
xdotool click 2
```
3. go to hotkeys configuration in Preferences menu, add custom hotkey, for example CTRL+F12 and in command field put
```
/home/username/my_magic_script
```

---

### Post by FrankenCub on 2011-06-24
Thanks Vaphell ! I went a read up on those and I think I see how they work. I get a little lost with all the things that can be done with Ubuntu, but I'm learnin lol. I will give this a try here in a few minutes, will let you know how I make out.

---

### Post by FrankenCub on 2011-06-24
Sweet, it works pretty good, once I figured out a couple things that I was doing wrong LOL. The biggest #-owas forgetting to make the "magic script" file executable. I kept getting an error and looked at everything for 20 minutes wondering what I did wrong LOL.
I gotta drive that "executable" into my head :p

Thanks a million Vaphell !!

---

### Post by CharlesA on 2011-06-24
I was going to suggest looking into greasemonkey to do that for you, but I wouldn't know where to start tbh.

---

### Post by FrankenCub on 2011-06-25
I'll take a look at that one too, if anything I'll know about it for future reference. Thanks ;)

---

