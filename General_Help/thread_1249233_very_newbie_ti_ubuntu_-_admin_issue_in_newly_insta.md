---
title: "very newbie ti ubuntu - admin issue in newly installed"
date: 2009-08-25
forum: General Help
---

### Post by turf on 2009-08-25
i see this writtings when i open the command prompt.:

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.
```

i installed this thru install inside windows option as
 i have a 8.10 desktop version of this ubuntu.

I  wanted to be the administrator but everytime i type su
it fails since the only password i can remember is the user.

I dont really think i did input password and admin when i install this.. 
can anyone tell me how to be an admin please. :confused:

---

### Post by tarps87 on 2009-08-25
The root user is disabled on Ubuntu.
As the message says, to run a program/ command with admin privileges use ```
sudo *commandName*
```

---

### Post by MohanaRao on 2009-08-25
Hi sir/madam,

    I am newly started using ubuntu with dual boot and installed ubuntu 9.04 in unallocated space in harddisk 20gb. My harddisk capacity is 80gb. Ubuntu is running slowly on my machine.
     This is my system configuration.
      Processor -  Intel celeron 3.06GHz.
      Ram -          1.5GB.
      HDD-           80GB.
      
    I don't have graphic card on my mohterboard, but i am using compiz effects it's working fine without any problem. And one more thing is when i am viewing youtube videos the processor running at its peak level continuoesly. I tried both browsers firefox and opera. Apart from that everything is working fine. So suggest me what are the changes should i make to run ubuntu smoothly. Thanks in advance and thanks for spending your time for me.

Regards, 
Mohan

---

### Post by P4man on 2009-08-25
> **turf said:**
> 

I  wanted to be the administrator but everytime i type su
it fails since the only password i can remember is the user.


Please read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by P4man on 2009-08-25
> **MohanaRao said:**
> Hi sir/madam,

    I am newly started using ubuntu with dual boot and installed ubuntu 9.04 in unallocated space in harddisk 20gb. My harddisk capacity is 80gb. Ubuntu is running slowly on my machine.
     This is my system configuration.
      Processor -  Intel celeron 3.06GHz.
      Ram -          1.5GB.
      HDD-           80GB.
      
    I don't have graphic card on my mohterboard, but i am using compiz effects it's working fine without any problem. And one more thing is when i am viewing youtube videos the processor running at its peak level continuoesly. I tried both browsers firefox and opera. Apart from that everything is working fine. So suggest me what are the changes should i make to run ubuntu smoothly. Thanks in advance and thanks for spending your time for me.

Regards, 
Mohan

Mohan, please start a new thread as your question is in no way related to the original poster's questin.

---

### Post by turf on 2009-08-25
> **tarps87 said:**
> The root user is disabled on Ubuntu.
As the message says, to run a program/ command with admin privileges use ```
sudo *commandName*
```


what are examples of command in sudo?
to make me as an admin?

can i just type

> sudo admin

is this it?

---

### Post by P4man on 2009-08-25
> **turf said:**
> 

> sudo admin

is this it?

sigh..

Please read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

its all in there, including examples. If you got any questions left after reading it, feel free to ask though.

---

### Post by turf on 2009-08-25
> **P4man said:**
> sigh..

Please read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

its all in there, including examples. If you got any questions left after reading it, feel free to ask though.


i've actually follow the link

i've type 

turf@ubuntu:~$ sudo mypassword turf
[sudo] password for turf: [*once again i type my passwordhere same as the user password*]
sudo: mypassword: command not found

now thats strange. :lolflag:


i really wanted to have control ever whatsgoing onafter all ican install it again if i mess up.

---

### Post by nothingspecial on 2009-08-25
If you want to run an app as root, for example gparted type

```
sudo gparted
```

if you want to use the mv command as root to move something to /usr/bin/ type

```
sudo mv something /usr/bin/
```

If you just want to move something around your home directory then you don`t need sudo

```
mv something ~/Videos
```

---

### Post by turf on 2009-08-25
i've actually got to become the admin as i type sudo -i

but then i wanted it didnt prompt me to give a password. 
now thats something i dont want.

i still want a password for it. so i'll be the only who can administer:)

---

### Post by vedek on 2009-08-25
that is why the root account is disabled by default due to the fact that with a inexperienced user using admin all the time can present major problems, even a / instead of a \ can cause damage to your system, so sudo is there to make sure that the commands that you want to access you at least have time to double check it.

---

### Post by nothingspecial on 2009-08-25
Once you`ve used sudo and typed your password you don`t have to type it again for 5 or 10 minutes. I forget the default time. You can remove this feature if you want.

Don`t worry though after 5 or 10 minutes you will be prompted for your password again, the next time you use sudo.

---

### Post by 3rdalbum on 2009-08-25
If you're worried about someone getting on your computer and using "sudo" and not being prompted for your password, you can force an immediate timeout by typing this command:

```
sudo -k
```

That's the whole command; it tells sudo to forget your password immediately rather than remember it for the next ten minutes.

---

### Post by MohanaRao on 2009-08-25
I am extremely sorry before i don't know how to start a new thread. sorry for interrupting you.

---

### Post by P4man on 2009-08-25
> **MohanaRao said:**
> I am extremely sorry before i don't know how to start a new thread. sorry for interrupting you.

LOL. Maybe you should start a thread then asking how to start a new thread ? :D

Just go to the appropriate forum (navigation on top): 

Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > General Help  

Or click this link:

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

Then near the top, you will see a "new thread" button in dark grey.

---

### Post by turf on 2009-08-25
i did it. and the sudo prompt me to ask password everytime i wanted to use the root account.. thanks guys.

:P

---

