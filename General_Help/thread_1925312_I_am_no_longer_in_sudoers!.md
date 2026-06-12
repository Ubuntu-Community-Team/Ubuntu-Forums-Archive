---
title: "I am no longer in sudoers!?"
date: 2012-02-14
forum: General Help
---

### Post by r9tysix on 2012-02-14
Hello , im using ubuntu 11.10 amd
Today i tried to update my distribution 
```
sudo apt-get update
```i got this message:
```
usr is not in the sudoers file.  This incident will be reported.
```mmm i found a solution
```
sudo visudo etc..
```but i can't execute this command as im not in sudoers :D , this solution didn't work.

the only thing that i can do now is login as root and then execute the command.
i tried to change the root passwd. 

```
usr@u:~$ passwd
Changing password for usr.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
[COLOR=Red]Password unchanged[/COLOR]

```:(

----------------------------------------
More infos:
when i try to unlock my account from "Account Settings" 
[IMG]http://img193.imageshack.us/img193/6715/screenshotat20120214163.png

&

```
usr@u:~$ groups
usr vboxusers
usr@u:~$ 

```im no longer in admins group :(
Thank you

---

### Post by Habitual on 2012-02-14
```
su - root
```
password

and you're there. Do what you need to.

---

### Post by SorryGoFish on 2012-02-14
> **Habitual said:**
> ```
su - root
```
password

and you're there. Do what you need to.

Are you sure? I thought the root password was randomized, not made identical to any specific user's password.

**Edit** I see the OP claimed to log in as root:

> **r9tysix said:**
> 
the only thing that i can do now is login as root and then execute the command.
i tried to change the root passwd. 

```
usr@u:~$ passwd
Changing password for usr.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
[COLOR=Red]Password unchanged[/COLOR]
[/CODE


This does not look like you're logged in as root. The prompt you pasted says `usr` is your username, not root. The result at the end, I'm guessing, is because you didn't change the password (you entered the same password 3 times, I believe). 

In order to get yourself back in the admin group you'll need to boot into single user mode. And issue a command to add yourself to the group admin.

To boot to single user mode, [here's one hit on google]("http://blog.troyastle.com/2010/06/boot-to-single-user-mode-in-ubuntu-1004.html").

To add yourself to sudo group (assuming `usr` is your username, and `admin` is the admin group):
[CODE]usermod -a -G admin usr
```

(Note, you may also want to add yourself to the group `sudo`. I believe the sudoers group is different for different versions of Ubuntu.)



By the way, you removed yourself from all groups. I guess you tried to add yourself to the group vboxusers, but accidentally, cleared out all the other groups? To see what other groups you should add yourself to, you may create a new user, and see what default groups are given to that user. This can be done after you add yourself to admin in single user mode, and reboot.

---

### Post by SorryGoFish on 2012-02-14
Maybe I should have just sent you to[ this stack exchange answer]("http://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user").

Let us know if you have any trouble.

---

### Post by r9tysix on 2012-02-14
> **SorryGoFish said:**
> Maybe I should have just sent you to[ this stack exchange answer]("http://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user").

Let us know if you have any trouble.


Thank you SorryGoFish Solved im now able to sudo :D. 
but the error in the picture (in the first post) is back  after rebooting :(

---

### Post by SorryGoFish on 2012-02-14
> **r9tysix said:**
> Thank you SorryGoFish Solved im now able to sudo :D. 
but the error in the picture (in the first post) is back  after rebooting :(

It's strange that it's asking for the root password, and not your own. If you want, you can set the root password. I'm sure this is generally discouraged though, so be sure you put a very good password.

```
$ sudo su -
# passwd
# exit
$ 
```

Then, you can give the root password when specifically asked.

---

### Post by josephmills on 2012-02-14
ummm. this is kinda wired could you open you terminal and type in 
```
sudo tail -n 20/etc/sudoers

``` and paste here thanks.

---

### Post by r9tysix on 2012-02-14
[COLOR=Red]SOLVED[/COLOR]
Thank u guys , 
SorryGoFish  Thanks :D

---

### Post by Habitual on 2012-02-14
> **sorrygofish said:**
> maybe i should have just sent you to[ this stack exchange answer]("http://askubuntu.com/questions/70442/how-do-i-add-myself-back-as-a-sudo-user").

Let us know if you have any trouble.

+1

---

