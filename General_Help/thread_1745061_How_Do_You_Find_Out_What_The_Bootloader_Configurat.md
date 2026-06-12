---
title: "How Do You Find Out What The Bootloader Configuration File Is Named?"
date: 2011-04-30
forum: General Help
---

### Post by TheNewbieGeek on 2011-04-30
How do you find out what the bootloader configuration file is named? I am setting file permissions...would it be wise to set the entire boot directory to 700? Thanks for the replies.

EDIT: I finally found a link with the information thank you.

---

### Post by cariboo on 2011-04-30
You're a little vague again, by bootloader I assume you mean grub, the configuration file is called grub.cfg, and is located in /boot/grub.

Can you explain why you feel the need to change file and directory permissions from the default?  If you recursively change the permissions of /boot to 700, you're going to cause serious breakage.

---

### Post by TheNewbieGeek on 2011-05-01
Thanks for your answer...I'll post the tutorial I am working on...it states to change the permissions of the system and daemon configuration files to 644 home folder to 700 and bootloader configuration files to 700 and firewall scripts to 700.

[http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](http://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions)

I don't know the name of the system configuration files I should change or where they are. I also don't know where the firewall scripts are located or what there named. same with the bootloader configuration files. I do know where home folder is and I have set those permissions.

Anyway I am sorry if I have been rude.

---

### Post by cariboo on 2011-05-02
Most of the files used by grub are in /boot/grub, if you check the permissions you'll see that they all have permissions of 644, except for grub.cfg which has the permission set to 444.

644 equals:

[LIST]
[*]read by owner
[*]write by owner
[*]read by group
[*]read by others
[/LIST]

444 equals:

[LIST]
[*]read by owner
[*]read by group
[*]read by others
[/LIST]

all the files are owned by root, and the group is root.

---

