---
title: "How do I configure PATH for texlive?"
date: 2011-08-05
forum: General Help
---

### Post by arroy_0209 on 2011-08-05
After installing texlive I got this message: "add /usr/local/texlive/2011/bin/i386-linux to your PATH for current and future sessions." By default the result of echo $PATH in ubuntu 10.04 LTS is:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin/bin:/usr/games

In my .bashrc file, exactly where should I insert the suggested PATH ? Does it matter where it is put (please keep security hole issues also while answering this question). For example will it be OK if I add this line at the end of my .bashrc file:
/usr/local/texlive/2011/bin/i386-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin/bin:/usr/games

If it is not, please suggest the correct position where texlive PATH should go.

(I realized simply adding the above line, /usr/local/texlive/2011/bin/i386-linux at the end of my .bashrc is not the correct way to do because this gives rise to executing common commands live vi or xemacs etc(PATH clash, command not found in suggested PATH)).

Another doubt is related to the kernel, the command sudo uname -a gives me: linux myname-desktop 2.6.32-33-generic #71 Ubuntu SMP wed Jul 20 17:31:40 UTC 2011 i686 GNU/Linux
Do you think the downloaded texlive will work since this relevant to i386-linux?

Thsnks for suggestions.

---

### Post by dcstar on 2011-08-05
> **arroy_0209 said:**
> After installing texlive I got this message: "add /usr/local/texlive/2011/bin/i386-linux to your PATH for current and future sessions." By default the result of echo $PATH in ubuntu 10.04 LTS is:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin/bin:/usr/games

In my .bashrc file, exactly where should I insert the suggested PATH ? .........

```
gksudo gedit /etc/environment
```

---

### Post by nothingspecial on 2011-08-05
Where ever you like, at the end would be good
```

export PATH=$PATH:/usr/local/texlive/2011/bin/i386-linux
```

Then 

```
. ~/.bashrc
```

---

