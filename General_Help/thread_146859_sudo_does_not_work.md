---
title: "sudo does not work?"
date: 2006-03-19
forum: General Help
---

### Post by brentlidstone on 2006-03-19
my terminal does not do anything when i try to use sudo commands... for instance i tried to install a .deb package with sudo dpkg -i <filename.deb>, then it asked for my password which i entered, then just acts as if nothing happened. I am also still having a problem with nothing in system>administration working, for instance I get a "starting users and groups" dialog then it closes and nothing happens. This is all on a fresh install of ubuntu using the one user account set up during installation.

---

### Post by dermotti on 2006-03-19
try typing the wrong password when you do a sudo and see if it does anything.

---

### Post by xenmax on 2006-03-19
hey brentlidstone, exact same prblm here.
i have managed to get by since a few months now by using su root for all the sudo stuff. And as far as accessing system->administration, i just launch them from cmd-line as root
Not exactly nice i know, but could not figure out the prblm.

---

### Post by codejunkie on 2006-03-19
[QUOTE=xenmax]hey brentlidstone, exact same prblm here.
i have managed to get by since a few months now by using su root for all the sudo stuff. And as far as accessing system->administration, i just launch them from cmd-line as root
Not exactly nice i know, but could not figure out the prblm.[/QUOTE]
open a terminal, login in as root with su then run 
```
adduser username admin
```replace username with your username, then try the apps in the system->administration menu again, when it asks for password give your user password, not the root password.

---

### Post by xenmax on 2006-03-19
I try that and it gives me the error:
  >> adduser: The group `admin' does not exist. <<

Thanks

---

### Post by codejunkie on 2006-03-19
[QUOTE=xenmax]I try that and it gives me the error:
  >> adduser: The group `admin' does not exist. <<

Thanks[/QUOTE]
you must have chose expert install, when you installed ubuntu. you'll need add your user name to the sudoers file, open a terminal login as root and run 
```
export EDITOR=gedit && visudo
```
then add your username to the bottom of the file like this.
```
yourusername	ALL=(ALL) ALL
```
save & close the file, then try the admin apps again if it asks for a password it will be you users not the root account.

---

### Post by Ramses de Norre on 2006-03-19
You can add it then, groupadd -g 106 admin

---

### Post by xenmax on 2006-03-19
Cheers! That works. Thanks a lot. I am sure there are more than just me who will like this solution - refer [http://www.ubuntuforums.org/showthread.php?t=146838](http://www.ubuntuforums.org/showthread.php?t=146838)

Yes, i had to choose export mode to install ubuntu on my new secondary hard-drive. My first and primary hdd had windoze on it and i wanted to install ubuntu on new hdd. Good thing that Ubuntu warned me that auto-install would erase everything on my hard-drive!! :)

---

### Post by Ramses de Norre on 2006-03-19
You can choose which harddrive and partition to install on in normal mode.
I installed ubuntu on my second hd too with win on the first, I just had to choose the right disk out of a list.

---

### Post by xenmax on 2006-03-19
When i saw the warning, i assumed it would completely format my primary hard-drive. :) I did not want to take chances with that - had (still have) a lot of critical AND non-backed-up stuff on my extended partition of first hard-drive :roll:

---

### Post by brentlidstone on 2006-03-19
[QUOTE=codejunkie]open a terminal login as root and run [/QUOTE]

how do i login as root if my name isn't in the sudoers file, nothing in system administration works and i can't use recovery mode? (unless there is a way to add my name to the sudoers file in recovery mode)

---

### Post by codejunkie on 2006-03-19
[QUOTE=brentlidstone]how do i login as root if my name isn't in the sudoers file, nothing in system administration works and i can't use recovery mode? (unless there is a way to add my name to the sudoers file in recovery mode)[/QUOTE]
[LEFT]***(Part1)***
if you did an expert install, it will ask you to enter a root password, along with your normal user name & password when you install ubuntu. open a terminal and enter ```
su
```then give the password you set for the root user. this will give you root privliges, then run 
```
export EDITOR=gedit && visudo
```
add your username to the bottom of the file like this
```
yourusername	ALL=(ALL) ALL
```
save & close the file, and try one of the Systen>Administration apps like like synaptic *when it asks for a password* **use your normal user password **not the root password.
---------------------------------------------------------------------------------------------------------
***(part2)***
if the above does not work, you need to insert your ubuntu install cd, at the cd boot menu enter
```
rescue
```follow the instructions given and when you reach the terminal , enter 
```
sudo passwd root
```and set a new root password, then reboot by entering 
```
reboot
```remove the cd and login like you normaly would, and redo the steps in ***(Part1)***.[/LEFT]

---

### Post by newpants2003 on 2006-04-03
reallyyyyyyyyyyyyyyyyyyyyyyyyyyyyy helpss!!!!!!!!!!
thanx a lot

---

### Post by ZiGz on 2006-04-03
Thanks that worked great.  Question: Does my user account have all the privledges now that they warn you about not using root for?

---

### Post by codejunkie on 2006-04-04
[QUOTE=ZiGz]Thanks that worked great.  Question: Does my user account have all the privledges now that they warn you about not using root for?[/QUOTE]
you always have to use root account in linux, basicly that's what sudo does, it allows a normal user to access programs as root without having to login as root. 
but if everything is working fine under your normal user account when using sudo. i would disable the root password with ```
sudo passwd -l root
``` just for the added security.

---

### Post by xenmax on 2006-04-04
codejunkie,

why not post your solution as a sticky? i must have posted this thread as a possible solution 5-6 times already and you might have done so similarly, not to mention others. probably the stick can be titled "Read for ppl who did an expert install" or something like that
just a thought....

Thanks,
xenmax

---

### Post by mooon on 2006-04-04
newby here,
i have installed the expert mode as well because afraid of losing files. i cannot type anything after i try to log in on root. does this mean i do not have expert rights or that a password wasn't set when i installed ubuntu?

i could reinstall if that is needed, haven't made a lot of changes yet but would save some trouble.

---

### Post by xenmax on 2006-04-05
> i cannot type anything after i try to log in on root. Can you please elaborate on that? If you are trying to login to system as root, then it is disabled in ubuntu by default [even if you did an expert install AFAIK].
At start-up, use your regular username and password

---

### Post by mooon on 2006-04-05
hello,

i tried it differently now and it does work.
now i will try your info before.

thx anyway :)

---

### Post by clownius on 2006-05-09
ty im finally able to do something.

---

### Post by gmcle454 on 2006-05-14
Thanks! For some reason, I too wasn't listed in the sudoer file. This thread fixed my problem.

I've used Gentoo for a couple of years now. With Gentoo wheel is one of the default groups, but it isn't even present in Ubuntu. On the flip side of the coin, the adm group used in Ubuntu isn't in Gentoo. It seems that adm is replacing wheel for Ubuntu's su permissions--Is this a correct observation?

Should I even bother adding the wheel group since (a)sudo works fine and (b)adm seems to handle su privileges?

---

