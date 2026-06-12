---
title: "&quot;Installing&quot; binaries"
date: 2012-03-20
forum: General Help
---

### Post by HKei on 2012-03-20
Basically, I want to make binaries globally available from the shell that I didn't install with apt-get.

I haven't quite figured out yet how I would go about doing that though (in this case, JRuby):

I downloaded the latest (1.6.7) JRuby binary distribution.
I unpacked it into my $HOME directory.

Now I tried several things:

Hard link to jruby:
$(HOME)/jruby-1.6.7/bin/ ln jruby /usr/local/bin/jruby

(doesn't work, because now jruby looks for all the jruby stuff in /usr/local)

Symbolic link:
$(HOME)/jruby-1.6.7/bin/ ln -s jruby /usr/local/bin/jruby

(doesn't work at all. bash tells me jruby isn't there, although it shows up in ls /usr/local/bin)

Now, is there any easy way to do what I want? Or do I have to copy all that stuff into /usr/local?

Please bear with me if I sound confused - I am doing this the first time, usually I rely on the packaging system. But I don't like to be constantly reminded by --version parameters that I'm a few versions behind (sometimes even major ones!) just because I was too lazy to set up stuff manually anymore.

---

### Post by Cheesemill on 2012-03-20
Open your ~/.bashrc file and add the following to it:
```
JRUBY_HOME=$HOME/jruby-1.6.7
PATH=$PATH:$JRUBY_HOME/bin
```Then reload your .bashrc
```
source ~/.bashrc
```Taken from:
[http://dermological.blogspot.co.uk/2007/02/installing-jruby-on-ubuntu.html](http://dermological.blogspot.co.uk/2007/02/installing-jruby-on-ubuntu.html)

---

### Post by HKei on 2012-03-20
Hm, I tried to avoid adding anything to the path variable, though I suppose I won't have much of another choice right now.

---

### Post by Cheesemill on 2012-03-20
You could probably just use your hard link method and then set the JRUBY_HOME environment variable, that way you wouldn't be adding to $PATH.

Edit - Setting the variable in /etc/environment would be system-wide so negating the need to alter any .bashrc files, and would work for all users.

---

### Post by HKei on 2012-03-20
Doesn't seem to work. it complains it can't find org.jruby.Main (same as before).

I'll try copying jruby into /usr/local, although that does seems a little fishy to me...

(if I move a directory into a directory where a directory (the redundancy!) with the same name exists, will the directories be merged?)

---

### Post by Cheesemill on 2012-03-20
Where/how did you set JRUBY_HOME ?
You may need a reboot for it to take effect.

---

### Post by HKei on 2012-03-20
In the bashrc. I will try rebooting for now.

Edit: still doesn't work.

EEdit: I just went with adding JRUBY_HOME to PATH for now. Thanks anyways!

---

