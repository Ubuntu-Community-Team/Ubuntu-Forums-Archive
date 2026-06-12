---
title: "Newbie CLI question"
date: 2010-01-23
forum: General Help
---

### Post by zookrider on 2010-01-23
I'm trying to get CheckGmail to play a wav file whenever I get a new email but am having some difficulty.

In CheckGmail's preferences there is an option to execute a command upon the receipt of a new email. I want it to

> play data.wav

The problem is that data.wav is located in a folder entitled "WAV_Files". Entering the above command from the home directory obviously returns:

> michael@michael-laptop:~$ play data.wav
play FAIL formats: can't open input file `data.wav': No such file or directory

When I enter:

> cd WAV_Files
play data.wav

the whole thing works beautifully. The problem, I can only enter one command into CheckGmail. I tried to pipe the commands together thusly:

> cd WAV_File|play data.wav

to no avail. I got the exact same "no such file or directory" line as above. Please help.

---

### Post by s.fox on 2010-01-23
Hello,

Try using && instead of |

-Silver Fox

---

### Post by nothingspecial on 2010-01-23
You have to specify the path, which would be

```
play /home/username/WAV_Files/data.wav
```

---

### Post by zookrider on 2010-01-23
> **nothingspecial said:**
> You have to specify the path, which would be

```
play /home/username/WAV_Files/data.wav
```

Thanks that did it. I knew it was something simple that I was missing. Lots to learn still.

---

