---
title: "Issues with grub / windows 7"
date: 2009-06-28
forum: General Help
---

### Post by nlakes on 2009-06-28
Hi everyone, 
I've upgraded my machine from Vista to Win 7 and I lost my grub. I scanned the forums and found some solutions that did not work, I'm a noob so not really good at this stuff. 

I did 
sudo -l
root (hd0,5) <- my linux install is there
setup (hd0,5) 
quit.

That did not restore grub, so installed a program called EasyBCD in Win7 which modifies the windows version of grub - however now when I boot up I can choose Ubuntu or Win7, but if I choose Ubuntu it boots into grub where I have to choose again & it shows windows 7 as "windows vista". 

So my questions are:
1) how do I disable grub and let EasyBCD handle the boot-loading, or
2) how to I reinstall grub so it identifies my Win 7 & ubuntu install and *it* takes over my boot loading?

Many thanks.

---

### Post by egalvan on 2009-06-28
1. Boot your computer with a Live CD
2. Open a terminal window.
3. Type

```
 sudo grub
```
you should get text of which last line is "grub>"

4. Type "
```
find /boot/grub/stage1
```
You should get a response like "(hd0,5)".
   **Use whatever [COLOR="Red"]your[/COLOR] computer spits out for step #5.**

5. Type

```
root (hd0,5)
```
(what you got in step #4, hard disk + boot partition)

6. Type
```
setup (hd0)
```
to install GRUB to MBR,

7. Quit grub by typing

```
quit
```

8. Reboot and remove the Live CD.

---

### Post by nlakes on 2009-06-28
Thanks for the reply, I tried that the first time, I did it again and got this output:

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
[B] Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)[/B]
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

I tried restarting and I still do not see grub, still the one I installed in Win7 only.

---

### Post by nlakes on 2009-06-29
bump.
Anyone? I can't get grub to take over.

---

### Post by nlakes on 2009-07-01
The issue is still not resolved, anyone?

---

### Post by nlakes on 2009-07-14
The posted solutions did not work. Anybody else? Please?

---

