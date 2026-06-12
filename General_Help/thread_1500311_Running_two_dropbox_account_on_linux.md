---
title: "Running two dropbox account on linux"
date: 2010-06-03
forum: General Help
---

### Post by annegirl on 2010-06-03
I had two dropbox accounts (one personal, one business) running on my ibook G4 that decided to die last week. I purchased an eee PC and put Ubuntu on it at the recommendation of 2 of my brothers.

Now I'm trying to get two dropboxes to run on this OS and I keep getting this in terminal

[FONT=monospace] HOME=$HOME/.dropbox-alt /usr/bin/dropbox start -i
Starting Dropbox...Traceback (most recent call last):
  File "/usr/bin/dropbox", line 224, in handle_ok
    self.dont_show_again_align.hide()

And a pop up window that says, "in order to run dropbox you must install the proprietary daemon."

What am I doing wrong?? I'm a total baby when it comes to terminal/geek stuffs. I'm trying to learn but I am still just crawling along.

Thanks!
[/FONT]

---

### Post by howefield on 2010-06-03
Have you set up the first dropbox account yet ?

After installing the dropbox .deb package, it is usual to start Dropbox from the Applications > Internet menu and then for the dialogue window to prompt you to download rest of the application.

---

### Post by annegirl on 2010-06-03
Yes, I've set up the first dropbox account and it is all connected and working well. It's the terminal part setting up the second one that is giving me fits. I have this feeling that something is not quite where it should be or it can't find the right piece or something...I just don't know enough to see it.

> **howefield said:**
> Have you set up the first dropbox account yet ?

After installing the dropbox .deb package, it is usual to start Dropbox from the Applications > Internet menu and then for the dialogue window to prompt you to download rest of the application.

---

### Post by benylin on 2010-07-22
Got this working on lucid this week.
(my wife and I like to use a single login, and each had existing dropbox accounts to work PCs)

I started from a position of having a working first account (mine).

First step is to move the existing account, and get it working ... 

So you can probably replace "me" and "other" in the commands below with "personal" and "business" or whatever you want to call them.

1] Stop the existing dropbox daemon running.

2] rename existing account .dropbox folder
```
mv ~/.dropbox ~/.dropbox-me
```

3] create a new bash script 'start-dropbox-me.sh', containing the following:
```
#!/bin/bash
HOME=/home/me/.dropbox-me /home/me/.dropbox-dist/dropbox start -i
```

Note that I found that pointing to /home/me/.dropbox-dist/dropbox made the difference - using the one in /usr/bin caused the same error you are seeing. I'm not really sure why, I was just experimenting and it worked.

4] and make it runnable:
```
chmod 775 start-dropbox-me.sh
```

5] use "system->preferences->startup applications" to add this script as a startup application. (actually, I edited the existing dropbox startup application to point at this script).

I now had a running dropbox after restart (or just running the bash script).

Second step is to configure the new account (for "other"):

6] create a new bash script 'start-dropbox-other.sh', containing the following:
```
#!/bin/bash
HOME=/home/me/.dropbox-other /home/me/.dropbox-dist/dropbox start -i
```

7] and make it runnable:
```
chmod 775 start-dropbox-other.sh
```

8] run this script, and follow usual registration (or existing account) process, to get it configured. Using a different location that the first account.

[at this point I had two working dropbox accounts]

9] use "system->preferences->startup applications" to add this other script as a startup application.

Restarted the PC and it all came back with the two dropbox Icons on the panel, etc.

Hope this works for you.

---

