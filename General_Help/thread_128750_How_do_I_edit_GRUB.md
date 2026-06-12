---
title: "How do I edit GRUB?"
date: 2006-02-12
forum: General Help
---

### Post by Pedestrian A on 2006-02-12
Hi,

I'm seriously new to Linux here. I installed Ubuntu (after some seriously devastating trial and error) just to try it out but now I wanna keep Ubuntu to learn more about it and it does seem a lot better than Windows anyway. But because of my lack of knowledge about Linux, I don't think I'm experiencing the full feature of Ubuntu. So let's start with GRUB. I'm sure you guys have heard this time and time again, how do I set it to boot Windows as default? I still need Windows, especially the other people who uses my desktop so I don't want it to boot to Ubuntu if I don't quickly tell GRUB to boot to Windows. I know a site [here]("http://users.bigpond.net.au/hermanzone/p15.htm"), that says I first have to go to Applications, Accessories and then Terminal. From there I type in sudo gedit/boot/grub/menu.lst and I would be asked for my password. But I can't type in my password. Help? Please give me step-by-step instructions? And where can I find a place that's neat and straigh-forward for new users to teach me all I need to know about Ubunut (or Linux)? Thanks.

Pedestrian A.

---

### Post by alfonz on 2006-02-12
why don't you start with this [starter guide first]("http://easylinux.info/wiki/Ubuntu")


as for the password it should be your user password and becarefull everything is case sensitive.

before you do anything.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
back up your grub list.

if you want windows to be the top most os then move these lines or something that resembles this
```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

above the linux kernel options

---

### Post by Mustard on 2006-02-12
With regards to typing in your password, it might be worth mentioning that you don't see the keypresses echoed on the screen when using the terminal.  There will be no asterisks for each keypress basically.  Try just entering the password and hitting enter.

With regards to setting windows as the default, there is a setting in the menu.lst called 'default'.  By default it is set to zero.  Grub counts each menu entry starting with zero.  So the 1st option on the menu is zero, the second option is 1, the third option is 2.  Count down the options and work out which one is windows, and then change the value of 'default' in the menu.lst to reflect this.

---

### Post by Pedestrian A on 2006-02-13
Thanks guys, got pass the password thing but I can't seem to edit menu.lst. Am I doing something wrong?

---

### Post by Pedestrian A on 2006-02-13
I also tried sudo nano /boot/grub/menu.lst but can't open menu.lst in nano. Should I try reinstalling Ubuntu? Maybe it wasn't installed properly or I accidentally messed up something? I don't mind having to reinstall as Ubuntu's installation is fast and I don't have to install drivers (or do I?) and I don't have any files on my Ubuntu partition yet (I just tried Ubuntu about a few day's back). Thanks.

---

### Post by Pedestrian A on 2006-02-14
Please.......

---

### Post by z_diver on 2006-02-14
in Linux there is "almost" never a reason to reinstall anything.  It takes quite a while to understand all the reasons for this but if you are just starting out have some faith.  It looks like you forgot the space between gedit and the absolute path so try 'sudo gedit /boot/grub/menu.lst'.  Tip: just highlight the code(without quotes), open a terminal and middle click to transfer the code to the terminal.

---

### Post by Mustard on 2006-02-14
A new install would be fine.  I must have reinstalled about 3-4 times when I first started using ubuntu, as I became pretty proficient at busting my linux installation while experimenting.  Eventually I learnt to put my /home folder on a seperate partition so that I could reinstall but not format over my /home folder so that all my settings were still in place.

---

### Post by Pedestrian A on 2006-02-14
Thanks guys,

Ya, I guess I missed the space  between gedit and the the absolute path but too late, I reinstalled (kinda fun actually, kinda). Thanks, I've managed to edit GRUB, I used nano. 

Pedestrian A.

---

### Post by chettyk on 2006-02-14
[QUOTE=Pedestrian A]but too late, I reinstalled (kinda fun actually, kinda).[/QUOTE]

One piece of advice that I got at a forum like this when I was just starting to use Linux was: Linux is not Windows, so don't reinstall unless you have messed up your system badly. You learn a hell of lot by figuring out what it is that you are doing wrong or why the system appears to be misbehaving. Mind you, figuring it out can sometimes quite difficult and time-consuming.

---

### Post by alfonz on 2006-02-14
Oh my appologies, I thougth I typed the commad to edit the grub menu 

well here it is even though its a lil late but for future use:

```
sudo gedit /boot/grub/menu.lst
```

again my appologies.

---

### Post by alfonz on 2006-02-14
[QUOTE=Mustard]
With regards to setting windows as the default, there is a setting in the menu.lst called 'default'.  By default it is set to zero.  Grub counts each menu entry starting with zero.  So the 1st option on the menu is zero, the second option is 1, the third option is 2.  Count down the options and work out which one is windows, and then change the value of 'default' in the menu.lst to reflect this.[/QUOTE]

hmm good to know thanks, I never thought about that:(

---

