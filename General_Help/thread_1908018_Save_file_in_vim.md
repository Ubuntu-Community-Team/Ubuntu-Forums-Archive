---
title: "Save file in vim?"
date: 2012-01-12
forum: General Help
---

### Post by onlinetechstores on 2012-01-12
> **dracayr said:**
> did you do that from a tty?
you can also edit files using nano or vim:

sudo vim /etc/X11/xorg.conf

dracayr

This may be a stupid question....but I am new....when I bring up the file to edit, how do i save it? like I am having to add a line to my httpd.conf file, after I add the link how do I save?

thanks!

---

### Post by oldos2er on 2012-01-12
Post moved to its own thread.

In vim, save a file with :w ([http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html))
The nano editor is somewhat easier to use, gedit is easier still.

---

### Post by Stovey on 2012-01-12
Hi Oldos2er!  Also "ZZ" saves and exits.

---

### Post by collisionystm on 2012-01-12
> **onlinetechstores said:**
> This may be a stupid question....but I am new....when I bring up the file to edit, how do i save it? like I am having to add a line to my httpd.conf file, after I add the link how do I save?

thanks!


in VIM

the letter   [SIZE=4]i[/SIZE]

lets you insert text

ESC key to leave the "insert mode"

So when you are done inserting text, hit ESC

write your changes to the file with[SIZE=4] :w! [/SIZE]   << lower case

performing the :w! will only write changes and not exit the file

[SIZE=3]typing two capital Z's will save and exit[/SIZE]

hold the [SIZE=4]shift key, Z Z[/SIZE]

to just quit and not save changes, press    [SIZE=4]:q![/SIZE]

same thing when reading manuals. to exit a manual just type [SIZE=4]:q[/SIZE]

---

### Post by collisionystm on 2012-01-12
> **oldos2er said:**
> Post moved to its own thread.

In vim, save a file with :w ([http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html))
The nano editor is somewhat easier to use, gedit is easier still.


nano is easier, but unfortunately it can give you a problem with leaving extra spaces when editing files.

For instance,

Lets say you want to add an SSH key to authorized_keys file.

You past the key from id_rsa.pub into a nano file. The nano file will screw it up because it takes everything after SSH and treats it as a new paragraph causing it not to work. Pasting into VIM however keeps everything the way it was intended.... 

just an example.....

---

### Post by bodhi.zazen on 2012-01-12
vim ftw, there is a bit of a learning curve to it though.

If you are managing a server, another option is to "Connect to a server" in nautilus.

You need to first install ssh server, be sure to secure it (use keys, disable password authentication).

[img]http://3.bp.blogspot.com/-0YA3ME8TjlQ/TrvZaMnhmkI/AAAAAAAABs0/yi3vydSS4tM/s1600/nautilus-connect-ssh-1.png[/img]

You can then open files with gedit, drag and drop files server <--> local , etc.

vim also has a nifty option of editing over ssh (note the double //, which is the only exception I am aware of to the obscure rule I posted yesterday).

```
vim scp://user@server//var/www/index.html
```

---

