---
title: "Ubuntu Ate WindowsXP"
date: 2006-05-16
forum: General Help
---

### Post by DanMan_7 on 2006-05-16
I am new to Ubuntu and was very excited to try it out.  I installed Ubuntu on a seperate partion outside of my current XP partition in hopes that the GRUB loader would sort it all out and I would be able to dual boot my machine.  After install, XP is not on the bootup list,](*,)  how can I manually add it?  Currently, my partition table is a 12gig Ubuntu EXT, and Hda 5 NTFS XP partition.:confused: 
 
     Thanks for any help,  DanMan_7

PS.  I read on the forum something about troubles when XP isn't on Hda 1, perhaps I just need the line of code for Grub to manually tell it where Hda5 is?  I don't know anything about bash codes.:neutral:

---

### Post by Dr. Nick on 2006-05-16
[quote=DanMan_7]I am new to Ubuntu and was very excited to try it out.  I installed Ubuntu on a seperate partion outside of my current XP partition in hopes that the GRUB loader would sort it all out and I would be able to dual boot my machine.  After install, XP is not on the bootup list,](*,)  how can I manually add it?  Currently, my partition table is a 12gig Ubuntu EXT, and Hda 5 NTFS XP partition.:confused: 
 
     Thanks for any help,  DanMan_7

PS.  I read on the forum something about troubles when XP isn't on Hda 1, perhaps I just need the line of code for Grub to manually tell it where Hda5 is?  I don't know anything about bash codes.:neutral:[/quote] 
Edit the file /boot/grub/menu.lst as root and add these lines to the bottom of the file, then save and reboot. I would copy the file first just in case

```
title           Microsoft Windows XP Professional
root            (hd0,4)
savedefault
makeactive
chainloader     +1

``` 
The root option is the one you have to worry about, If XP was on the first partition it would be 0,0 but since its on the 5th try 0,4

The 2nd digit is partion number the first is for the actual drive. Both start at 0 and go up

---

### Post by Slim Odds on 2006-05-16
[QUOTE=Dr. Nick]```
title           Microsoft Windows XP Professional
root            (hd0,4)
savedefault
makeactive
chainloader     +1

```[/QUOTE]

What if he's using XP Home edition? :D

---

### Post by Dr. Nick on 2006-05-16
[quote=Slim Odds]What if he's using XP Home edition? :D[/quote] 
Then anyone who uses his computer will be stunned and say "why did you blow an extra 100 dollars on the pro version when then home edition is barely worth the $100 it cost" Then all you need to do is install a nice xp professional boot screen and no one would ever know :twisted: lol I need to change that line to something else to detur me from booting into it :)

But in all seriousness for anyone reading that, The title line is up to you, The computer doesnt care what you use.

Good suggestions are

Linux wannabe
or
Windoze :-k

---

### Post by DanMan_7 on 2006-05-16
Thx for your help!  I will try it as soon as I get off work.
And yes, I use Professional.    :)

---

### Post by Dr. Nick on 2006-05-16
[quote=DanMan_7]Thx for your help!  I will try it as soon as I get off work.
And yes, I use Professional.    :)[/quote]

Hope it works, just make sure you add it outside the automagic list. You will see what I mean when you read the menu.lst file. If you add it to the wrong spot it will dissappear when you update kernels. If it doesnt work just fiddle with the hd(0,4) part until you find the numbers that work

---

### Post by DanMan_7 on 2006-05-16
When I run the sudo command it opens up the file to edit, but their is no text within the file.  I can view the file from the GUI and can see exactly where the line goes, but I need the terminal to show the text so I can edit it.... Any suggestions?

       Thanks again! DanMan_7

---

### Post by Lord Illidan on 2006-05-16
[quote=DanMan_7]When I run the sudo command it opens up the file to edit, but their is no text within the file.  I can view the file from the GUI and can see exactly where the line goes, but I need the terminal to show the text so I can edit it.... Any suggestions?

       Thanks again! DanMan_7[/quote]

Run this:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by DanMan_7 on 2006-05-17
Thank you all for your help, but i still have the problem.  I have edited Menu.1st file and now the option to boot windows xp is there.  the file looks like this now:
title           Microsoft Windows XP Professional
root            (hd0,5)
savedefault
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

When I choose to boot with XP i get this error message:

Root    (hd0,5)
filesystem type unknown partition type 0x82
save default make active
Error 12 invalid device requsted.

I really would like to get that windows partition operable.  i am sure most of you know what a pain in the ](*,)  it is to get windows working right (if that's possible)  
I will also include a picture of my partitions to show what my hd is setup like, so that posssibly you can help me spot an error.

       Thank you kindly, DanMan_7

---

### Post by Dr. Nick on 2006-05-17
[quote=DanMan_7]Thank you all for your help, but i still have the problem.  I have edited Menu.1st file and now the option to boot windows xp is there.  the file looks like this now:
title           Microsoft Windows XP Professional
root            (hd0,5)
savedefault
makeactive
chainloader     +1

### END DEBIAN AUTOMAGIC KERNELS LIST

When I choose to boot with XP i get this error message:

Root    (hd0,5)
filesystem type unknown partition type 0x82
save default make active
Error 12 invalid device requsted.

[/quote] 
Did you try (hd0,4)? The first partition is 0 not 1 so when its on hda5 it would translate to 4, If I understand that corectly. In your case you would be calling hda6 with 0,5 which is your swap file. Changing the 5 to a 4 will hopefully work

---

### Post by DanMan_7 on 2006-05-17
Unfortunatly I tried that too.  As i am very ignorant, I wonder if the trouble may be related to the ntfs being mounted.  Ubuntu will not mount my ntfs partition unless I manually do it each time.  I have tried editing the FStab file, but it still will not automatically mount it.  perhaps Grub won't see it, cause its not visibily mounted?
                                         Thanks, DanMan_7

---

### Post by Dr. Nick on 2006-05-17
[quote=DanMan_7]Unfortunatly I tried that too.  As i am very ignorant, I wonder if the trouble may be related to the ntfs being mounted.  Ubuntu will not mount my ntfs partition unless I manually do it each time.  I have tried editing the FStab file, but it still will not automatically mount it.  perhaps Grub won't see it, cause its not visibily mounted?
                                         Thanks, DanMan_7[/quote] 
The ntfs doesnt need to be mounted, infact it never gets mounted until you are loading ubuntu. I will contine looking up ideas, but in the meantime could you post your entire /boot/grub/menu.lst file please?


It appears by your attachement that you have a seperate boot partition, that shouldnt make a difference as I used to have mine set up that way but who knows :rolleyes:

EDIT
Just for kicks and the off chance it might work add 
rootnoverify (hd0,4)
instead of just root (hd0,4) I have seen other people say just root get them a error

---

### Post by turbojugend_gr on 2006-05-17
Hit there, I believe that's not the case but give it a try.
Edit the /boot/grub/menu.lst file and go to the Windows option... Change it to look like this```
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
The "map" thing is maybe your solution... Windows tend to identify vica versa the drives. So give it a try and remember to change the (hd0) (hd1) cases to your needs. Also I don't see the need for the makeactive option but I won't argue on that anyway. I hope that works, notify me with your progress.

---

### Post by Dr. Nick on 2006-05-17
[quote=turbojugend_gr]Hit there, I believe that's not the case but give it a try.
Edit the /boot/grub/menu.lst file and go to the Windows option... Change it to look like this```
title        Microsoft Windows XP Home Edition
root        (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
``` The "map" thing is maybe your solution... Windows tend to identify vica versa the drives. So give it a try and remember to change the (hd0) (hd1) cases to your needs. Also I don't see the need for the makeactive option but I won't argue on that anyway. I hope that works, notify me with your progress.[/quote]

The makeactive may not be necessary, I am not sure what all it does, I just know on my installation it added it for me so I assumed it was needed, though it may not be.

---

### Post by turbojugend_gr on 2006-05-17
[QUOTE=turbojugend_gr]Hit there, I believe that's not the case but give it a try.
Edit the /boot/grub/menu.lst file and go to the Windows option... Change it to look like this```
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
The "map" thing is maybe your solution... Windows tend to identify vica versa the drives. So give it a try and remember to change the (hd0) (hd1) cases to your needs. Also I don't see the need for the makeactive option but I won't argue on that anyway. I hope that works, notify me with your progress.[/QUOTE]

Just in case your are too lazy to figure it out your case should be:```
title		Microsoft Windows XP Home Edition
root		(hd4,0)
savedefault
map		(hd0) (hd4)
map		(hd4) (hd0)
chainloader	+1
```

Again I am not sure, as I am not on your machine at the moment make a backup so you won't get confused on getting back to your previous configuration.

---

### Post by turbojugend_gr on 2006-05-17
[QUOTE=Dr. Nick]The makeactive may not be necessary, I am not sure what all it does, I just know on my installation it added it for me so I assumed it was needed, though it may not be.[/QUOTE]

The makeactive command is used only for Primary Partitions so it may causes a problem in his case. My memory tells me that this command is limited to primary PC partitions on a hard disk. But it may be useful in other cases too.

---

### Post by DanMan_7 on 2006-05-18
Thanks a lot, I really appreciate your help.  I'll let you know how it goes.

           ,DanMan_7

---

