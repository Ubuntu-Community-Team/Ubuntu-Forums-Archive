---
title: "linux simple hacks"
date: 2009-09-12
forum: General Help
---

### Post by dink123 on 2009-09-12
does anyone know how to enter as the superuser using the command line, when the GRUB starts up?

---

### Post by NoaHall on 2009-09-12
You can create "root" as a log-inable account, but this is not recommended at all. Can I ask why you want to do this? The title "linux simple hacks" suggests under the current day meaning of the word that you instead to break in to a system in order to cause damage against the admins wishes.

---

### Post by dink123 on 2009-09-12
> **NoaHall said:**
> You can create "root" as a log-inable account, but this is not recommended at all. Can I ask why you want to do this? The title "linux simple hacks" suggests under the current day meaning of the word that you instead to break in to a system in order to cause damage against the admins wishes.
  
i am doing this for a small assignment under operating systems. with the intention of understanding how o/s's(esp LINUX) work. since that is also a kind of a hack, i put that  title. there is no intention of harming others. 
so if you know tell me please..

---

### Post by NoaHall on 2009-09-12
Ah, okay. 
Warning - don't do this unless you know what you're doing.
```
 sudo gedit /etc/gdm/gdm.conf 
```

Find this line -```
 [security]
# Allow root to login.  It makes sense to turn this off for kiosk use, when
# you want to minimize the possibility of break in.
AllowRoot=false
```

Change AllowRoot to "=true"

---

### Post by mcduck on 2009-09-12
> **dink123 said:**
> does anyone know how to enter as the superuser using the command line, when the GRUB starts up?

When the grub starts up? Not possible, you aren't even running Linux at that stage, so there's no superuser (or any other user) at that stage.

Or do you mean how to get the system to boot into root console from Grub? In that case just select the recovery mode from Grub menu, and when asked what you want to do select "drop to root shell prompt".

(note that if you are using Grub2 the recovery mode is listed as "single user mode").

---

### Post by mcduck on 2009-09-12
> **NoaHall said:**
> Ah, okay.

```
 sudo gedit /etc/gdm/gdm.conf 
```

Find this line -```
 [security]
# Allow root to login.  It makes sense to turn this off for kiosk use, when
# you want to minimize the possibility of break in.
AllowRoot=false
```

Change AllowRoot to "=true"

That doesn't have anything to do with Grub. That would allow logging into desktop as root user (which should never, ever, be done on any machine connected to network, or actually used for anything.). Also that doesn't enable the root account itself. Which is something that can't be discussed in these forums.

---

### Post by NoaHall on 2009-09-12
I didn't say it did have anything to do with Grub. I only said it was possible to enable logging in to it. And i've already warned him/her. You're making up things to argue with me about. I never said he should do it, I said quite the oposite. Read my first post before attacking me, please. Besides, other distros enable it by default. Arch etc. It's fine as log as you know what you are doing.

---

### Post by mcduck on 2009-09-12
> **NoaHall said:**
> I didn't say it did have anything to do with Grub. I only said it was possible to enable logging in to it. And i've already warned him/her. You're making up things to argue with me about. I never said he should do it, I said quite the oposite. Read my first post before attacking me, please.

No, I only pointed out that the original poster asked how to do this from Grub.

No need to be overly defensive, since I never claimed that you'd have said such things. Most of the post (the part about logging into desktop as root ) was of course intended as advice to the OP).

---

### Post by dink123 on 2009-09-12
> **NoaHall said:**
> Ah, okay. 
Warning - don't do this unless you know what you're doing.
```
 sudo gedit /etc/gdm/gdm.conf 
```Find this line -```
 [security]
# Allow root to login.  It makes sense to turn this off for kiosk use, when
# you want to minimize the possibility of break in.
AllowRoot=false
```Change AllowRoot to "=true"

but in order to do this you have to enter in to X-server. can you please tell me what does this do?

---

### Post by Liolikas on 2009-09-12
Lets say you are in situation that you forgot your sudo password. Not everything is lost. You can boot from liveCD, access /etc/shadow file and enter encrypted new root password into it or try to decrypt existing password with various cryptography software. But you have to understand basics of modern cryptography and google basic information about shadow file.  
---
But there is no simple solution like win98 press F8 (or sth) to enter DOS at boot (as superduper user without password!!!!) and rm C:/windows/username.(sth) and reboot and done. :D

---

### Post by NoaHall on 2009-09-12
Well, if you want to do it from the terminal 

```
 sudo nano /etc/gdm/gdm.conf 
``` 

And do the same. It enables the logging in of the "root" user. Which is basicly what you become once using "sudo"

---

### Post by dink123 on 2009-09-12
> **mcduck said:**
> When the grub starts up? Not possible, you aren't even running Linux at that stage, so there's no superuser (or any other user) at that stage.

Or do you mean how to get the system to boot into root console from Grub? In that case just select the recovery mode from Grub menu, and when asked what you want to do select "drop to root shell prompt".

(note that if you are using Grub2 the recovery mode is listed as "single user mode").

Thank you..i tried it.
in this way anyone can enter in to the system and change the settings if the GRUB is not password protected. am i right?

---

### Post by NoaHall on 2009-09-12
Yes. Although they'd have to know what they were doing(which is highly unlikely) and there aren't may guides out there which suggest to "delete and steal a users files, system, and important data"

---

### Post by dink123 on 2009-09-12
> But there is no simple solution like win98 press F8 (or sth) to enter DOS at boot (as superduper user without password!!!!) and rm C:/windows/username.(sth) and reboot and done. :grin:

thank you; 
but is it the same with windowsXP as you said for win98?

---

### Post by NoaHall on 2009-09-12
I believe there is a way to get to the command line on Windows start up, yes.

---

### Post by mcduck on 2009-09-12
> **dink123 said:**
> Thank you..i tried it.
in this way anyone can enter in to the system and change the settings if the GRUB is not password protected. am i right?

Yes, physical access to a computer should always be considered as admin access.

Even if that method is disabled with a Grub password, one can always boot a machine with a live-CD and access all files that way, or remove hard drives and plug them into other machine to get the data. This works for all operating systems, and disabling the option is rather hard as long as the computer in question has a CD drive or USB ports (since BIOS passwords are useless so disabling boot from CD/USB won't help lot). Because of this you should always protect your machine from unwanted physical access, or if you can't, encrypt any sensitive data.

---

### Post by mcduck on 2009-09-12
> **Liolikas said:**
> Lets say you are in situation that you forgot your sudo password. Not everything is lost. You can boot from liveCD, access /etc/shadow file and enter encrypted new root password into it or try to decrypt existing password with various cryptography software. But you have to understand basics of modern cryptography and google basic information about shadow file.  
---
But there is no simple solution like win98 press F8 (or sth) to enter DOS at boot (as superduper user without password!!!!) and rm C:/windows/username.(sth) and reboot and done. :D

Since the sudo password is just a normal user password, it can be reset by logging into recovery mode, entering root shell, and running "passwd *username*".

No need to use a live CD or mess with the shadow file.

---

### Post by dink123 on 2009-09-12
> **mcduck said:**
> Since the sudo password is just a normal user password, it can be reset by logging into recovery mode, entering root shell, and running "passwd *username*".

No need to use a live CD or mess with the shadow file.

dear mcduck;
what is the difference between the above two approaches(i.e yours and the editing of the '/etc/gdm/gdm.conf' file)?
because for me if i want to get computer to my hand entering as the single user mode from the GRUB options is the easiest.

---

### Post by NoaHall on 2009-09-12
Editing the file - lets you LOG ON on normal ubuntu as root. (which is what you would do if you just wanted root, and not to cause major damage)

Single user mode/drop to root shell - Makes you root. Only able to access root from there only.

---

### Post by mcduck on 2009-09-12
> **dink123 said:**
> dear mcduck;
what is the difference between the above two approaches(i.e yours and the editing of the '/etc/gdm/gdm.conf' file)?
because for me if i want to get computer to my hand entering as the single user mode from the GRUB options is the easiest.

My way signs you in as root in a terminal session.

The GDM way allows logging into graphical desktop as root (if the root account is enabled). You still need to enable the root account. Also note that this only affects the graphical desktop, if root account is enabled it can be used in terminal without enabling graphical login for root. Logging into desktop as root is usually specifically disabled this way even in those Linux distributions that use root account.

Note that even the way I suggested is only really necessary for recovery purposes. In all normal use you can simply start root session in a terminal by running "sudo -i".

---

### Post by dink123 on 2009-09-13
> **mcduck said:**
> 

Or do you mean how to get the system to boot into root console from Grub? In that case just select the recovery mode from Grub menu, and when asked what you want to do select "drop to root shell prompt".

(note that if you are using Grub2 the recovery mode is listed as "single user mode").

sorry i came up with this later. 
when i first try this i could enter as the root. but i set up a root password and now when i try to enter to the single user mood it will ask for the root password. according to that if someone has assigned a root password isnt there a way to login as the root?

---

### Post by mcduck on 2009-09-13
> **dink123 said:**
> sorry i came up with this later. 
when i first try this i could enter as the root. but i set up a root password and now when i try to enter to the single user mood it will ask for the root password. according to that if someone has assigned a root password isnt there a way to login as the root?

If you have set a root password then you need that password for the recovery mode as well. So if you decide to enable the root account against Ubuntu's default policy, you'd better never forget that password..

The files can, of course, still be accessed with any Live-CD.

---

### Post by NoaHall on 2009-09-13
And you can still attack using chroot.

---

### Post by dink123 on 2009-09-13
> **NoaHall said:**
> And you can still attack using chroot.

can you please tell me how to do it

---

### Post by Comzee on 2009-09-13
truecrypt is a nice little tool that can thwart pretty much anybody trying to get into your system, data, or any form of HD access. Boot-loader included ;).


[http://blog.taragana.com/index.php/archive/how-to-hack-root-password-in-linux/](http://blog.taragana.com/index.php/archive/how-to-hack-root-password-in-linux/) 

P.S. As it's stated in the blog you can password protect grub, doesn't help on the live-CD workaround :'( .

---

### Post by NoaHall on 2009-09-13
> **dink123 said:**
> can you please tell me how to do it

From a live disk, first mount then -
```

chroot /media/disk/

```

---

### Post by dink123 on 2009-09-13
i found a way rather than the those two above.
at the grub press select the recovery mode then press e then select kernal press e then type ro init = /bin/bash press enter then  boot .
this brought me to the root@[none] notice there is none inside.
but inside that login i cant do anything, i cant create, rename or delete , i will show up a message "read only file system".
why is this? in order to get access to the read , write and delete what should i do? do i need to add something extra?

---

### Post by NoaHall on 2009-09-13
It's because you're loading into the shell itself, and not bonded with the file system. Try mounting the filesystem you're trying to access.

---

### Post by dink123 on 2009-09-13
but i have access to the all the folders. doesn't  that mean that l have mounted the file system?

---

### Post by NoaHall on 2009-09-13
Hm, oh I see, I mis-read what you wrote.

In that case, you're logging in to a account that doesn't technically exist.

---

### Post by dink123 on 2009-09-13
so what can i do?

---

### Post by savagenator on 2009-09-13
I am inserting cents:

If you do init = /bin/bash, you are just logging into the shell. You don't really have access to anything because the filesystem is read-only. The things is, i don't know if you have access to the mount command.

Here is the ideal situation (advanced): you login as root from somehwere, mount the filesystem, and then chroot into the system (type "man chroot" in a terminal to see what it does)

Ideal situation (simple): login in single user mode (init 1). It loads the kernel, mounts the file system, and you can log in as root. It doesn't load any of your services.

---

### Post by dink123 on 2009-09-13
> **savagenator said:**
> I am inserting cents:

If you do init = /bin/bash, you are just logging into the shell. You don't really have access to anything because the filesystem is read-only. The things is, i don't know if you have access to the mount command.



ya mount command works.

> Here is the ideal situation (advanced): you login as root from somehwere, mount the filesystem, and then chroot into the system (type "man chroot" in a terminal to see what it does)

Ideal situation (simple): login in single user mode (init 1). It loads the kernel, mounts the file system, and you can log in as root. It doesn't load any of your services.

i did a small test. that will print a message instead of the init(a small bash script). so insted of init i am getting the string i used in that script.
because of that i cannot do the above two methods you mentioned.

---

### Post by savagenator on 2009-09-13
> **dink123 said:**
> 

i did a small test. that will print a message instead of the init(a small bash script). so insted of init i am getting the string i used in that script.
because of that i cannot do the above two methods you mentioned.

Are you still using /bin/bash instead of the kernel? If you don't load the kernel, you are not actually using linux you know...

Also, looking back at earlier posts, in the line "ro init = /bin/bash", "ro" stands for "read only". You can try to change it to "rw" to possibly get a read-write file-system. 

But! When you are in bash under read-write mode, you can run the bootup process manually to where you want it (you may want to run /etc/rc.sysinit if it exists in ubuntu, i am not sure) At least check [debian based system's boot]("http://www.debianhelp.co.uk/boot.htm") and [Arch linux's boot]("http://wiki.archlinux.org/index.php/The_Arch_boot_process") which may have some relevant information in the beginning (but arch linux is a little different than ubuntu, some files don't exist, other do.)

---

### Post by dink123 on 2009-09-13
thank you so much. it works when changed to "rw".
if you have time please refer 
[http://ubuntuforums.org/showthread.php?p=7942903#post7942903/](http://ubuntuforums.org/showthread.php?p=7942903#post7942903/) that is how i faced this problem.
i am glad to have your ideas about that thread.
thanks

---

### Post by cariboo on 2009-09-13
This looks like a homework thread, according to the code of conduct:

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

### Post by savagenator on 2009-09-13
> **cariboo907 said:**
> This looks like a homework thread, according to the code of conduct:

Responding to that, I'm going to change my extra long post to a much shorter one.

After almost an hour of research, the best way to do your "assignment" is to understand how the ubuntu system boots (using system V instead of inittab. Refer to man init.) What i did is booted into single user mode and edited two files. 3 lines in one in /etc/event.d/ and I added 2 lines in /root/.bashrc

I think thats is a pretty good hint :)

---

