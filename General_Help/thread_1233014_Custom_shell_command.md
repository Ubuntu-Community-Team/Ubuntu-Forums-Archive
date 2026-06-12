---
title: "Custom shell command"
date: 2009-08-06
forum: General Help
---

### Post by infernus_crusher on 2009-08-06
Is there a way to create your own shell command? Like you can type "firefox" to start up Firefox but "abcd" does nothing. I'd like "abcd" to start up a custom program.

---

### Post by SlugSlug on 2009-08-06
> **infernus_crusher said:**
> Is there a way to create your own shell command? Like you can type "firefox" to start up Firefox but "abcd" does nothing. I'd like "abcd" to start up a custom program.

sudo vi /usr/local/bin/abcd

then input your custom program

sudo chmod +x /usr/local/bin/abcd

---

### Post by Johnny B on 2009-08-06
alias abcd=`whatever command`

---

### Post by Mka on 2009-08-06
or if you don't have administrative rights:
```

if [ -e ~/bin ]; then
:
else
mkdir ~/bin;
export PATH=$PATH:~/bin # rather put this line on ~/.bashrc
fi
touch ~/bin/abcd;
chmod 755 ~/bin/abcd;

```

---

### Post by nothingspecial on 2009-08-06
> **Johnny B said:**
> alias abcd=`whatever command`

You can put your alias`s in .bashrc

```
nano .bashrc
```

Place your alias in it

alias abcde='command'

Ctrl O to save

Ctrl X to exit.

You have to restart bash before it will work. Just type

```
bash
```

---

### Post by infernus_crusher on 2009-08-06
If I type ```
alias x="command"
``` in the command line, which file gets changed? I would like to remove an alias I used for testing.

---

### Post by slakkie on 2009-08-06
> **infernus_crusher said:**
> If I type ```
alias x="command"
``` in the command line, which file gets changed? I would like to remove an alias I used for testing.

alias stuff='ls -altr'
unalias stuff

---

