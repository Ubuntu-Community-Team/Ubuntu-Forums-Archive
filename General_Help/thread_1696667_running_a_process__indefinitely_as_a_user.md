---
title: "running a process  indefinitely as a user"
date: 2011-02-27
forum: General Help
---

### Post by ixxalnxxi on 2011-02-27
i am using Ubuntu 10.04.1 LTS. i only ever contact my ubuntu machine through SSH. everytime i login, i do:

 ~/downloads/.dropbox-dist/dropboxd &

this launches the dropbox process and all is great. except when i log back into the ubuntu machine via ssh after a few hours, the process no longer exists. how can i get the process to run indefinitely?

---

### Post by tredegar on 2011-02-27
You need to learn about **screen**

I think it'll solve your problems.

---

### Post by cjhabs on 2011-02-27
> **ixxalnxxi said:**
> i am using Ubuntu 10.04.1 LTS. i only ever contact my ubuntu machine through SSH. everytime i login, i do:

 ~/downloads/.dropbox-dist/dropboxd &

this launches the dropbox process and all is great. except when i log back into the ubuntu machine via ssh after a few hours, the process no longer exists. how can i get the process to run indefinitely?

Try

```

nohup ~/downloads/.dropbox-dist/dropboxd &

```

---

### Post by seawolf167 on 2011-02-27
> **tredegar said:**
> You need to learn about **screen**

+1 for screen

After I ssh into a box, I pretty much immediately use screen then detach any process that will take any significant amount of time so I don't loose it

```
man screen
```

or just google search for a screen how-to, you'll love it when used with SSH

---

### Post by ixxalnxxi on 2011-02-28
screen did sound good, but it happens to gobble up my 'up' key for some reason. i can't use my command history at all -- it just gives me a OA and OB letters in place of previous commands i used. i will try the nohup suggestion up top, thanks.

---

