---
title: "SSH headless server question"
date: 2010-08-30
forum: General Help
---

### Post by baddnady23 on 2010-08-30
I run a headless SSH server on my local network that is used to stream audio to the internet via darkice.

My question is, when administrating the server from another desktop via SSH, I need to run 

```
sudo darkice -c /etc/darkice.cfg
``` 

to start darkice.  How am I able to close that terminal window that is SSH'd into the server without actually killing darkice?  When ever I close that window, darkice is dead and that is a no go for me...:confused:

---

### Post by Sam on 2010-08-30
Use "screen" for this.

After logging in, run
```
screen
```

Then run your application. To detach press Ctrl-A, then D.

Then you can log out without killing the running process.

Afterwards, to resume, run
```
screen -r
```

---

### Post by baddnady23 on 2010-08-30
I thought screen had something to do with it.  Thank you very much.

---

