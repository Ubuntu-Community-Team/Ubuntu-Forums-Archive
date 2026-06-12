---
title: "VLC compile error"
date: 2010-08-06
forum: General Help
---

### Post by smothpocket on 2010-08-06
Hello, I'm attempting to compile the latest version of VLC from source. I'm able to run ./configure without any errors, however when I try to make I receive the following error. I tried to google the problem but couldn't find a solution. I don't want to install the program from the repositories because it's outdated and the tray icon doesn't blend in.

-rw-r--r-- smothpocket/smothpocket   181 2010-04-12 18:22 default/subX/playtreeglyphs.png
-rw-r--r-- smothpocket/smothpocket 39468 2010-04-12 18:22 default/subX/about.png
  LUAC   lua/extensions/allocine-fr.luac
luac: `=' expected;
  last token read: `Extension' at line 2 in file `lua/extensions/allocine-fr.lua'
make[2]: *** [lua/extensions/allocine-fr.luac] Error 1
make[2]: Leaving directory `/home/smothpocket/Downloads/vlc-1.1.2/share'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/smothpocket/Downloads/vlc-1.1.2'
make: *** [all] Error 2


Any ideas?

---

### Post by luigi_mb on 2010-08-06
It's probably easier to add the VLC PPA:

```

$ sudo add-apt-repository ppa:c-korn/vlc
$ sudo apt-get update

```

The latest version 1.1.2 is available, and you can install it with Synaptic.

/luigi

---

### Post by andrew.46 on 2010-08-08
Hi smothpocket,

> **smothpocket said:**
> Any ideas?

Have you installed these?:

```
sudo apt-get install lua5.1 liblua5.1-0-dev
```

There is a guide on these forums for building vlc-git that I am sure could be easily modified for the release version:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

Andrew

---

### Post by elliotn on 2010-08-08
Synaptic is beta than compiling

---

### Post by smothpocket on 2010-08-09
> **luigi_mb said:**
> It's probably easier to add the VLC PPA:

```

$ sudo add-apt-repository ppa:c-korn/vlc
$ sudo apt-get update

```

The latest version 1.1.2 is available, and you can install it with Synaptic.

/luigi

I never considered that another repository might have an updated version lol. Thanks for the suggestion :) This way will definitely be more simple.

> **andrew.46 said:**
> Hi smothpocket,



Have you installed these?:

```
sudo apt-get install lua5.1 liblua5.1-0-dev
```

There is a guide on these forums for building vlc-git that I am sure could be easily modified for the release version:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

Andrew

I had installed those packages when it was erroring out during config. I'll definitely check out that link tomorrow morning to see what I may have missed. Even though the suggestion from luigi_mb will make it easier to get up and running, it bothers me that I couldn't get this compiled successfully. 

Thanks guys for your help. I always get great results from this community :)

---

### Post by andrew.46 on 2010-08-14
Hi luigi,

> **luigi_mb said:**
> It's probably easier to add the VLC PPA:

```

$ sudo add-apt-repository ppa:c-korn/vlc
$ sudo apt-get update

```


Christopher Korn's PPA does not seem to carry vlc any more, any idea what happened?

Andrew

---

