---
title: "What do I need to compile apps from source?"
date: 2010-12-30
forum: General Help
---

### Post by just_jeepin on 2010-12-30
I'm wanting to setup a emulation PC running Ubuntu (or Lubuntu). I've installed 10.10 and am wanting to compile MAME from the most recent source.

I'm not a Ubuntu newbie but I am new to compiling apps from source. What packages do I need to install to be able to compile?

Thanks for any help!
Danny

---

### Post by hakermania on 2010-12-30
Usually source tarballs contain a README/INSTALL file which say what packages are required to build the package and with what commands :)

---

### Post by tredegar on 2010-12-30
**sudo apt-get install build-essential**
Will fetch and install the minumum you need (gcc make kernel source etc)

D/L mame, untar it, read the README
Have fun.

---

### Post by qamelian on 2010-12-30
you can also save yourself some aggravation by installing most of the necessary dependencies:

```
sudo apt-get build-dep packagename
```

where packagename is the name of the app as it exists in the Ubuntu repos. Unless the version you're compiling requires newer dependencies, this will save you potentially hours of running in circles trying to locate and install other packages.

---

### Post by 0949er on 2010-12-30
> **qamelian said:**
> you can also save yourself some aggravation by installing most of the necessary dependencies:

```
sudo apt-get build-dep packagename
```where packagename is the name of the app as it exists in the Ubuntu repos. Unless the version you're compiling requires newer dependencies, this will save you potentially hours of running in circles trying to locate and install other packages.

*quivers at dependency hell*

---

### Post by kostkon on 2010-12-30
You can get the latest version of SDLMAME from the [*sldmame4ubuntu*]("http://sdlmame.wallyweek.org/") project site.

Hope that helps.

---

### Post by just_jeepin on 2010-12-31
I thought that sdlmame was abandoned since sdl is now in the official mame.

---

### Post by just_jeepin on 2010-12-31
Thanks for all the help! I'll have to try it when I get back to work on Monday (that's where the computer is right now cause my monitor died).

---

