---
title: "Start Skype from terminal"
date: 2012-01-26
forum: General Help
---

### Post by Yumi on 2012-01-26
Sorry to ask this question, but I am in China and trying to access the Skype forum I am always diverted to a Chinese website. I do know the answer is there in the forum.

I need to open 2 Skype instances from the terminal and log in at the same time. Starting Skype is no problem, but what is the sytax to log in.

Thanks Michael

BTW Skype does not provide any assistance in China other than Chinese. Very user unfriendly!

---

### Post by wolfen69 on 2012-01-26
> **Yumi said:**
> Sorry to ask this question, but I am in China and trying to access the Skype forum I am always diverted to a Chinese website.
That is between you and your internet provider/government. 

> Starting Skype is no problem, but what is the sytax to log in.
You need to sign up for a username and password.

---

### Post by partloer on 2012-01-27
Getting to the forum might be because of recent [Chinese regulation]("http://en.wikipedia.org/wiki/Skype#Service_in_the_People.27s_Republic_of_China")

[More]("http://www.pcmag.com/article2/0,2817,2374898,00.asp")

Let me know if you are having problems connecting to Skype I am interested to hear if it is blocked.  One way around this is to use a VPN.

The command to launch Skype should just be ```
skype
``` But I don't know how to launch skype with the login credentials unless you have skype save your username and password.

---

### Post by WorMzy on 2012-01-27
```
echo username password | skype --pipelogin
```

---

### Post by Yumi on 2012-01-27
Thank you WorMzy, this was what I was looking for. It works. But never be satisfied - when I put this command into "Startup Applications" it does not. Would you also know how to modify this command for that purpose.

Skype is not blocked in China. But all URL's concerning Skype are diverted to "http://skype.tom.com/". This makes sense for local users but not for foreigners not able to cope with written Chinese.

Michael

---

### Post by WorMzy on 2012-01-28
Rather than putting the command itself into the startup list, try writing a script, making it executable, then adding the script to the list of startup applications.

e.g.

Make a new file in your home folder called .startskype and put the following text into it:
```
#!/bin/bash

echo username password | skype --pipelogin
```
Then run
```
chmod +x ~/.startskype
```

Then add that file to the list of start up applications.


Note: Files beginning with a "." don't show up unless you turn on "show hidden files" in your file manager. Ctrl+H usually toggles this.

Note2: It's been a while since I used GNOME2, and I've never used GNOME3/Unity, so I can't guarantee that this will work for you.

---

### Post by Yumi on 2012-01-28
That did the trick, thank you.

Michael

---

