---
title: "Not recognized as root"
date: 2009-07-10
forum: General Help
---

### Post by Solipsil on 2009-07-10
I've installed Linux Ubuntu 9.04. Installation went perfectly fine, I've set up a root password as suggested but ever since that, whenever something requires specifically root password, it won't recognize it and will deny me access. I can't even browse through root folder anymore because apparently I don't have permission to.

Any help appreciated because this is getting irritating - I can't install through Terminal anymore.

Thanks

---

### Post by michy99 on 2009-07-10
Actually, setting up a root password is discouraged in Ubuntu. You can do whatever you need to do using sudo or gksudo instead.

---

### Post by Solipsil on 2009-07-10
Great, thanks for that, it worked.
Is there a way to remove the root passwords so I wouldn't get any more of these messages when
I want to access protected folders? (in case of a rush and I forget about sudo command)

---

### Post by 0pul3nce on 2009-07-10
Have a go at the instructions on this website

[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

---

### Post by Solipsil on 2009-07-10
Thank you, I just tried the tip on that website to disable the root password but instead, I got this - 
```
odessa@Mack:~$ sudo passwd -l root
[sudo] password for odessa: 
Sorry, try again.
[sudo] password for odessa: 
Password changed.
odessa@Mack:~$ 

```

---

### Post by doas777 on 2009-07-10
never tried it, but based on --help, wouldn't you want to use:
```
sudo passwd -d root
```? 

also remember, when using sudo/gksu use your own password, not root's. sorry if i'm stating the obivious.

---

### Post by Solipsil on 2009-07-10
Don't worry, stating the obvious helps, I'm a beginner.
I tried that, but I got this:
```
odessa@Mack:~$ sudo passwd -d root
Password changed.
odessa@Mack:~$ 

```

Password changed to what? It didn't ask me to put anything in. Or does this mean the password has been removed?

---

### Post by doas777 on 2009-07-10
> **Solipsil said:**
> Don't worry, stating the obvious helps, I'm a beginner.
I tried that, but I got this:
```
odessa@Mack:~$ sudo passwd -d root
Password changed.
odessa@Mack:~$ 

```Password changed to what? It didn't ask me to put anything in. Or does this mean the password has been removed?

the passwd has been removed. check out the -d option here: [http://linux.die.net/man/1/passwd](http://linux.die.net/man/1/passwd)

you should be ready to rock 'n roll. have fun!

---

### Post by Solipsil on 2009-07-10
Thanks!

I can now install what I need through the Terminal.
However, I still can't open the root folder.
Again, "no permission to view the contents of 'root'".
Maybe a redundant question, but does it require system restart now
that I've removed the root password?

---

### Post by michy99 on 2009-07-10
Why do you want to look in /root? It can be done, but usually there is no reason for it. To list what is in /root:```
sudo ls /root
```

---

### Post by Solipsil on 2009-07-10
I've managed to install IrfanView through Wine (along with needed .dll) but unlike in Mint, it won't run in Ubuntu. I've read somewhere to check root folder for it to make sure it's been installed. That's why I need to see what's in the root. I've just tried that command but nothing got listed.

---

### Post by michy99 on 2009-07-10
If you installed it through wine, it is probably in ~/.wine/drive_c/Program\ Files/
```
ls ~/.wine/drive_c/Program\ Files/
```
If you are looking for a good image viewer, there are several linux viewers that work very well. I like gthumb.

---

### Post by Solipsil on 2009-07-10
I can see it in Wine (through Applications) but it won't run. I can see the CPU struggling to open it but nothing happens. But that's a whole other issue. The reason why I want IrfanView is simply because of the very easy way to crop images with predefined crop selection size that I can paste onto the image I want to crop.

---

### Post by michy99 on 2009-07-10
Do you have mfc42.dll in ~/.wine/drive_c/windows/system32 ?

---

### Post by Solipsil on 2009-07-10
Yep, it's there.

---

### Post by michy99 on 2009-07-10
Did you get mfc42.dll from an XP install or did you download it from somewhere else? I read somewhere that there is an old version of mfc42.dll that causes a crash.

---

### Post by Solipsil on 2009-07-10
I'm not dual booting at the moment so I got it from here - [www.dll-files.com](www.dll-files.com)

---

### Post by michy99 on 2009-07-10
I have XP on this computer even though I hardly ever use it. Try replacing mfc42.dll with this one and see if it fixes it.

[http://www.hotshare.net/file/160694-2747104cdc.html](http://www.hotshare.net/file/160694-2747104cdc.html)

---

### Post by Solipsil on 2009-07-10
Thanks for the tip. Unfortunately, the new .dll didn't help. I replaced the old one with the one you provided, and again, CPU struggles to launch but nothing happens.

---

### Post by michy99 on 2009-07-10
I'm out of ideas. Maybe you should start a new thread with Irfanview in the subject and someone who uses it can help.

---

### Post by Solipsil on 2009-07-10
No problem, at least you tried, thanks. I might do that soon, yeah.

---

### Post by doas777 on 2009-07-10
> **Solipsil said:**
> Thanks!

I can now install what I need through the Terminal.
However, I still can't open the root folder.
Again, "no permission to view the contents of 'root'".
Maybe a redundant question, but does it require system restart now
that I've removed the root password?

the folder ' /root' is the location of the user profile for the root user. since the root user will not be used except via sudo/gksu, you will not need to use it often. if you want to navigate to it from the terminal, use:
```
sudo cd /root
```
if you want to get there with a gui, hit alt-F2, and enter
```
gksu nautilus
```
(gksu is sudo, for GUI applications).
this will open a file window to the /root directory by default, and you can navigate and make changes with root permissions.

here is some general info on sudo:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

have fun

---

### Post by doas777 on 2009-07-10
> **Solipsil said:**
> Thanks for the tip. Unfortunately, the new .dll didn't help. I replaced the old one with the one you provided, and again, CPU struggles to launch but nothing happens.

usually your best bet, instead of replacing the dll in %systemroot%\system32, placing it in the game directory, and creating an application profile and an override for that dll. 
here is some info on configuring wine:[http://www.winehq.org/docs/wineusr-guide/config-wine-main](http://www.winehq.org/docs/wineusr-guide/config-wine-main)

---

### Post by Solipsil on 2009-07-11
Thanks, I'll get to Wine in a minute.
But I've reached an obstacle with getting to root folder via the terminal. First it reported cd command not being found and then simply "permission denied" without an explanation.
I tried gui and it opens root just fine, however, there is only Desktop icon in there and nothing else. Should it be this way?

---

### Post by carml on 2009-07-11
Yes it should be so,because usually nobody access as root into a Ubuntu system.

---

### Post by Solipsil on 2009-07-11
I see, alright.
I guess the tip I found about IrfanView was wrong.
That's solved then.
Now, hopefully I won't be getting many "permission denied" messages in terminal when I try to install something.

Thanks to everyone who helped. I'll be sure to update in case password input in terminal still causes problems.

---

