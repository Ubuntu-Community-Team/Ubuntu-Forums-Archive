---
title: "Debian tty1 login problems"
date: 2009-11-25
forum: General Help
---

### Post by bafman on 2009-11-25
Hello 
This is my first time I am using the forum and I feel sorry that I now decided to registered. Usually I was browsing the various posts and getting the answers to various questions I had but now i find my self in a position that desperately needs help.

I am new to Linux so a newbie but I am trying to gather as much knowledge and eventually get rid of the Windows OS. I am using UBUNTU so i decided to registered in the forums so later i can have the ability to post since i do not intent to use other Linux distro than UBUNTU. So maybe my problem is not related to Ubuntu OS itself but Debian maybe. Also English is not my native language.

A friend of my gave me a game server based in Debian version Lennny/SID and I need to know if it is possible to find the login password. He got the PC from his fathers shop. His father bought it from a customer in order to resell it but my friend decided to keep it hopefully to have a look if the machine it is good for a game server so to load our game  and use it all of the friends. 

It is a Dell PC. It is booting normally and comes to this point

Debian GNU/Linux lenny.sid test-system tty1

test-system login:

I boot from an Ubuntu DVD and mount the HDD. After finding the /etc file I found out that the files i was looking were not accessible so I could not see their contents and hopefully get to the login password. Browsing the files i saw that tomcat 5.5 servlet is installed in the PC.
Later on I got in the terminal and tried some commands. Below are the results:

media/ROOT/etc

unshadow PASSWORD-FILE- SHADOW-FILE

pwunconv can&#8217;t lock passwd file

grpunconv can&#8217;t lock group file

Later tried to use John the ripper to try to recover the password and here are the results again:

john passwd  Loaded 0 passwords cracked, existing...

john --show --shells=-/etc/expired passwd     Loaded 0 passwords cracked, 0 left

I read that john can not recover passwd unless is shown but I could not because trying to unshadow the passwd, passwd-, group, files I could not

Is it possible that the login that the system need is not a administrator password and something else. If I change the bootloader (grub) can I pass overpass the login password and get the desktop?

Is there a way to put the pc in my local network and try to access it from tty1??

There is something I am doing wrong but I do not know what is it. 

A hammer will not help me isn&#8217;t it?:P

Thank you very much

---

### Post by bafman on 2009-11-26
Hi 
I got help with more reading the forum and Google as well and came to these results.

I typed cat /proc/partitions and results are 
7 0 1334364 loop0
3 0 156290904 hda
3 1 154810341 hda1
3 2 1 hda2
3 5 1477948 hda5

Then fdisk -l and results
/dev/hda1 * 1 19273 154810341 83 Linux
/dev/hda2 19274 19457 1477980 5 Extended
/dev/hda5 19274 19457 1477948+ 82 Linux swap /Solaris

I used mkdir /file 
Later used mount /dev/hda1 /mnt/hda1

Results: can&#8217;t find /hda1//mount/ in /etc/fstab or /etc/mtab

I proceed and boot from Ubuntu DVD and check in the ROOT directory etc/fstab. I found this

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
LABEL=ROOT / ext3 default,errors=remout-ro 0 1
/dev/sda5 non swap sw 0 0
I can not make any changes from there cause it need perditions and I could not find a way to log in as administrator so edit the /etc/fstab file

Rebooted and tried to 
mkdir /file and 
Then vi /etc/fstab. The text editor opened and showed nothing so I had to shut down cause I was afraid if I was going to effect the etc/fstab file and do not boot at all.

What are my mistakes?? Is there any way to edit the etc/fstab somehow??

Thank you very much
bafman 
 
Posts: 2
Joined: 2009-11-26 01:18
Top

---

### Post by corncob on 2009-11-26
>  Is there any way to edit the etc/fstab somehow??

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by bafman on 2009-11-27
Hi Corncob
Thank you vey much for your post and informations. I succeed to mount the hda1 at least. It appears that i might not need to edit the file at all.

sudo su
mkdir /media/disk
after fdisk -l game me the same 
/dev/hda1 * 1 19273 154810341 83 Linux
/dev/hda2 19274 19457 1477980 5 Extended
/dev/hda5 19274 19457 1477948+ 82 Linux swap /Solaris

Later typed  mount /dev/hda1 /media/disk

I am still root@bt:~# So ls will give me only install.sh

mount /dev/hda1 /media/disk looks ok and later chroot  /media/disk
And I am in bt:/# 
With ls I can now see the etc file.  cd etc I can see the passwd file in white color letters

I type passwd and is asking for Enter new Unix password
I set a new password and type exit
I am now to root@bt:~# ( i am using Backtrack4 from DVD)
Type  unmount /media/disk and get bash:command not found
Later reboot to see if the system made any changes  No changes to the test-system login. The new password does not work.
I am not sure if i can use john the ripper software to uncover or recover the passwd file that it appears to be shadowed.

So I proceed to add new user according to your instructions
I succeed to ad a new user so I log in as newuser password as I set it.
It comes to marios (which is the new user I set) marios@test-system:$
From here ordinary console commands do not work at all even ls command doesn not give me anything.
Pwd gives me /home/marios

Thank you very much

---

