---
title: "New Partitions - only read access ??"
date: 2011-10-11
forum: General Help
---

### Post by thyriel on 2011-10-11
Hi,

a problem i came across in Ubuntu 11.04 (also applies to xubuntu at least), that id like to get solved more user friendly then id currently do.

Im a lot partitioning, like new SD Cards for phones, external drives and so on.
The problem now is, after partitioning with gparted as ext[234] the new partition has rights like this for example:
drwxr-x**r-x**  3 root  root  4096 2011-10-11 20:15 test
As seen, owner is root (which is fine), but i have only read access and no write access to the partition.
Im still a newbie to Linux, so i have read alot about user rights and so on the wiki, id also tested this with a Ubuntu 11.04 live cd so i can be sure its not a problem with my local installation.

Making etc/fstab entries is no option, those partitions are used on a lot systems like media players, phones and so on, so id either need to have write access to new partitions.

Only solution i found so far is a creating a starter "sudo chmod o+rwx /media/*" and run that after partitioning.

But thats not a userfriendly solution for me, so the question is, how can i change the default rights for newly created ext[234] partitions ?

Also i have to say, this seems like a bug to me. It just makes no sense that a new partition is created without write access, id also tried a Linux Mint livecd and there for example its setting the user rights correctly so i can write to it after partitioning

---

### Post by TeoBigusGeekus on 2011-10-11
Try changing the ownership of the mount point
```
sudo chown -R yourusername /media/whatever
```

---

### Post by thyriel on 2011-10-11
sure that does work... but its not a userfriendly solution... In other Linux Distribution that does work "out of the box", only in Ubuntu/Xubuntu 11.04 its not working as it should... As as i said, id also tried it from liveCDs and its the same, but when i use for example Linux Mint LiveCD its working as it should...

I always thought linux is so customizeable, so i think there should be a permanent solution to that problem...

---

### Post by redmk2 on 2011-10-11
> **thyriel said:**
> sure that does work... but its not a userfriendly solution... In other Linux Distribution that does work "out of the box", only in Ubuntu/Xubuntu 11.04 its not working as it should... As as i said, id also tried it from liveCDs and its the same, but when i use for example Linux Mint LiveCD its working as it should...

I always thought linux is so customizeable, so i think there should be a permanent solution to that problem...

I'll bet your problem is due to the default *umask *setting  I set mint to 002, but I believe the Ubuntu default is 022.

Umask defines the ultimate file permissions used at creation time.  The Linux kernel values are 777 directories and 666 for files.  If you apply 022 to these values you get 755 for directories and  644 for directories, which is the default, while my setting get 775 and 664 respectively.  Just what you want.

Check the LinuxMint settings and see.  To do that use the CLI command ```
umask 
```

In some instances you might find a leading 0 which is normal (i.e. 0022 or 0002).

Edit:  Partitions don't have permissions at all.  File systems are where the permissions are provided for.

---

### Post by thyriel on 2011-10-12
Much Thanks redmk2 :)
That seems to be exactly what i was looking for...
A first quick test temporary setting it with umask did work in terminal with mkdir, default was indeed 0022... (strangely in Nautilus it created files still with the old settings, but id guess nautilus is just not reloading the new umask value)
i will look forward into the umask wiki entry and start editing the default values for my needs so its permanent then.

Will just take some time, as i really want to understand what im changing here so i dont muess up my system and can undo it just in case... Id let u know if i got it working then

---

### Post by redmk2 on 2011-10-12
> **thyriel said:**
> Much Thanks redmk2 :)
That seems to be exactly what i was looking for...
A first quick test temporary setting it with umask did work in terminal with mkdir, default was indeed 0022... (strangely in Nautilus it created files still with the old settings, but id guess nautilus is just not reloading the new umask value)
i will look forward into the umask wiki entry and start editing the default values for my needs so its permanent then.

Will just take some time, as i really want to understand what im changing here so i dont muess up my system and can undo it just in case... Id let u know if i got it working then

Umask is a environmental variable.  When you set it in a terminal it is only seen by that terminal session.  When you use Nautilus from the login session it has only the default umask setting.  Some applications also set a umask value for setting the permissions when creating files and directories.

Let me know what you find.  I can always just tell you how (and why) I set the umask value on my system.  ;-)

---

### Post by TeoBigusGeekus on 2011-10-12
+1 for umask. I've totally forgotten about it.

---

### Post by thyriel on 2011-10-12
ok, it works fine now after editing the umask value /etc/profiles only thing i dont get is the umask value for root user. It seems he has his own settings, but where is his profile stored ?

for example, if i create folders now it works fine, if i create a folder in terminal with sudo mkdir it still has only write access for root user

---

### Post by redmk2 on 2011-10-12
> **thyriel said:**
> ok, it works fine now after editing the umask value /etc/profiles only thing i dont get is the umask value for root user. It seems he has his own settings, but where is his profile stored ?

for example, if i create folders now it works fine, if i create a folder in terminal with sudo mkdir it still has only write access for root user

The problem is not the root user.  The problem is with sudo and the way it uses the environment.  When you use sudo with no switches you are not using the root environment.  If I remember correctly you actually execute commands with the calling sudoers envronment.

I fiddled with the command a bit. As a mortal user umask is 002.  As root (really root - not sudo root) the umask is 002.  As a sudo command the umask is, as you observed, 022!  Not good, but so trivial that I don't care.  The real question is how important is it to you to you.

---

### Post by thyriel on 2011-10-13
> **redmk2 said:**
> The problem is not the root user.  The problem is with sudo and the way it uses the environment.  When you use sudo with no switches you are not using the root environment.  If I remember correctly you actually execute commands with the calling sudoers envronment.

I fiddled with the command a bit. As a mortal user umask is 002.  As root (really root - not sudo root) the umask is 002.  As a sudo command the umask is, as you observed, 022!  Not good, but so trivial that I don't care.  The real question is how important is it to you to you.

Thats exactly what i thought how i workls... thanks for clarification :)

Another thing i found that could probably solve this, as i guess the problem is caused because gparted is started with sudo automatically:
[http://en.wikipedia.org/wiki/Setgid](http://en.wikipedia.org/wiki/Setgid)

could that work if i do that on /media ?

---

### Post by redmk2 on 2011-10-13
> **thyriel said:**
> Thats exactly what i thought how i workls... thanks for clarification :)

Another thing i found that could probably solve this, as i guess the problem is caused because gparted is started with sudo automatically:
[http://en.wikipedia.org/wiki/Setgid](http://en.wikipedia.org/wiki/Setgid)

You should never use sudo to run *gparted*.  As gparted is a GUI application.  You should use ***gksudo ***.  Could this be your problem?  Maybe, but I don't know that for sure.  I do know that gksudo handles things in a slightly different manner.> 



could that work if i do that on /media ?

I don't understand the question.

---

