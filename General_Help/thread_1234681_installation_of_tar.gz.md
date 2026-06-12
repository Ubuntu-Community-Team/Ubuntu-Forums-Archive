---
title: "installation of tar.gz"
date: 2009-08-08
forum: General Help
---

### Post by wenhaosparty on 2009-08-08
When following the instructions here:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
to compile the tar.gz file, I tried to make directory writable by typing:
sudo chown yourusername /usr/local/src

However, it doesn't work at all on my computer. Is there anyone else running into similar problem?

---

### Post by Soul-Sing on 2009-08-08
What do you want to install? (A theme, a program, etc.)
Are there no .deb alternatives?

---

### Post by tommcd on 2009-08-08
> **wenhaosparty said:**
> 
sudo chown yourusername /usr/local/src
However, it doesn't work at all on my computer. Is there anyone else running into similar problem?
Don't bother messing with /usr/local/src. It is not necessary at all.
Just install the **build-essential** and **checkinstall** packages as the tutorial says. Download the .tar.gz program you want to your home directory, then untar it as it says in the tutorial.
Usually there will be a README or an INSTALL file in the directory that is created when you untar the file. Then cd into the directory that is created and read those file(s). They will tell you how to install the program, as well as any needed dependencies, etc.
Typically, you would run:
```

./configure
make
sudo make install

```
to install the program. In order to use checkinstall and install the program as a .deb file so that you can easily uninstall it with apt-get or synaptic, change the last line from:
```
sudo make install
```
to
```
sudo checkinstall
```
Then launch the program from the terminal simply by typing it's name. If there are missing dependencies, there will be an error that says it can't find a dependency. You can likely install any needed dependencies with apt-get.
Your first choice for software should always be the Ubuntu repos though.

---

### Post by wenhaosparty on 2009-08-08
I want to install pymacs, the component required to run emacs as python IDE

---

### Post by wenhaosparty on 2009-08-08
> **tommcd said:**
> Don't bother messing with /usr/local/src. It is not necessary at all.
Just install the **build-essential** and **checkinstall** packages as the tutorial says. Download the .tar.gz program you want to your home directory, then untar it as it says in the tutorial.
Usually there will be a README or an INSTALL file in the directory that is created when you untar the file. Then cd into the directory that is created and read those file(s). They will tell you how to install the program, as well as any needed dependencies, etc.
Typically, you would run:
```

./configure
make
sudo make install

```
to install the program. In order to use checkinstall and install the program as a .deb file so that you can easily uninstall it with apt-get or synaptic, change the last line from:
```
sudo make install
```
to
```
sudo checkinstall
```
Then launch the program from the terminal simply by typing it's name. If there are missing dependencies, there will be an error that says it can't find a dependency. You can likely install any needed dependencies with apt-get.
Your first choice for software should always be the Ubuntu repos though.
Thanks for your kind reply!

---

### Post by Soul-Sing on 2009-08-09
Pymacs is in the repos.of Ubuntu (jaunty) And can be installed via synaptic package manager.

---

### Post by wenhaosparty on 2009-08-09
> **leoquant said:**
> Pymacs is in the repos.of Ubuntu (jaunty) And can be installed via synaptic package manager.

Wow... You are right, I have done the installation!
I thought synaptic package manager is the same as Add/Remove Applications. So I just searched in the "Add/Remove Applications" dialogue window.

---

### Post by Soul-Sing on 2009-08-09
wenhaosparty lots of success with Ubuntu and pymacs!

---

