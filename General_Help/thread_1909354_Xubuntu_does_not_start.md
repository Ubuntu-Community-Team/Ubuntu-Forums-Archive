---
title: "Xubuntu does not start"
date: 2012-01-15
forum: General Help
---

### Post by enuff on 2012-01-15
Hello,
I've been using Xubuntu for a month and everything was fine until this morning it failed to start.
I tried to make the NumLock on by default by adding the following line:

greeter-setup-script=/usr/bin/numlockx on

to

leafpad/etc/lightdm/lightdm.conf

On the next boot I get "checking battery state.." and it freezes there. I read that this problem is caused by video controller drivers, but I don't have an external VGA. I am using the Intel VGA integrated on the motherboard. 
The fact that the problem appeared immediately after editing the
leafpad/etc/lightdm/lightdm.conf
makes me think that the problem is there. 
I would like to delete the line that I added, but I need to start Xubuntu first. 
I press CTRL+ALT+F1 and to open a command line, but I don't know how to edit the 'lightdm.conf' file from there. 
How can I skip this battery state check in order to log in Xubuntu?

---

### Post by AnotherMuggle on 2012-01-15
Did you make a backup of the file before you edited it?

If not then after you have pressed CTRL+ALT+F1 to switch to tty1 you can enter the following commands:

sudo nano /etc/lightdm/lightdm.conf

This will open the text file in a console editor (called nano).  Now inside the console revert any of the changes you made to the file.

Once you are done making changes press Ctrl+X and you will be asked if you want to save the file.  Enter y and the file will be saved and you will drop back to the command prompt.

Now enter:

sudo shutdown now -r

Your computer will reboot and hopefully you will get all the way to your desktop.

Good luck!

---

### Post by enuff on 2012-01-15
I  could not do it with 'nana' because it opened a black fine and there was nothing to delete. 
However, I typed "startx" and Xubuntu loaded (something I should have tried first). Once in Xubuntu I opened 
leafpad/etc/lightdm/lightdm.conf
and deleted the line that I had previously added. 
Now Xubuntu is booting normally, but I still have to figure out how to keep the NumLock on by default since my user password contains numbers and it drives me crazy having to hit NumLock very time I log in.

---

