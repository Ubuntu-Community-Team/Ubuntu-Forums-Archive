---
title: "where's the applications menu"
date: 2012-10-13
forum: General Help
---

### Post by sudoninja on 2012-10-13
new to ubunutu server 11.10
where's the applications menu?

the GUI i have doesn't appear to be all there.
i don't know what gui it is. there's a vertical bar to the left. top icon - mouse over says "dash home"

most annoying thing is the top line of the screen is hogged by something which just repeats the title of whatever app is running with input focus.

i'd really like to switch from Windows to ubuntu 'cos M$ is going out of business. 1st impressions: ubunto is no faster than windows, it's really bad at telling you what's going on. once i;ve installed an app - ubuntos hides it never to be seen again. the software center lets u see apps but not run them! ~@^@&*$!

---

### Post by Merrattic on 2012-10-13
Have you installed X and a desktop manager/window manager on your server installation? Even with these installed most of the server applications are command line only anyway.

If not, you will only be presented with a command line after installing a server distro.

Quickest way to find what applications you have is to browse "/usr/bin"
```
 ls /usr/bin
``` or to see what packages are installed```
dpkg -l | less
```

---

### Post by wojox on 2012-10-13
> **sudoninja said:**
> new to ubunutu server 11.10
where's the applications menu?

What do you mean, it's all command line.

---

### Post by sudoninja on 2012-10-13
> **Merrattic said:**
> Have you installed X and a desktop manager/window manager on your server installation? Even with these installed most of the server applications are command line only anyway.

If not, you will only be presented with a command line after installing a server distro.

Quickest way to find what applications you have is to browse "/usr/bin"
```
 ls /usr/bin
``` or to see what packages are installed```
dpkg -l | less
```
"ls /user/bin" gives me
ls: cannot access /user/bin: No such file or directory

dpkg shows me what;s installed but not where it is or how to run it. :(

---

### Post by sudoninja on 2012-10-13
> **wojox said:**
> What do you mean, it's all command line.
yes i know server is installed as cli only. but somehow i was able to install a gui - which one i don't know. in windows there's only one gui that's fit for purpose. in ubuntu there seems to be many - not all fit for general purpose i guess.

let's pretend i had a cli only enviro, how would i find these apps once installed?

---

### Post by PaulW2U on 2012-10-13
> **sudoninja said:**
> the GUI i have doesn't appear to be all there.
i don't know what gui it is. there's a vertical bar to the left. top icon - mouse over says "dash home"


I'm not sure that you installed the server version as you have Unity installed and it **is** all there. :)

Mouse clicking on that icon will reveal the dash and the installed GUI applications.

> **sudoninja said:**
> "ls /user/bin" gives me
ls: cannot access /user/bin: No such file or directory

The command given was 'ls /**usr**/bin'.

---

### Post by wojox on 2012-10-13
> **sudoninja said:**
> 
let's pretend i had a cli only enviro, how would i find these apps once installed?

[Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")

---

### Post by sudoninja on 2012-10-13
> **PaulW2U said:**
> I'm not sure that you installed the server version as you have Unity installed and it **is** all there. :)

Mouse clicking on that icon will reveal the dash and the installed GUI applications.



The command given was 'ls /**usr**/bin'.
Thanks PaulW2U!

That's made things a lot clearer for me. (i'm planning to run wine on a window app i have). also the clue that only gui apps are listed in dash home.

but i can't see that applications menu that i've seen in other ubunutu installs.

---

### Post by sudoninja on 2012-10-13
> **wojox said:**
> [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")
thanks for the link wojox

---

### Post by PaulW2U on 2012-10-13
> **sudoninja said:**
> 
but i can't see that applications menu that i've seen in other ubunutu installs.

That's because it's not there. ;)

The idea is that you can search either for the application by **name** or **type**. On the second lens of the dash, 'Search Applications' you can filter on application type if you're not sure what you're looking for or merely want to browse what is installed.

Alternatively you can install Gnome Classic(?), I'm not sure what it's called in your version of Ubuntu and go back to the more traditional Gnome 2 look that you've seen before. Just log out once installed and select it before logging back in.

---

### Post by kurt18947 on 2012-10-13
> **sudoninja said:**
> Thanks PaulW2U!

That's made things a lot clearer for me. (i'm planning to run wine on a window app i have). also the clue that only gui apps are listed in dash home.

but i can't see that applications menu that i've seen in other ubunutu installs.

Possibly because you were looking at installs older than 11.10?  There was a controversal change to Unity as default in 11.10.  Gnome 2 is no longer supported by Gnome hence the change.  There are at least a couple choices to get the 'retro' look.  One which Xfce-desktop,  another is MATE.  I'm not sure either is really appropriate on a server though.  MATE most nearly duplicates Gnome 2 and is installed via a PPA.  Xfce-desktop is availiable in the repos and keeps the gnome apps vs. the 'lighter' apps in Xubuntu.

---

