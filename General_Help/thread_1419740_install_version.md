---
title: "install version"
date: 2010-03-02
forum: General Help
---

### Post by cucuru on 2010-03-02
hello, I have a problem with mplayer, and I read that it could be because is an old version.

The problem is that I have ubuntu 8.04 in the computer, so, it install the last version for this that is 2:1.0~rc2-0ubuntu13.1

Can I install the 9.10 version for mplayer that is 2:1.0~rc2-svn2009, I tried somethings but they didn't work.

Is it possible? 

Thanks! Regards

---

### Post by Barriehie on 2010-03-02
Yes you can, but realize that since you're wanting to install a version that's not sanctioned in the repos for your version of ubuntu weird/bad things may/could happen.  Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and get the one you want.  The file should open with the gdebi installer and it will be added into synaptic.  I'ld make a backup first!

---

### Post by cucuru on 2010-03-03
Hello, may I include it in synaptic? I cant do it, because it is ubuntu server, and it is with comands, I tried with:

```

sudo dpkg -i mplayer.deb

```

But I need a lot of differents packages, should I download all of them and install them manually? isnt there any faster and easier way?

thanks! regards!

---

### Post by Barriehie on 2010-03-03
It should pull in the dependencies required; I'ld definitely make a full backup first, or find an alternative package that will work with your version of OS.

---

