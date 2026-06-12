---
title: "I was wondering if it was possible to boot to win xp from linux."
date: 2006-05-31
forum: General Help
---

### Post by bartosz on 2006-05-31
Hello,
      I was wondering if it was possible to boot to win xp from linux when it restarts. Thus it will automatically choose win xp when grub loads. Or Vice versa, so when I restart windows xp, it will load linux. Is it possible to do that? When I previously used Suse, I found that they had the option to restart to windows directly rather than to suse. I was wondering if Ubuntu had the same capabilities. Thank you.

---

### Post by mr.diogo.schneider on 2006-05-31
Sure. And that's pretty simple, indeed. Just change the value of "default" in /boot/grub/menu.lst to whatever entry you want to boot into.

---

### Post by bartosz on 2006-05-31
Hello,
      What I meant was, would it be possible to implement a restart button to either linux or windows to boot directly to the other operating system? Thank you.

---

### Post by Sutekh on 2006-05-31
Yes it is possible.

For this to work, you need to 
 
 1) Edit your GRUB menu
 ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
 sudo gedit /boot/grub/menu.lst
``` and find this line ```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
**default         0**
 
``` and change it to
 ```
**default        saved**
``` 
 2) Then you need to make sure that the GRUB entry that you want to boot to has the line **savedefault**, for example
 ```
title           Microsoft Windows XP Professional
root            (hd1,0)
**savedefault**
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
 
``` 
3) Finally you can use this code to echo the menu default to grub using a pipe (the | ) and then shutdown the computer for a reboot
 ```
echo savedefault --default=**N** --once | grub
sudo shutdown -r now
``` Changing **N** for the number corresponding to the entry you want to boot.
 When the GRUB menu starts the N'th GRUB menu entry will be automatically selected and booted.
 
 You can add the code to a launcher (button) and call it "Boot Windows" or something.
 
 You can also use
 ```
sudo grub-reboot **N**
``` to change the default boot entry. This does exactly the same thing as the code above, yet waits for you to give it the okay to reboot. 
 
 So you can use whichever method appeals to you.

---

### Post by bartosz on 2006-05-31
Thank you very much for the replies, I will try that out right now. Thank you again.

---

