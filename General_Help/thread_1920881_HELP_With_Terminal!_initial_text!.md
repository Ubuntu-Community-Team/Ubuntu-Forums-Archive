---
title: "HELP With Terminal! initial text!"
date: 2012-02-05
forum: General Help
---

### Post by rtty21 on 2012-02-05
The initial text that is displayed  in the Terminal (the stuff before the cursor) is really annoying. Is there any way that I can disable it?
I would like to turn this:

    root@boss:~# 

into this:

    #

Is there anyway to do this? :confused:

thank you for your time.

---

### Post by Krytarik on 2012-02-05
Please see my earlier reply reg. that here:

[http://ubuntuforums.org/showthread.php?p=11638021#post11638021](http://ubuntuforums.org/showthread.php?p=11638021#post11638021)

Regards.

---

### Post by Khayyam on 2012-02-06
rtty21 ...

There are reasons why PS1 (the variable that asigns 'prompt') is set to something "annoying" (with experience one would say "sane") it gives you some idea of who and where you are. If you have a number of shells (local/remote, root/user) active you can tell at a glance which of these you "intend" to provide input as PS1 changes to reflect $USER, $HOST, and $PWD (at least as its set by default). Setting it to PS1="#" (for both root and $USER) means that these clues are not available, and until you've run foul of an unintended input then you may not see the value in them. At minimum set it to PS1="\$ " (if your using bash) as then you will at least be able to differenciate between a root shell and your regular user.

Also, without $PWD you will need to ask your self "where in the filesystem am I", and save you having to type 'pwd' to find out. Not knowing this, at a glance, can lead you to assume things which may not be the case.

My PS1 sets the colours displayed for $USER and $HOST dependent on whether its a root/user shell, and/or local/remote shell. This means if I'm ssh'd into a server I'm administrating I can see instantly which is which, and as I run many shells concurrently this is a matter of sanity, not an annoyance.

So, PS1 is set to something more than "#" for a reason, it provides some visual feedback as to the nature of that particular shell.

HTH ...

---

### Post by nothingspecial on 2012-02-06
You can change it and change it back like this

```
nothingspecial@magik:~$ PS1='# '
# 
# . .bashrc
nothingspecial@magik:~$ 
```

---

### Post by rtty21 on 2012-02-06
thanks all for all your help! :popcorn:

my troubles are ovor  :D

---

