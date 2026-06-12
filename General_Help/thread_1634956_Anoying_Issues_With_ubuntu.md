---
title: "Anoying Issues With ubuntu"
date: 2010-12-01
forum: General Help
---

### Post by Azza156 on 2010-12-01
hey all, usually i don't bother posting messages on forums for help since i just keep googling the problem till i find something but these 2 problems for a otherwise awsum OS have been driving me to and from ubuntu countless times.

First thing is the inability to open .exes & yes I've read everything google has had on offer about it, all i want to do is turn off executable bit. i kinda find it ironic that to relax and play a game i have to go through hours of hair ripping frustration to some how get it to load.

What its doing is i launch it and it says its blocked, i right click on the .exe i want to launch and click properties then permissions and try to tick "allow executing file as program" but then it automatically unticks itself so yeah as annoying as that is I've tried making my account "root" and doesn't do much, i tried the usual terminal commands like sudo sh "/blah/blah/blah.exe" and gives me a weird error.

so yeah any help with that would be awsum, please keep the terminal commands to a minimum.

last thing is when i attempt to access my windows shares that i can access on all but this laptop without the need of a password. (ps3, xbox, vista box, win 7 box etc all can access it without a problem), so yeah is there a way to turn off the password protect sharing on ubuntu's end since it isn't windows 7's fault.

also theres that problem with the ugly boot screen after installing the latest catalysts but i could care less about that anymore.

---

### Post by dino99 on 2010-12-01
welcome noob :)

[http://www.ehow.com/how_5016375_run-exe-files-ubuntu.html](http://www.ehow.com/how_5016375_run-exe-files-ubuntu.html)

---

### Post by 3rdalbum on 2010-12-01
> **Azza156 said:**
> 

First thing is the inability to open .exes & yes I've read everything google has had on offer about it, all i want to do is turn off executable bit. i kinda find it ironic that to relax and play a game i have to go through hours of hair ripping frustration to some how get it to load.

What its doing is i launch it and it says its blocked, i right click on the .exe i want to launch and click properties then permissions and try to tick "allow executing file as program" but then it automatically unticks itself so yeah as annoying as that is I've tried making my account "root" and doesn't do much, i tried the usual terminal commands like sudo sh "/blah/blah/blah.exe" and gives me a weird error.

If the Windows program is stored on a read-only medium such as a CD-ROM, or on a filesystem that doesn't support "execute" permission (such as a Windows filesystem) then the checkbox will untick itself.

You don't actually need to give the file execute permission; just open a terminal, type 'wine' and a space, then drag the file to the terminal. Run the resulting command. Easy when you know how.

> also theres that problem with the ugly boot screen after installing the latest catalysts but i could care less about that anymore.

Unavoidable, I'm afraid. The speccy technology that allows for the nice-looking boot screen is not supported by the ATI or Nvidia proprietary drivers.

---

### Post by Mark Phelps on 2010-12-01
> First thing is the inability to open .exes & yes I've read everything google has had on offer about it, all i want to do is turn off executable bit. i kinda find it ironic that to relax and play a game i have to go through hours of hair ripping frustration to some how get it to load.

Linux is NOT about making it easy to use Windows stuff; it's about providing an ALTERNATIVE to Windows stuff.  IF you can't live without Windows stuff, then do one of the following:
1) Setup a multi-boot machine
2) Install Windows in Virtualbox

These will free you from the limitations of using Wine and other kludges to run Windows stuff.

---

### Post by Azza156 on 2010-12-01
Remember this is a laptop I'm running it on so i don't really care that much about running windows stuff, just that i wouldn't mind the option thats all. reason I'm asking is that I had no problem running windows programs like wow, steam etc on the previous ubuntu 9.10 off a ntfs partition.

but anyway yeah that solved that problem, i just deleted the existing partition and remade it as a ext4 one & can now tick that box.

So any of you's know how to fix that password sharing problem? like i said i was duel booting ubuntu with win 7 on this laptop and I had no issues accessing my main pc's shares from 7.

---

### Post by cottfcfan on 2010-12-01
heres the solution to your ugly boot screen:

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

---

### Post by Azza156 on 2010-12-01
> **cottfcfan said:**
> heres the solution to your ugly boot screen:

[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

yeah that worked, thanks.

---

### Post by cottfcfan on 2010-12-01
Glad I could assist.

---

### Post by Azza156 on 2010-12-01
thats 2 outta 3 problems sorted, anyone got a idea why ubuntu's asking for a password to access my win 7 pc when there isn't any

---

### Post by cgb on 2010-12-01
Not completely sure on your sharing problem but the below link may help.  Seems like their was/is? a problem with connecting to Windows 7 when Live Sign-In Assistant is installed.  Not sure if this is the problem with yours but it might be worth a shot.  Typically I use password protected sharing so I haven't encountered this problem myself.

[http://ubuntuforums.org/showthread.php?p=9635253]("http://ubuntuforums.org/showthread.php?p=9635253")

---

### Post by Azza156 on 2010-12-03
yeah came across that awhile ago but yeah didn't solve my problem. anyone else having similar difficulties?

---

### Post by Azza156 on 2010-12-03
bump

I'm sure theres alot of people out there that are having a similar issue so cmon someone on this forum should at least know why ubuntu is asking for a imaginary password & i doubt its a ntfs related thing since it worked fine back in ubuntu 9.10.

---

### Post by Azza156 on 2010-12-04
bump

---

### Post by zaax on 2010-12-04
I'm having the same problem with HJsplit and this is a Linux program and the exe bit won't stay ticked.

[http://www.hjsplit.org/linux/](http://www.hjsplit.org/linux/)

---

### Post by Azza156 on 2010-12-14
so no one knows how to fix this problem with ubuntu not being able to connect to shares over the network??

---

