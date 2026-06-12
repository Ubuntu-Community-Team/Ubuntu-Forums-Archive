---
title: "default reset"
date: 2011-10-31
forum: General Help
---

### Post by jmacx81 on 2011-10-31
I need a way to reset the default on my ubuntu. I can not view my partition through windows or I would format the partition. Does anyone know how to restore the defaults. Here is what the deal is now. I get to the GRUB screen and select ubuntu, then it goes to the ubuntu start up screen, now instead of going to the ubuntu login screen it goes to a script log in screen and after you enter your username and password it goes to another ubuntu prompt and awaits a command.

---

### Post by Wayne_V on 2011-10-31
I think we need more info - are you talking about just a non-graphics login?  Or are you booting into recovery mode for some reason?

---

### Post by jmacx81 on 2011-10-31
it is a non-graphics login.

---

### Post by Devi1903 on 2011-10-31
Have you tried entering

```
start X
```

to start the x server?

---

### Post by Wayne_V on 2011-10-31
or any other command?

df
who -a
dmesg
ls
pwd

---

### Post by Devi1903 on 2011-10-31
perhaps try posting the messages log so that we can see what happened during boot to stop x running

---

### Post by philinux on 2011-10-31
> **Devi1903 said:**
> Have you tried entering

```
start X
```

to start the x server?

That should be
```
startx
```

---

### Post by jmacx81 on 2011-10-31
I have tried startx. It does nothing but take me to the ubuntu load screen for over an hour and nothing happens. I can not post my script because I am deployed to Afghanistan and there is no way to copy and paste from my computer to a government computer to post. I was trying to get rid of some KDE programs when this problem happened so if there was a way that I could restore the defaults without needing an internet connection at first that would be helpful.

---

### Post by jmacx81 on 2011-10-31
but I can type what happens.

Grub screen

ubuntu start up screen

non graphic (terminal type) login

Ubuntu 11.04 ubuntu tty2
ubuntu login:
Password
Last longin: blah blah blah
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-10-generic x86_64

* Documentation:   [https://help.ubuntu.com/](https://help.ubuntu.com/)

mac@ubuntu:~$


Does that help at all?

---

### Post by jmacx81 on 2011-10-31
> **Wayne_V said:**
> or any other command?

df
who -a
dmesg
ls
pwd

All of these commands work

---

### Post by Wayne_V on 2011-11-01
without an internet connection?  that could be tough.

cd to /var/cache/apt/archives and see what .deb files are there.

then do "dpkg --list | grep "^r" | more".  this will tell you what packages were recently removed.

and then *maybe* you can do "dpkg -i <pkg>.deb" to get them back.

or, maybe better, try:

sudo apt-get -f --no-download kubuntu-desktop

note, I'm assuming you were using kubuntu since you said you were removing KDE packages.   If the packages are still in the cache you should be able to reinstall ... maybe ....

good luck!

---

### Post by jmacx81 on 2011-11-01
> **Wayne_V said:**
> without an internet connection?  that could be tough.

cd to /var/cache/apt/archives and see what .deb files are there.

then do "dpkg --list | grep "^r" | more".  this will tell you what packages were recently removed.

and then *maybe* you can do "dpkg -i <pkg>.deb" to get them back.

or, maybe better, try:

sudo apt-get -f --no-download kubuntu-desktop

note, I'm assuming you were using kubuntu since you said you were removing KDE packages.   If the packages are still in the cache you should be able to reinstall ... maybe ....

good luck!

I am really happy that you posted this information, I'm sure it is very helpful but I am a little embarrassed to say that you lost me. I used to be decent at script but not I am very bad at it. Should I try the sudo apt-get first? I can handle that one but the others may take a little more explaining.

---

### Post by Wayne_V on 2011-11-02
no problem - try this:

$ cd /var/cache/apt/archives
$ ls *desktop*

if you see something like ubuntu-desktop....deb or kubuntu-desktop...deb, then try:

$ sudo apt-get -f --no-download install ubuntu-desktop 

(or kubuntu-desktop, whichever you saw).  

and *hopefully* you will be able to reinstall from the .deb archives

out of curiosity - what is the reason you don't have internet?  is it because of the desktop not loading or is it because it's a personal computer and you can't plug it in to the network?   (if it is because of the missing desktop we might be able to work around that ...)

---

### Post by jmacx81 on 2011-11-02
well last night I tried the sudo apt-get command, I didn't get anything out of it so I was going to follow your insturctions today but when i went to boot it up my computer stays stuck on the ubuntu startup screen. The reason I don't have internet is I'm deployed to Afghanistan and we have to pay for the internet here so once you get a wireless (wireless is all we have) you have to go to the logon webpage and once you logon you then get internet so if I can't open a web browswe then I get no internet.

---

### Post by jmacx81 on 2011-11-02
Ok, I was able to get back into the prompt and all I got was

$ ls: cannot access *desktop*: No such file or directory

---

### Post by jmacx81 on 2011-11-02
Ok not sure if this will help. I was in the GNU GRUB screen and I hit e for edit just to see what it said and I'll type it out

setparams 'Ubuntu, Linux 2.6.38-10-generic'

insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 3CBE3ED2BE3E8484
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.38-10-generic root=UUID=3CBE3ED2BE3E8484 loop-/ubuntu/disks/root.disk ro   quiet splash
initrd /boot/initrd.img-2.6.38-10-generic

---

### Post by Wayne_V on 2011-11-02
when you did the remove did you do 'apt-get remove' or 'apt-get purge'?    I think 'purge' clears out the cache as well.   So if you have nothing in the /var/cache/apt/archives directory and you can't get internet address your only hope is the ubuntu DVD ....

---

### Post by jmacx81 on 2011-11-02
well I removed everything through synaptic (spelling) I didn't do anything through the terminal view. I have internet on my windows side so I've started a download of ubuntu 11.10 on uTorrent. Once I get that done I can just burn to a disk then boot from that right? When it loads will it give me to option to formate the partition that ubuntu was on?

---

