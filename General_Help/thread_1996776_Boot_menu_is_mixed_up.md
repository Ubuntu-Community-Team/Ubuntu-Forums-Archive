---
title: "Boot menu is mixed up"
date: 2012-06-04
forum: General Help
---

### Post by Chelidze on 2012-06-04
So today Ubuntu 12.04 did some strange update, I am a new user and for me it was strange never seen it before, it asked me to replace some files and so on !! 
 after i restarted PC here is what i saw 
[IMG]http://i.imgur.com/227RZl.jpg[/IMG]

and see

[IMG]http://i.imgur.com/kuN8a.png[/IMG]

Is there a way to remove duplicates from Ubuntu 12.04 boot menu  

and know i am getting errors when i tried to update software in ubuntu

 Is there a software that will fix my ubuntu errors ??

 one more thing Grub Customizer  can not save edited information 
       thank you for your time

---

### Post by Chelidze on 2012-06-05
not the best way to fix this but this worked for me 

```
[http://askubuntu.com/questions/146743/reorder-and-clean-up-grub-menu-in-ubuntu-12-04](http://askubuntu.com/questions/146743/reorder-and-clean-up-grub-menu-in-ubuntu-12-04)
```

```
While a s[CODE]udo update-grub2
``` should remove the duplicate enties, to bring the Windows menu-item at first position additionally do :

```
sudo gedit /boot/grub/grub.cfg
```
Cut the portion of text starting from
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7...
to
}
### END /etc/grub.d/30_os-prober ### 
and pest it just before
menuentry 'Ubuntu, with Linux..

save the file and reboot.

You have to perform steps(1-4) every time grub-pc package-update or a kernel-update happens to keep Windows menu-item at first place.[/CODE]

---

