---
title: "Sending different commands to another terminal"
date: 2011-11-25
forum: General Help
---

### Post by mswamy78 on 2011-11-25
Hello,

I am playing a movie using /dev/pts/0 terminal, say "mplayer test.mpg".

Now I have opened another terminal /dev/pts/1. From this I want to send the command to pause the mplayer which is the command "p". How shall I send this command to /dev/pts/0.

I tried,
write lucid /dev/pts/0 > p
export PROMPT_COMMAND="p > /dev/pts/0"

Both did not help me..
Please suggest.

Regards,
Swamy

---

### Post by Sazhen86 on 2011-11-25
I don't think you are going to be able to do what you want due to the way that pseudo terminals work.  You need input to mplayer not output to the terminal emulator.

You might be able to get mplayer to do what you want if you use the -input option and specifying a FIFO (named pipe) as the input.  That way you should be able to echo commands to the pipe and have mplayer act on them.  Use -input cmdlist to get a list of available commands.

Hope that helps.

---

### Post by Habitual on 2011-11-25
```
apt-get install -y screen
```

---

### Post by HermanAB on 2011-11-25
You can probably also do it with Expect.

---

### Post by llamabr on 2011-11-25
> **Habitual said:**
> ```
apt-get install -y screen
```

how could screen be used to solve this issue?

---

