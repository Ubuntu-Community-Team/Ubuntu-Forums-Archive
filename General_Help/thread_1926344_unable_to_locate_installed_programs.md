---
title: "unable to locate installed programs"
date: 2012-02-16
forum: General Help
---

### Post by tommyleinen on 2012-02-16
I have installed several programs through synaptic package manager and cannot locate them! I am running UNR 10.04.

I have checked /usr/share/applications and they are not in here...

Tried reinstalling them, still not appearing.

---

### Post by Simple Name on 2012-02-16
Any examples ?

---

### Post by AlexDudko on 2012-02-16
Try this to locate your installed programs:
> sudo updatedb
> locate installedProgramExecutable

---

### Post by tommyleinen on 2012-02-16
> **Simple Name said:**
> Any examples ?

one was dhcp probe (name might vary slightly) I'm not in front of it just now. I installed docky, and that appeared no problem.

---

### Post by tommyleinen on 2012-02-16
> **AlexDudko said:**
> Try this to locate your installed programs:

Thankyou, I will try tonight.

---

### Post by drmrgd on 2012-02-16
Assuming you want to stay in the terminal to launch programs, the locate command will work, and will show you any instance of the search term on the system.  You may get a lot of hits and won't be sure where the actually executable binary is located.  It'll be good to help you figure that out along with it's location if you don't know the binary name.  If you do know the executable, then try the 'which' command:

```
which dhcp-probe
```

That command will tell you where the actual binary is located.  For example:

```
~$ which google-chrome
/usr/bin/google-chrome

```

That being said, if you installed a program the standard way (which you did if you installed it from Synaptic), the binary should be located in your $PATH environment, and just typing the name should suffice.  In that case, just type 'dhpc-probe'.

---

### Post by tommyleinen on 2012-02-16
> **drmrgd said:**
> Assuming you want to stay in the terminal to launch programs, the locate command will work, and will show you any instance of the search term on the system.  You may get a lot of hits and won't be sure where the actually executable binary is located.  It'll be good to help you figure that out along with it's location if you don't know the binary name.  If you do know the executable, then try the 'which' command:

```
which dhcp-probe
```That command will tell you where the actual binary is located.  For example:

```
~$ which google-chrome
/usr/bin/google-chrome

```That being said, if you installed a program the standard way (which you did if you installed it from Synaptic), the binary should be located in your $PATH environment, and just typing the name should suffice.  In that case, just type 'dhpc-probe'.


Cool thanks for your input - I will let you know how it goes! ;)

---

### Post by tommyleinen on 2012-02-16
Great, thanks guys - they were all in usr/share/doc!

Is there any way to add the .exe to one of the menus such as system tools or games?

Thanks

---

