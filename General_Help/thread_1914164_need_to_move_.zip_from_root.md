---
title: "need to move .zip from root"
date: 2012-01-23
forum: General Help
---

### Post by evolutionmoto on 2012-01-23
Hello all! I am one month into my new Linux/Ubuntu adventure and loving every second of it :). Any how I am encountering a problem with my Android compile. Its saving my .zip to the Root of Ubuntu and after using  $ sudo nautilus too see it, I cant move it to any where I can use it. Is there a way to either change the .zip file permissions or move it too non root /home ?

thanks in advance for any help you guys are able to provide :D

running Ubuntu 10.04lts 64bit

---

### Post by pbrane on 2012-01-23
You should be able to change permissions and move it using the terminal. Something like this.
```

sudo chown <your-user-name>:<your-user-name> /path/to/filename
sudo mv /path/to/filename /directory/to/move/file-to

```

type *man chown* and/or *man mv* in a terminal to see the manual page for those commands.

I would look into why your android build has root access. You shouldn't need root privileges to compile code. Maybe to install it, but not to build it.

---

### Post by evolutionmoto on 2012-01-23
Thanks for the help on the move. It worked perfectly. As for the build having root I'm pretty sure it was the install. In the beginning of the install and set up tutorial it called for sudo -i to save time but now its looking like a headache.  The source ended up being in the root and now it compiles there :(. Is it possible to move the entire source in the same fashion you had me use to move the .zip?

Thank you so much for taking the time to help me.

---

