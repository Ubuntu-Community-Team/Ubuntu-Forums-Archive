---
title: "Synaptic Package Manager Problem"
date: 2011-01-11
forum: General Help
---

### Post by jasonwupilly on 2011-01-11
Hey Everyone!
I'm am really REALLY new to the Ubuntu/Linux community and I bumped into a problem:

So it started off when I tried to install Sony Vegas with Wine on Ubuntu. When that didn't work, I tried to remove the Sony program in the "Uninstall Wine Software" but for some reason, the program couldn't find the Sony program. So I went to home/jasonwupilly/.wine/drive_c/program files/Sony and deleted the whole directory. However, it was still showing up under applications -> wine -> programs. Basically, then I restarted my computer and some weird black screen showed up. So I restarted my computer again and ran in Linux recovery mode and click "Repair". I could access my account by when I tried to open Synaptic, i got this message:
E: Type 'src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Thanks in advance!

***EDIT***
what is a bean?

---

### Post by lithopsian on 2011-01-11
Show us the first few lines of  /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list.  Sounds like it is corrupt.

---

### Post by zami on 2011-01-11
> **lithopsian said:**
> Show us the first few lines of  /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list.  Sounds like it is corrupt.
Yes, this.

To view it,
hit ALT+F2 ,and in the run box, type in

gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list

and copy&paste the contents of that file here.

-zami

---

### Post by zami on 2011-01-11
Oh and the "beans" are just your post count.  :)

-Laura

---

### Post by jasonwupilly on 2011-01-11
Hey guys there are only two lines:
src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main

---

### Post by jasonwupilly on 2011-01-11
Also: how can you upload screenshots on this forum? cuz I've got screenies of exactly what the popups say.

---

### Post by zami on 2011-01-11
> **jasonwupilly said:**
> Hey guys there are only two lines:
src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main

Curious.  Mine is
```

deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu maverick main #Wine
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu maverick main #Wine

```
note your first line starts "src http://...."
and mine starts "deb http://..."
I would make that change.

To do so, this time do

```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```
make your changes, save, and close the file.
You'll be prompted for a password.

Then restart Synaptic, or hit "Reload" if you still have Synaptic running, and *hopefully* you wont have that same error!

I don't understand how you got this problem to begin with, that's a mystery.  Deleting a .wine directory should not mess with your repositories, as far as I know.  If I had to guess, I'd say your repository error (in Synaptic) and the black screen at boot that you mentioned, were just coincidentally timed errors.  (Just a guess, of course.)

-zami

---

### Post by zami on 2011-01-11
To upload files, hit the little paperclip icon you see when posting - just up above the text entry field.

And just so you know what commands you are using...
"gedit" is just the command to start the text editor.
"sudo" allows you to run commands from the terminal, with administrator privileges,
while "gksu" allows you to run graphical programs, with administrator privileges.
"gksu gedit" just starts the normal text editor, but with admin privileges.

Try not to use "sudo" or "gksu" if you don't have to, as it's easy to muck things up doing so.  

And if you didn't care about any of this, just disregard it!  I just know it drove me batty when I first installed Ubuntu, to follow commands blindly and not know what they meant.  I still do it when I need help of course, but I'm always trying to learn more.

-Laura

---

### Post by jasonwupilly on 2011-01-11
Thanks zami!
Problem Solved :P I am now free to enjoy the wonders of Linux :D

---

### Post by zami on 2011-01-12
:D
Glad it's working again!

-zami

edit: if you re-read this, will you please go to the top of the thread, click "Thread Tools", and "mark this thread as solved" please? It's just a little way to help keep the forums moving.

---

