---
title: "Terminal autocomplete (tab) issue with apt-get"
date: 2011-02-02
forum: General Help
---

### Post by slooksterpsv on 2011-02-02
I'm having an issue when I run apt-get and try to use autocomplete. It seems to only happen when I try to remove or install certain items - like gwibber, gnome stuff, etc.

So let me show you what happens:
```

user@mycomp ~ $ sudo apt-get remove gwigrep-status: /var/lib/dpkg/status:13456: expected a colon
.

```
So I typed in gwi pressed tab and it came up with the /var/lib/dpkg/status:13456: expected a colon (newline) .

So I dunno how to fix it. Any ideas?

---

### Post by vividexstance on 2011-02-08
Since yesterday, autocompletion for apt-get does not work.  It works for commands/directories, but not when I try to use it for apt-get (anything).  I've checked around and made sure I had all the necessary files, and that it wasn't commented out.  I've also tried uninstalling and reinstalling bash/bash-completion and the problem still persists.  Any help??

---

### Post by slooksterpsv on 2011-02-08
> **vividexstance said:**
> Since yesterday, autocompletion for apt-get does not work.  It works for commands/directories, but not when I try to use it for apt-get (anything).  I've checked around and made sure I had all the necessary files, and that it wasn't commented out.  I've also tried uninstalling and reinstalling bash/bash-completion and the problem still persists.  Any help??

Open terminal, type in:
pico ~/.bashrc

Now type in the following at the end:

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

Then press CTRL+X then Enter. Now close terminal, open it again, and it should work.

---

