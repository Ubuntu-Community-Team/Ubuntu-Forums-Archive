---
title: "Problem with GRUB in terminal"
date: 2011-04-22
forum: General Help
---

### Post by Zombiphill on 2011-04-22
I just had a question about my GRUB. I'm using Ubuntu 10.10 Netbook remix and I'm running it on a Samsung N145. No dual boot with Windows, just fully installed Ubuntu. I was trying to get the brightness function keys to work without freezing the keyboard, and one of the steps I had to use was going into the etc/default/grub folder, trying in a line and saving the changes. Well, somehow I messed up my GRUB because now when I type into the terminal:

sudo vi etc/default/grub 

I get this message:













E325: ATTENTION
Found a swap file by the name "/etc/default/.grub.swp"
          owned by: root   dated: Tue Apr 12 06:52:33 2011
         file name: /etc/default/grub
          modified: YES
         user name: root   host name: phill-N250P
        process ID: 2012
While opening file "/etc/default/grub"

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/default/grub"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/default/.grub.swp"
    to avoid this message.

"/etc/default/grub" [New File]
Press ENTER or type command to continue


Now when I follow that I type

:recover

I'll get the grub command terminal, but I can't edit it, or if I do change something, my arrow keys start displaying A B C or D depending on which direction I press, and I can't do antyhing afterwards.

Or if I just hit ENTER I get this:

~                                                                                                                     
~                                                                                                                     
~                                                                                                                     
~                                                                                                                     

But its all the way down the window, there's about 20 - 30 of them.


Now my question is this: did I mess up my grub? And if so, how can I go about fixing it? I'm still relatively new to Linux, but I'm not afraid of the command line. Any help is appreciated, thanks!

---

### Post by wilee-nilee on 2011-04-22
I would start with trying to get in with supgergrub2 then fixing the edit.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Use the middle one it will probably get you in.

There is also this option.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Zombiphill on 2011-04-23
Will doing any of these procedures remove the changes I've made to grub?

---

### Post by wilee-nilee on 2011-04-23
> **Zombiphill said:**
> Will doing any of these procedures remove the changes I've made to grub?

Your description is to sparse to know exactly what you did.

We can assume that purging and reinstalling grub might work, only you would know as you have done the work.

I do notice though that your command is missing a / in front of the etc should be this I believe.
sudo vi /etc/default/grub

I suggested these methods; the supergrub first as it looked as if you may know the fix by opening the file, try it again with the / .

It may be that you just in the post notation missed the / hard to tell.

> 

sudo vi etc/default/grub

I get this message:


---

### Post by Zombiphill on 2011-04-23
OK, I'll try and see if any of these works. Thanks for the help!

---

