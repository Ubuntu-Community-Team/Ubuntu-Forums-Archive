---
title: "completely lost with ubuntu install and setup"
date: 2011-02-06
forum: General Help
---

### Post by csikose on 2011-02-06
...

---

### Post by debd on 2011-02-06
your problem is not really clear.
tell a bit more specifically.
what the problem is and when ...I mean after what it happened.

---

### Post by dino99 on 2011-02-06
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by csikose on 2011-02-06
...

---

### Post by csikose on 2011-02-06
...

---

### Post by debd on 2011-02-06
let me know something..
do you have any other operating system (e.g. windows) installed in the  laptop?
and do you have the Ubuntu bootable cd ?

---

### Post by sanderd17 on 2011-02-06
If you need the data, just boot from a live CD, look for the data in one of the partitions (jus with the file manager) and copy it to an external HDD. Then you can just reinstall ubuntu.

If you need info to set things up, just ask what you want to set up. We might be able to help.

---

### Post by csikose on 2011-02-06
...

---

### Post by csikose on 2011-02-06
...

---

### Post by oldfred on 2011-02-06
Post this so we can see your entire configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by csikose on 2011-02-06
...

---

### Post by csikose on 2011-02-06
...

---

### Post by debd on 2011-02-06
do you remember setting up a different /boot partition while installing ubuntu?
its needed to know.

or just tell me how did you install ubuntu.  insert the boot media, them what option did you choose? remember?

---

### Post by csikose on 2011-02-06
...

---

### Post by oldfred on 2011-02-06
If you are able to install Ubuntu, then just follow the instructions on running the boot script posted above.

Without some good info we cannot help.

---

### Post by csikose on 2011-02-06
...

---

### Post by debd on 2011-02-06
```
sudo mount /dev/sda1 /mnt  
sudo grub-install --root-directory=/mnt /dev/sda
```[COLOR=#000000][FONT=Times New Roman][FONT=Verdana][FONT=monospace]* *[/FONT]
[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Verdana][FONT=monospace][I]
[/I][/FONT][/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=Verdana][FONT=monospace]**[/FONT]
  [/FONT][/FONT][/COLOR]
enter your bootable cd in the laptop.
select try Ubuntu.
open a terminal as I described before.
enter the codes.


now let me tell you one thing in clear. assuming that you have only ubuntu installed in your laptop, and on dev/sda1  I have posted this code here.
this will rescue if there is anything wrong with grub.

---

### Post by csikose on 2011-02-06
...

---

### Post by csikose on 2011-02-06
...

---

### Post by debd on 2011-02-06
Boot your computer up with Ubuntu CD
Open a terminal.
 type "sudo -s"
Enter root passwords as necessary.
Type "grub"
Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". Use whatever your computer spits out for the following lines.
Type "root (hd0,1)", or whatever your hard disk + boot partition numbers are for Ubuntu.
Type "setup (hd0)", to install GRUB to MBR, or  "setup (hd0,1)" or whatever your hard disk + partition nr is, to install GRUB to a partition.
Quit grub by typing "quit".
Reboot and remove the bootable CD.

this is the easiest way buddy.if not with this ....only a guy physically being there with ur laptop may repair it..

---

### Post by csikose on 2011-02-06
...

---

### Post by debd on 2011-02-06
absolutely ur choise

---

### Post by csikose on 2011-02-06
...

---

### Post by SavageWolf on 2011-02-08
Why did you remove all your posts?

---

