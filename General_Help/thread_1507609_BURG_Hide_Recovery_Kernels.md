---
title: "BURG Hide Recovery Kernels"
date: 2010-06-11
forum: General Help
---

### Post by techunit on 2010-06-11
Hi I have installed BURG and I love it. I got the resolution set and I want to hide the ubuntu recovery kernel if I can. It isn't something super important but I would like to do this. Thanks For any help you can provide.

---

### Post by techunit on 2010-06-11
I followed the instructions on omg ubunu... [http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)...

Is there a fast easy way of changing the default ubuntu icon in the BURG Radiance theme to be the new icon as of 10.04. Um Thanks for any help

---

### Post by techunit on 2010-06-11
I found some information on doing this but I cant get it to work. It doesn't seem to be work for burg

---

### Post by techunit on 2010-06-11
Actually it is fixed by going through the file burg found at /etc/default/burg

I found the line ```
#GRUB_DISABLE_LINUX_RECOVERY="true"
``` and remove the # so it is no longer omited. After that burg will no longer display the recovery kernel. I have found that Most of my threads aren't getting attention. I wonder why. Just post so I know that this is wrong... Purhaps I have reached the point where I should be finding more specific threads to work on.

---

### Post by Perturbed Penguin on 2010-06-18
lol I know the feeling of getting no response to one's questions! Thanks for answering yourself here anyways though - your answers helped me figure out how to hide the recovery kernel. Thanks!

---

### Post by Falc7 on 2010-06-20
I've done that, but i still get the recovery options, anyone know why?

Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"

Also, i cant update burg it seems
jamie@jamie-kubuntu:~$ sudo update-burg
/etc/default/burg: 28: Uncomment: not found

---

### Post by techunit on 2010-06-22
Cant really help you there. Um Themeing Burg is complicated if you want to do complicated things with it. I still find that it doesn't have a smoothness that I am satisfied with yet.

---

### Post by alket on 2010-06-22
Or you can simply press F during burg loading

---

### Post by JKyleOKC on 2010-06-22
> **Falc7 said:**
> I've done that, but i still get the recovery options, anyone know why?

Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_LINUX_RECOVERY="true"

Also, i cant update burg it seems
jamie@jamie-kubuntu:~$ sudo update-burg
/etc/default/burg: 28: Uncomment: not foundTry putting the "#" in front of "Uncomment" back and see if that doesn't make update-grub happy. That's what the error message is indicating: the program doesn't know anything about "Uncomment" and that line is simply a comment telling you what to do with the line that follows. Putting the # back turns it back from a command into a comment.

---

### Post by vs8 on 2010-06-27
I want to see only two icons, Ubuntu and Windows. I get two Ubuntu and two Windows icons. How can I remove Windows Vista (loader) entry from burg/grub? I don't want my wife to be confused with the two icons.


Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2


That's my cfg file, she uses Win7 the Vista entry is a recovery entry.

Thank's!

---

### Post by drewsus on 2010-06-27
```
t - Open theme selection menu
f - Toggle between folding mode
n - Jump to the next item with the same class
w - Jump to the next Windows item
u - Jump to the next Ubuntu item
e - Edit the command of current boot item
c - Open a terminal window
2 - Open two terminal windows
h - Display help dialog (only available in sora theme)
i - Display about dialog (only available in sora theme)
q - Return to old grub menu
F5/ctrl-x - Finish edit
F6 - Switch window in dual terminal mode
F7 - List the folded boot items
F8 - Toggle between graphic and text mode
F9 - shutdown
F10 - reboot
ESC - quit from the current popup menu or dialog.
```

---

### Post by techunit on 2010-06-27
Um Not Sure About your Situation Um I don't know how you would hide a partition  in burg...

---

### Post by drewsus on 2010-06-27
> **techunit said:**
> Um Not Sure About your Situation Um I don't know how you would hide a partition  in burg...

as **babaroga** said earlier and following the BURG shortcuts I just posted from the BURG wiki, press F at the BURG menu to "*toggle folding mode*"

This will do exactly what you are asking for. Try changing the theme as well. 

Sora_clear (I think it is called that) is the one I use.

---

### Post by dcstar on 2010-06-28
And make sure you have the latest version of burg updated a few days ago with an important bug fix (updating the menu when a new kernel is installed).

---

### Post by vs8 on 2010-06-28
Thank you guys, I have the latest version installed but it still doesn't work correctly. I was doing some research and it seems like it's a bug. 

I also found out that you could organize the entries as groups but I'm not sure how to do that.

---

### Post by drewsus on 2010-06-28
> **vs8 said:**
> Thank you guys, I have the latest version installed but it still doesn't work correctly. I was doing some research and it seems like it's a bug. 

I also found out that you could organize the entries as groups but I'm not sure how to do that.

Im sorry, I hate to be rude, but its already been said 3 times in this short 2 page thread...
Check out my last two posts.

---

### Post by drivindisco on 2010-08-18
Hey y'all... I've been having the same headaches with burg as well. I installed burg with this guide:
[http://www.liberiangeek.net/2010/07/manage-burg-boot-loader-ubuntu-10-04-lucid-lynx-burg-manager/]("http://www.liberiangeek.net/2010/07/manage-burg-boot-loader-ubuntu-10-04-lucid-lynx-burg-manager/")

I was having major issues with grub loading burg until a ran across how to install burg properly, b/c it seemed to me that there is a bug with the burg manager install tab. I had to run these terminal commands to install burg:
```
sudo apt-get update
sudo apt-get install burg
```

And write burg to the mbr:
```
sudo burg-install /dev/sda
sudo update-burg
```

After I got burg to load, my theme wouldn't load so I had to set the resolution with burg manager to 1280 x 800 under the 'Parameters' tab. 

Finally, I came across removing the Ubuntu recovery kernel and found this post, which didn't work the first time. The problem I had was simple. After uncommenting ```
GRUB_DISABLE_LINUX_RECOVERY="true"
``` and saving ```
/etc/default/burg  
```, you need to run:
```
sudo burg-install /dev/sda
sudo update-burg
```

This will write your changes to the mbr and the recovery kernel will be hidden. I really hope my long winded post helps someone with burg headaches. However, all is well now for me!

---

### Post by rory526 on 2011-01-22
Entering
```
sudo burg-emu
```
in a terminal and pressing 'f' was the most convenient for me.
Thanks everybody.

---

