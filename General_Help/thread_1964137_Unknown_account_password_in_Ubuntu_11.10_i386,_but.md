---
title: "Unknown account password in Ubuntu 11.10 i386, but I dont have a password set?"
date: 2012-04-23
forum: General Help
---

### Post by danworsley on 2012-04-23
Hi All,

I am new to Ubuntu and I have just moved over from Windows.
I have installed the os above, during installation I entered a user account password to continue the installation. After the installation was complete I access the user accounts in system settings, clicked the password box under Login Options and changed the Actions box to "Log in without a password".
Since then I can boot into ubuntu without a password, if my laptop goes into sleep or hibernate I wont need a password, but to perform any administration actions it prompts for a password, but I have no idea what it can be? I tried the password I used in the original installation but it wont accept it. I went back to user accounts to put everything back to how it was, but it needs this password before I can make any changes?

Help needed, and would be very much appreciated! :lolflag:
Thanks!

Dan.

---

### Post by cmont899 on 2012-04-23
This should be the password of the user that you are logged in as. Try opening the terminal and running the command passwd to reset your password and see if it works with the new one.

---

### Post by imachavel on 2012-04-23
very bad, ubuntu should ask for the password to log in as well as to make administrative changes. It is very secure in this way. If you had this problem with windows, you could not reset the password unless you got into user account control, meaning you couldn't log in if you didn't know the password to get to control panel -> user account control. Otherwise you would need to download and burn a password reset .iso disk, and burn it with an .iso burner to bootable media for example cd rom or dvd rom, whichever your disk type your burner supports, and boot to it. And I've never gotten any of those dos .exe bootable password reset disks to work. The linux live cd might be able to help you out there, but this might work better, as bios and booting and recovering into boot option is from main board with boot media is a pain in the *** no matter what file system OS you are using.

When you installed linux, linux should have made it a little easier to recover the password to get into your OS file system kernel to load all the files and everything else. The recovery mode in linux is not a gui with less programs running like it is in windows with possibly the same necessity for permissions. There is a recovery mode which seems to be accessible without the same need for permissions, it uses the bash shell prompt interface, you can do anything, unmount the file system, run fsck, etc. So here you are with this option:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

write it down, memorize it. This time don't forget the password. Be lucky you aren't using ntfs winblows, but this time, treat the file system more delicately then you would windows. If you install something, a program, anything... like for example AN OPERATING SYSTEM :lolflag:, and it asks for a password :lolflag:, write it down and don't forget it

---

### Post by imachavel on 2012-04-23
> **cmont899 said:**
> This should be the password of the user that you are logged in as. Try opening the terminal and running the command passwd to reset your password and see if it works with the new one.

But let's take a look at this I was playing around with it a bit:

passwd
Changing password for danel.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
Password unchanged
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
danel@danel-Dimension-4700:~$ passwd
Changing password for danel.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
Sorry, passwords do not match
passwd: Authentication token manipulation error
passwd: password unchanged
danel@danel-Dimension-4700:~$ passwd
Changing password for danel.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully


You need the old password. Only way I think to change the password without entering the old one is in grub, when your hdd is recognized to boot to, and the OS hasn't loaded yet, but basic basic basic basic boot sector has, and you are at the grub menu. You choose terminal prompt, and I believe to reset the password you don't need the old password. I THINK!

---

### Post by fara on 2012-04-23
[Edit: check out my next post]

Hi

there is a guide for resetting the lost password at here:
[https://help.ubuntu.com/community/LostPassword]("https://help.ubuntu.com/community/LostPassword")

The standard way should be working for your case, give it a try

Cheers

---

### Post by fara on 2012-04-23
Well the guide I mentioned in the previous post might be a bit old, try this first:

[LIST=1]
[*]reboot your computer and while you're at grub menu choose the current ubuntu version with (recovery mode) at the end of its name.

[*]Ubuntu starts booting in recovery mode, everything would be in text mode for now but don't worry, it'll be very easy. you'll be shown a menu after a while called "Recovery Menu".

[*]In the recovery menu choose "remount". after remount is done a message saying "finished, please press ENTER" will be shown, press enter and you'll be back to the "Recovery Menu".

[*]Now choose "root" from the menu. You should be seeing a prompt like "root@computername:~#" which is the root prompt of course

[*]at root prompt type:
```
passwd user
```
type your username instead of user in the above line

[*]Now passwd asks for your new UNIX password twice, remember that nothing would be shown when you're typing passwords.

[*]If everything goes perfectly you will see a message like:
```
passwd: password updated successfully
```

[*]Type "exit" or press CTRL+d at the root prompt to get back to recovery menu.

[*]In the recovery menu choose resume to resume to boot into your system, your new password should be effective by now.

[*]Reboot and boot normally.
[/LIST]

I hope this helps.

Cheers

---

### Post by danworsley on 2012-04-23
> **imachavel said:**
> very bad, ubuntu should ask for the password to log in as well as to make administrative changes. It is very secure in this way. If you had this problem with windows, you could not reset the password unless you got into user account control, meaning you couldn't log in if you didn't know the password to get to control panel -> user account control. Otherwise you would need to download and burn a password reset .iso disk, and burn it with an .iso burner to bootable media for example cd rom or dvd rom, whichever your disk type your burner supports, and boot to it. And I've never gotten any of those dos .exe bootable password reset disks to work. The linux live cd might be able to help you out there, but this might work better, as bios and booting and recovering into boot option is from main board with boot media is a pain in the *** no matter what file system OS you are using.

When you installed linux, linux should have made it a little easier to recover the password to get into your OS file system kernel to load all the files and everything else. The recovery mode in linux is not a gui with less programs running like it is in windows with possibly the same necessity for permissions. There is a recovery mode which seems to be accessible without the same need for permissions, it uses the bash shell prompt interface, you can do anything, unmount the file system, run fsck, etc. So here you are with this option:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

write it down, memorize it. This time don't forget the password. Be lucky you aren't using ntfs winblows, but this time, treat the file system more delicately then you would windows. If you install something, a program, anything... like for example AN OPERATING SYSTEM :lolflag:, and it asks for a password :lolflag:, write it down and don't forget it


Thanks for the link, i followed the instructions through and I have now got control of my account.
I did have the original password written down, but after i disabled the password requirements it would no longer accept it for administration privileges.

Anyway, I wont be trying it again! 

Thanks for the help everyone

Dan

---

### Post by perkins4306 on 2013-02-12
I am unable to boot up to the grub menu. I hit shift as soon as my computer starts to reboot. A black screen with "Grub"  in the top left corner appears but quickly disappears. Help! What am I doing wrong?

---

