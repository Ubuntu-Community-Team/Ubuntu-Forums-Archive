---
title: "Session lasting less then 10 seconds"
date: 2010-02-24
forum: General Help
---

### Post by funkyguy4000 on 2010-02-24
Okay so here is my problem.

I boot up like normal boom boom, i put in my log in info and it shoots me this message that says: 

Your seession only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that here is some installation problem or that you may be out of diskspace.   Tryloggin in with one of the failsafe sessions to see if you can fix this problem.

and it then gives me this option to view details(~/.xsession-erros file)

I click it and it shows this:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im0switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default
mkdtemp: private socket dir: Permission denied


I did have to do a manual FSCK a little while ago.  The thread about that is right here: [http://ubuntuforums.org/showthread.php?t=1370168](http://ubuntuforums.org/showthread.php?t=1370168)

I am not the administrator, my brother is and he is out of town for a few months and he would kill me if he found out i screwed up his awesome computer.  So the faster the help that would be awesome.

I am not an ubuntu user, i'm a windows person:confused:.  So if you have any ideas on helping me please just shoot em out and i'll try to figure out what you mean.  

Thank you so much!!!!
:popcorn::popcorn::popcorn:

---

### Post by PoHandle on 2010-02-24
When at the login screen, try switching to TTY console by pressing CTRL + ALT + F***X*** (where ***X*** can be 1-4)
Once at the CLI, you'll be prompted to log in.  Enter your login information, then type:
```
sudo chmod a+w /tmp
```
You'll be asked for your password on that account.
After that, you can switch back to your GDM screen (usually CTRL + ALT + F7) and see if you are now able to log in.

---

### Post by funkyguy4000 on 2010-02-24
whenever i put in the sudo command it says
shannon is not in sudoers file, this incident will be reported

and then it doesn't do anything

---

### Post by PoHandle on 2010-02-24
I see. In order to be able to edit the permissions of /tmp, you must have root permissions.  Since your account is not able to use 'sudo'. you will have to find another way to gain root.

Another way I can think of is booting into single user mode.  However, if your brother was cautious enough not to include other users in the sudoers group, then he has probably set a root password, in which case the following method will not work unless you know/guess the root password.  You might get lucky, though. I know a few friends that never set root passwords after a fresh install. haha.

Try this:

[LIST=1]
[*]Reboot the computer
[*]When at the Grub menu, hit 'e' to edit an entry. (if the Grub menu doesn't appear, reboot again and hold shift until the menu displays)
[*]Look for the line that looks like ```
linux	/boot/vmlinuz-2.6.31-x-xx root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ro vga=792 quiet splash
```
[*]Add the word **single** after **ro** in that line so it reads like  ```
linux	/boot/vmlinuz-2.6.31-x-xx root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ro **single** vga=792 quiet splash
```
[*]Now hit CTRL + X to boot
[*]You'll be greeted with a menu on a blue screen.  Select **root - Drop to root shell prompt**
[*]You will be prompted for the root password.  If one has not been set, you should be able to just hit Enter and be at the root CLI.
[*]Now enter the chmod command from my earlier post
[*]Reboot normally
[/LIST]

If you get stuck at the root password prompt, you can guess as many passwords as your heart desires.

If this does not work, you might be able to use a LiveCD and chroot your partion to chmod the /tmp directory.  I'm probably wrong though.

---

### Post by funkyguy4000 on 2010-02-24
Nah that isn't working for me.
It says to go into one of the failsafe terminals.  Any commands I could do there without the sudo command that would help me?

---

### Post by PoHandle on 2010-02-25
Unfortunately, you will need to have root permissions to do this.  Using the sudo command is just one way to do this.

Ok, so this is the last thing I could think of.

You'll want to boot from an Ubuntu LiveCD, mount the partition of your Ubuntu installation, and change the permissions of the /tmp folder.  This will work and give you root (kinda) permissions in a dirty, security breach type of way.

So go find an Ubuntu LiveCD, or if you don't have one, download an .ISO copy and burn it to a cd. ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download))

[LIST=1]
[*]Boot from the LiveCD (have the CD in the drive at boot time)
Select your preferred language then select "Try Ubuntu without making changes to the computer"

[*]After it boots, mount the partition with the Ubuntu installation.
This is easy if you only have one OS partition on the computer, but can be confusing if there are multiple.
Click on Places on the top panel, then look for *XXX* GB Filesystem where *XXX* is the size of the partition.  Click it to mount it. (If you see multiple ones, mount them one by one until you find the Ubuntu one)

[*]Open a terminal, and enter ```
cd /media/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```
where *xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx* is the UUID of the partition.

[*]Change the permissions of the /tmp folder with ```
sudo chmod a+rwx tmp
```
From the LiveCD, sudo will not ask you for a password and give you root permissions (although they technically are not the root permissions of the installation, it still works)

[*]Reboot normally.
[/LIST]

If you have any trouble locating the Ubuntu installation, try ```
sudo fdisk -l /dev/sd***x***
``` where ***x*** a letter identifying your harddrive. (Mine is /dev/sda, and yours should be too if you only have one harddrive)  Any partitions with "Linux" (not "Linux Swap") under the System column is a possibility to be the Ubuntu installation.  If you only see one, that's it, and you can use the information listed to determine which partition to mount.

---

### Post by funkyguy4000 on 2010-02-25
alright so it is shooting me these errors

Buffer I/O error on device sr0, logical block 278918
end_request I/O error dev sro sector 1115676

and also 

Squashfs error sb_bread failed reading block
SQUASHFS error unable to read block

Is that a problem with the drive or what,  I've tried using different software to burn, different disks, different drives, different burn drives.  It all is fine but for some reason it can't read the cd.

---

### Post by PoHandle on 2010-02-26
When do you get these errors?  If they are at boot time, you might have BIOS related issues.

---

### Post by funkyguy4000 on 2010-02-27
okay so i have another thread that is now active again it has like all the info, and some people have been helping me out.

Here is the thread

[http://ubuntuforums.org/showthread.php?t=1373505](http://ubuntuforums.org/showthread.php?t=1373505)

If you have any ideas it would be awesome if you posted them on there for people who just want to find 1 thread to figure out a problem

---

### Post by PoHandle on 2010-03-03
So you're saying this is a duplicate post of an active 3 month old thread in which you gave more information on your problem?  Wow. I'm sorry I wasted my time on this thread.  Good luck with your problem.

---

