---
title: "Encrypted drive, deleted key removed password blank desktop"
date: 2012-07-09
forum: General Help
---

### Post by Narmada808 on 2012-07-09
[SIZE=1][SIZE=2]     Before i get into my problems i'll give a little background. I'm running **ubuntu 11.04 natty** as the only OS on my hard drive. After the install i used the ethernet[SIZE=1] [SIZE=2]port  for internet but never got around to installing my wireless driver; my  current living situation has wireless but no wired internet, so [B][U]my machine is not hooked up to the web.
[/U][/B][/SIZE][/SIZE][/SIZE][SIZE=2]After install i opted to  **encrypt** my entire drive. Recently i decided that it was unnecessary for  my current situation, so i tried to remove the encryption. The only  apparent way to do that was to **manually delete the key** in system  settings->keys & encryption. Maybe that's whats causing all of my  problems? :confused:[/SIZE]


[SIZE=2]         ***_My problem is as follows,_*** and happened the 1st time i booted after deleting the key-

I boot to the ubuntu [/SIZE][/SIZE]login. My login name (for purposes of this thread Xxx) appears as normal. 
I click the username and since i deleted the password key it brings me  directly to the desktop, but without my background or the GUI loaded.
It then displays the following errors in a popup-
"There is a problem with the configuration server. (usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)" 
and
"Could not update ICEauthority file /home/Xxx/.ICEauthority"

When i would leave the computer alone at this point it would 'lock' and  ask for my password; the old password was accepted, a blank one was  not.  

 I had problems logging into the terminal at this point (asks for  password, login screen does not) but i got through it and was trying  some fixes when i decided to use the ***passwd*** command, specifically 

```
sudo passwd -d Xxx
```I hoped that it would wipe my password  from the system and therefore restore access.. looks like it was a **big mistake**, because now when i enter the terminal and enter
```
sudo passwd -s Xxx
```it prompts me for a password, when i provide the old one ***it fails***, when i type nothing and hit enter [I][B]it fails.

[/B][/I]so as of right now **i can't use sudo**, which basically stops me from trying anything else. 

Entering ```
less /etc/passwd
``` returns ```
xxx:x:1000:1000:Xxx,,,:/home/xxx:/bin/bash
``` on the line for my user.

~~~~~~~~~~~~~~~~~~~~~~~

If i leave the computer alone, two more graphically pleasing (looks normal, i can move them) windows appear.

 One is the update manager; im not connected to the internet, but hitting the "install updates" brings up an authentication prompt. Again, like in the terminal, **both my old password and ****no password fail**.

The other one states "***Nautilus could not create the following folders: /home/Xxx/Desktop, /home/Xxx/.nautilus.** Before running Nautilus please create these folders or set permissions such that nautilus can create them."*
I am then able to alt+tab between the terminal the other window, and the graphics of doing so look pretty normal

When i leave the computer alone long enough for it to 'lock',  the screen fades all the way to black and without input instantly returns to  normal, without prompting for a password as it did before i used the ***passwd*** command. 



I was planning to wipe the drive and install a different version of  ubuntu soon anyway, but i make music on my computer and my project files  are priceless & irreplaceable- _**All i need is to be able to move files off the drive.**_  Previous attempts to do so with a boot USB have failed, stating "You do  not have the permissions neccesary to view the contents". i have tried ***ecrpytfs-recover-private*** and was still not able to view the files in the temporary folder i created... maybe i'm just a noob? anyway i'm thinking that ***ecrpytfs-recover-private ***might be nonfunctional now that i don't have a password to use with it.... 

**I do have **the long key (8263a0ed94a7cbf26bc464e194781195)  provided when i setup the encryption, but i cant figure out anyway that  it'll help me... maybe just more newbness?



Thanks!!:D

---

### Post by cool110 on 2012-07-09
At this point the best option would be to boot a live CD/USB to get a working sudo.
Mount the drive with your files on.
Then run sudo ecryptfs-recover-private, answer no to knowing your LOGIN passphrase and enter the "long key" when asked for the MOUNT passphrase.

---

### Post by Narmada808 on 2012-07-09
It found the directory but only asked FOR the LOGIN, not if i knew it. For some crazy reason it accepted my old password though! =D  
 it points me to the read-only directory at /tmp/ecryptfs.ZlcDN85W, but when i open the folder i'm denied due to lack of privileges...  =\

---

### Post by cool110 on 2012-07-09
just use sudo -i to get a root shell or gksudo nautilus to open the file manager as root.

---

### Post by Narmada808 on 2012-07-09
Following the directions [here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Short_advanced_way") allowed me to successfully *ls* the contents of /home/xxx, which returns ```
 Desktop Downloads Music Public Ubuntu One
```etc. trying ```
xxx@ubuntu:~$ cd /home/xxx/desktop 
xxx@ubuntu:~$ ls
``` returns [I]"no such file or directory"

[/I]Manually browsing to the folder (both on the drive and on the live USB in /mnt) result in lack of permission notifications.

---

### Post by Narmada808 on 2012-07-09
YES!!!!!! thanks so much you're a life saver!

---

### Post by Narmada808 on 2012-07-09
Alright, so for anyone who may view this in the future this is how i restored access-

1)Booted a live USB
 2)manually mounted my hard drive and changed the root using the following-
```
[FONT=monospace]u[/FONT]buntu@ubuntu:~$ sudo mount /dev/sda3 /mnt 
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/dev 
ubuntu@ubuntu:~$ sudo mount -o bind /dev/shm/ /mnt/dev/shm 
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc 
ubuntu@ubuntu:~$ sudo mount -o bind /sys /mnt/sys

ubuntu@ubuntu:~$ sudo chroot /mnt 
```
and then added a new user with [code]adduser, which upon log in actually brought up the GUI. Using system settings->users and groups i gave my original account the password i had before (i had changed it with the passwd command previously) and **checked the "asked on login"** box. 

Rebooted and everything was prime!!!!!!

---

