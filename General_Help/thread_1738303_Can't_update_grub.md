---
title: "Can't update grub"
date: 2011-04-24
forum: General Help
---

### Post by gesaugen on 2011-04-24
I'm gona cry out of misery! Linux is pain. so much pain....

ok, here goes (before I cut myself to death with ubuntu DVD):
I have U10.10. I wanted to hide bootloader menu. Some "smart guy" wrote a solution on this forum for hiding a bootloader menu in a way to set timing of menu to 0. And I executed it (oh the obvious stupidity!) So now that makes me go directly to windows (which is my default boot OS in bootloader menu).

SO, now for at least half a day I'm trying to fix that so I can see the bootloader menu and go normaly to ubuntu (because now I cant, menu is disabled via this smart 0 sec parameter in grub for bootload timing)
So I've loaded a live version ov ubuntu and tryed to make grub changes, and I did  BUT for fixing that problem I need also to run a command from terminal "sudo update-grub" which can't be run just like that from live distribution of ubuntu. So I've searched and searched and nothing works: either I cant mount or something wont work or... I really don't know any more. Theres at least a dozen different ways to recover grub non of which doesn't work for me :(

and here I beg you for help: how to update that #@! >:E grub and set it to default values?

disk with ubuntu is "sdc1", so please PLEASE write me a copy-like commands that I can only copy and execute them from my live distibution or I'll burm myself with my PC just to stop this hell suffering called linux! (I'm crying now in fetal possition)

---

### Post by Sun.Dial on 2011-04-24
Hi, how about looking at the Start Up manager in System/Administration at the top left of the screen. You should be able to set the time delay there.
Good luck, Sun

---

### Post by Hedgehog1 on 2011-04-24
This can be corrected (you are not the first who have done this :D ).

Please boot from your LiveCD/LiveUSB, and select 'TRY'

```
sudo mount /dev/sdc1 /mnt
```

```
gksudo gedit /mnt/etc/default/grub
```

[COLOR="Red"]and then change:[/COLOR]

GRUB_TIMEOUT=0

[COLOR="red"]to[/COLOR]

GRUB_TIMEOUT=10

[COLOR="red"] save the file, then exit the text editor.[/COLOR]

```
sudo grub-install --root-directory=/mnt /dev/sdc
```

**The Hedge**

:KS

p.s. "***Linux is pain. so much pain...***" This bout of pain was your own doing, by the way...  You cannot dual boot and NOT have a grub menu...

---

### Post by yetiman64 on 2011-04-24
Have you tried pressing the **shift** key down while booting (you don't mention it)? 

This is the key to bring up the grub menu when hidden. Press it down and hold it down while the grub boot occurs.

Also could you please drop a link to the thread you followed in the first place, as I have given instructions for hiding the menu here in the last few days and would like to check what you have done. I may very well be the "smart guy" you refer to. Is [[COLOR=Blue]--THIS--[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1733199") the thread in question?

In that thread I specifically instructed the OP, NOT to set "GRUB_TIMEOUT=" to 0. 

> You can reduce the grub timeout setting "GRUB_TIMEOUT=" if you wish, but please **do not**  set it to 0 if Windows is set as the default boot. Doing so will stop  you booting into Ubuntu and it is Ubuntu that controls grub (do you see  the potential for trouble ?). 3 is a good low setting to set for  "GRUB_TIMEOUT=" while still allowing you time to hit the **SHIFT key** to bring up the grub screen (the key binding you ask about in your post)The timeout to set to 0 is "GRUB_HIDDEN_TIMEOUT=". If you have set the other timeout to 0 don't worry so much as it can be fixed from a live cd  by a chroot method. (I have instructions for it here if needed though if you followed the other thread I posted in correctly it won't be needed).

Try pressing the **SHIFT** key when you would normally expect to see the grub menu and see if it brings up the menu. We really need to know which settings you changed before attempting anything.

---

### Post by gesaugen on 2011-04-25
Hedgehog, thanks for those commands: they could be executed fine (without errors I usually get) bit those didn't fix my problem: the grub was still hidden (I really don't know why anymore) 

so I've turned to good old recipe for fixing OS-es: reinstall the damn thing!

And everything is ok now, sun is shining, birds are singing and I can live another day with this suffering of OS...

But I'm wiser: I've done .bak copies of all files that need to be changed.

thanks all for help! :popcorn:

---

