---
title: "Command Help"
date: 2011-06-17
forum: General Help
---

### Post by simsimma on 2011-06-17
When you run a command by holding down alt+f2 which key do you press to go to the next line? So you can type the next code in the next line.

Thanks,

Sim:popcorn:

---

### Post by WorMzy on 2011-06-17
As far as I'm aware, there isn't one. Use a terminal or a script to run more complex code, the run dialogue (Alt+F2) is just for simple one-liners.

---

### Post by ruffEdgz on 2011-06-17
You can just use the semicolon to end a command so for example:
```

for i in 1 2 3 4; then
echo "Hello $i"
done

```
This can also be written like this:
```
for i in 1 2 3 4; do echo "Hello $i"; done
```
Is that what you mean?

Cheers!

:EDIT: nvm, when you execute the alt+f2 'Run Application', that is used for running applications, not for executing lines of code. Write a script or find an application you want to actually run by typing them in for finding them in the list below the text box.

---

### Post by simsimma on 2011-06-17
for example : wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
sudo wget [http://deb.playonlinux.com/playonlinux_natty.list](http://deb.playonlinux.com/playonlinux_natty.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

for this line of code I need to add echos in it?

---

### Post by ruffEdgz on 2011-06-17
So for that line of code, open up your terminal then copy this line of code into it:
```

wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -; sudo wget http://deb.playonlinux.com/playonlinux_natty.list -O /etc/apt/sources.list.d/playonlinux.list; sudo apt-get update; sudo apt-get install playonlinux

```
That should be equivalent to:
```

wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_natty.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

```
I downloaded this using the PlayOnLinux website but I just did it one at a time but I should have just done it this way I suggested :P

---

### Post by simsimma on 2011-06-17
Ok, thank you so what is a sudo password? once I hit enter it's asking for a sudo password :(

---

### Post by simsimma on 2011-06-17
what is the difference between all these playonlinux versions like natti and maverick anyways I got the code to work btw, thank you very much xD

---

### Post by WorMzy on 2011-06-17
sudo password = your password.

Maverick, Natty, Oneiric, etc. are all different versions of Ubuntu. When you install PlayOnLinux via apt-get, the software centre, or synaptic package manager, it'll automatically install the right version for you.

---

### Post by simsimma on 2011-06-17
Oh lol I just used the code for natty version, and I have the latest version of ubuntu btw :O

---

### Post by ruffEdgz on 2011-06-17
If you are on Ubuntu 11.04, then you want the Natty version for PlayOnLinux (I just pasted what was on their site here but you should be good):
```

For the Natty version

Type the following commands:

wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_natty.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

```

---

