---
title: "i have to know"
date: 2006-02-01
forum: General Help
---

### Post by jmxhgyZN8wK7 on 2006-02-01
when you install a program from source (.tar.gz, or .tar.bz2, or whatever), where is the "proper" place to extract it?

(and yes, i know how to use synaptic and apt-get, but i'm trying to install [this]("http://zyzstar.kosoru.com/?tuneroid").)

thanks...

---

### Post by GeneralZod on 2006-02-01
I always extract mine to ~/tmp.  It doesn't really matter in the slightest, really, as long as you have write access to where you want to extract it.  It's probably best to stick to somewhere inside ~ (or one of its subdirectories), but again, it really doesn't matter that much.

---

### Post by Jason_25 on 2006-02-01
One of the best ways to do that is to use checkinstall.  It installs software you built from source into the package manager so you can easily uninstall it.  It's available from the repos.

---

### Post by dage on 2006-02-01
thank to jmxhgyZN8wK7 for the link :), I'm searching this programme too :)

---

### Post by jmxhgyZN8wK7 on 2006-02-02
well, i finally got all the dependencies installed... after i ran

```
./configure
```

it gave me a message that said it had finished and that i should start make, so i started make, and it finished without telling me anything useful... then i installed checkinstall and did

```
sudo checkinstall
```

just like Jason_25 said... apparently, it made the package and installed it, but now i can't figure out how to launch the program!  i've tried

```
tuneroid
```

in the folder where i did all the configure/make/checkinstall stuff, and in /usr/bin, but nothing is happening... :(

---

### Post by soulestream on 2006-02-02
whereis tuneroid
which tuneroid

---

### Post by jmxhgyZN8wK7 on 2006-02-03
hey!  i found it and it works!

i get line after line of this stuff

```

kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-gtar'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-lhz'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-rar-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/x-zip-compressed'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'application/zip'
kbuildsycoca: WARNING: '/usr/share/applications/file-roller.desktop' specifies undefined mimetype/servicetype 'multipart/x-zip'

```

but it works!  thanks for all of your help.

---

