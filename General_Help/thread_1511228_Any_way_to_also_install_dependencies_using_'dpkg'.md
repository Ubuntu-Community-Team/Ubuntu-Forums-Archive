---
title: "Any way to also install dependencies using 'dpkg'?"
date: 2010-06-16
forum: General Help
---

### Post by inameiname on 2010-06-16
Is there any way to make this:

sudo dpkg -i *.deb

also install dependencies for a deb file in the same way as GDebi does?

Basically I have the above in a script, which I can right click in any folder and have it automatically install all debs in it. So much easier and quicker than using GDebi for each one. However, as of now, it doesn't seem to be installing dependencies, and causes broken packages.

---

### Post by arrange on 2010-06-16
Why don't you use the *gdebi* command? ```
NAME
       gdebi - Simple tool to install deb files

SYNOPSIS
       gdebi [package.deb]...

DESCRIPTION
       gdebi  lets  you  install local deb packages resolving and installing its dependencies. apt does the same, but only for remote (http, ftp) located
       packages.

```

---

### Post by CharlesA on 2010-06-16
You can try to install the deb with dpkg, then run this:

```
apt-get -f
```

Not the best way, but it works, I guess.

---

### Post by bodhi.zazen on 2010-06-16
> **inameiname said:**
> Is there any way to make this:

sudo dpkg -i *.deb

also install dependencies for a deb file in the same way as GDebi does?

Basically I have the above in a script, which I can right click in any folder and have it automatically install all debs in it. So much easier and quicker than using GDebi for each one. However, as of now, it doesn't seem to be installing dependencies, and causes broken packages.

apt-get install -f works

Why are you installing .deb and not using apt-get / aptitude / synaptic / ?

---

### Post by inameiname on 2010-06-16
To arrange:

Boy I'm an idiot...hehe. I forgot about using gdebi through the terminal. :P Thanks for that. It'll probably suffice.

To CharlesA:

"apt-get -f" is a good idea too, thanks. It is something I'm aware of, I just forgot that I could add that at the end of a script with 'sudo dpkg -i *.deb', or something. Of course, using gdebi would work probably be better.

To bodhi.zazen:

I do use the repos just fine. It's just sometimes I come across an updated application that is either not in the official repos, or in any PPA. Also, user created debs or whatnot aren't in any repository as well. Anyway, I have several and when for instance I need to install them all, it takes awhile opening each one, one by one, with gdebi, and installing.

Anyway, thanks again everyone.

---

### Post by inameiname on 2010-06-16
Does anybody know just how to use 'gdebi' to batch install from, say a  directory?

Opening a terminal in a particular directory, and typing:

sudo gdebi *.deb

only installs the first deb file that is in there. 

Is there any way to install all that are on there, without having to  write out each one in the command?

And also, how can I make a script for it? Something like:

#!/bin/bash
tty -s; if [ $? -ne 0 ]; then gnome-terminal -e "$0"; exit; fi
sudo gdebi *.deb

---

### Post by CharlesA on 2010-06-16
As a sidenote: You can also check what dependancies a deb needs by using this:

```
dpkg --info /path/to/deb
```

---

### Post by inameiname on 2010-06-16
Ah, thanks. I didn't know that.

---

