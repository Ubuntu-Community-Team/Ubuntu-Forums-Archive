---
title: "Ok Newbie messed up......:("
date: 2010-01-29
forum: General Help
---

### Post by gshot on 2010-01-29
Hi Guys,

Im new to Linux and Ubuntu, but have a good working knowledge of MS Pcs etc. (not that it helps here)

I installed 9.10 Ubuntu and all worked great, the I decided to install the [compizconfig-settings-manager]("apt:compizconfig-settings-manager?section=universe")

All worked fine and I selected a few changes like enabling the cube effect etc....

Then the machine froze, I restarted and now it hangs at the login/network manager applet.

How do I undo the changes I made in the compiz config settings manager?  I have tried to find a way to boot in safe mode, but I soley run Ubuntu on this machine and see no option to boot into safe mode upon start up.

I also tried booting of the live CD, mounted the main hard drive then could not figure out what to do?

Any help would be great, and remember guys, Im a complete NEWBIE, all this talk about subo subu and terminals scare me......;)

---

### Post by llawwehttam on 2010-01-29
This should be simple enough.
 
Press Ctrl+Alt+F1 . You will get a terminal fulscreen. 
DO NOT BE SCARED.
 
Login with your username and password. 
When you type your password it will seem as if you are not typing.
Thisd is normal as * shows how many characters you have so a blank is a security feature.
 
You then need to stop X.
```
sudo service gdm stop
```
 
You will be asked for your password so type it in. Again you will not see typing.
 
you then need to reset compiz.
 
```
gconftool-2 --recursive-unset /apps/compiz
```
 
hope that works for you. 
 
You can then restart your graphical display.
 
```
sudo service gdm start
```
 
use Ctrl+alt+F7 to get back to your gui.
 
Hope that helped.

---

### Post by gshot on 2010-01-29
Thanks for the very quick reply!

When do i press Ctrl+Alt+F1?  During booting or after I boot with the live cd?

---

### Post by Grenage on 2010-01-29
When the system appears to have frozen, it should get you a terminal.

---

### Post by gshot on 2010-01-29
nope it wont even do that

I cannot get past the login screen where is asked for my network key (wireless network)

No buttons work or mouse?

---

### Post by gshot on 2010-01-29
I can however browse my hard drive via the LIVE CD boot.  

Could I change a file there?  If so what exact file and how?

Thanks so much guys..

---

### Post by nothingspecial on 2010-01-29
Hold down shift and escape after you restart and see if you can boot into recovery mode.

---

### Post by Grenage on 2010-01-29
Ok, in that case when you boot the machine up, select the 'recovery mode', that should be in the grub menu.

---

### Post by llawwehttam on 2010-01-29
No no no slow down. Sorry I should have been clearer. you press Ctrl+ALt+F1 after you have booted up without the live cd so where you would normally see the login screen.
 
If you can't do that interrupt booting at grub, I think you hold the shift key down now, and select recovery mode. you can use the commands there instead.
 
EDIT: lol three of us answerd at the same time.

---

### Post by gshot on 2010-01-29
Thanks everyone...getting there.

OK when I hold down SHIFT at boot I get the option to select RECOVERY MODE

THen I get - 

resume
clean
dpkg
grub
netroot
root

Which option should I pick?

(have already tried a few and not sure what Im doing)

---

### Post by Grenage on 2010-01-29
You'll want root :)

---

### Post by llawwehttam on 2010-01-29
You want the root opton. It will give you a command line. You then type:
```
su yourusername
``` and then run 
 
```
gconftool-2 --recursive-unset /apps/compiz
```
 
You will not have to stop or start the gdm though. When you have run the commands instead of
```
sudo service gdm start
```type
```
sudo shutdown -r now
```
 
EDIT:lol grenage beat me to it again.

---

### Post by nothingspecial on 2010-01-29
root, then 

```
su username
```type the command ```
gconftool-2 --recursive-unset /apps/compiz
```

Then type ```
exit
```

----you were quicker than me though

---

### Post by llawwehttam on 2010-01-29
> **nothingspecial said:**
> root, then type the command ```
gconftool-2 --recursive-unset /apps/compiz
```
 
Then type ```
exit
```
 
----you were quicker than me though
 
That would run it as root not as the user. You need to log in as the user with 
 
```
su username
```

---

### Post by nothingspecial on 2010-01-29
> **llawwehttam said:**
> That would run it as root not as the user. You need to log in as the user with 
 
```
su username
```

quite right -- fixed

---

### Post by gshot on 2010-01-29
Thanks guys, all working now.

The support here is great and fast, thank you so much.

I searched all over the place for a way to fix this and I suspect Im not alone, perhaps this could be made a sticky or reposted somewhere else to help other newbies....

Thanks again!

---

### Post by llawwehttam on 2010-01-29
> **nothingspecial said:**
> quite right -- fixed
 
I learnt my lesson with that after deciding to completely reset a user account by wiping everything in it( as I had nothing of value in it and had messed up a few config settings) and used ```
rm -rf ~/*
```
 
sadly as I was logged in with root and thats where I kept all my fixes and scripts back then( as I came from fedora and centOS)........ well I think you can guess what happened.
I now back up everything and use root as little as possible. 
 
> **gshot said:**
> Thanks guys, all working now.
 
The support here is great and fast, thank you so much.
 
I searched all over the place for a way to fix this and I suspect Im not alone, perhaps this could be made a sticky or reposted somewhere else to help other newbies....
 
Thanks again!
 
No problem your welcome. I will put it in my blog later ( linked in my signiture).

---

### Post by nothingspecial on 2010-01-29
ouch

---

### Post by llawwehttam on 2010-01-29
Right I have put it in my blog now. Link is here: [http://llawwehttam.blogspot.com/2010/01/reset-bad-compizconfig-settings-in.html](http://llawwehttam.blogspot.com/2010/01/reset-bad-compizconfig-settings-in.html)

Also if you can please mark the thread as 'Solved' under thread tools above.

---

