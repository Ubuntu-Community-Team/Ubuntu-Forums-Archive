---
title: "No init found. Try passing init= bootarg"
date: 2010-10-12
forum: General Help
---

### Post by PJay3 on 2010-10-12
Hi
First post :) 
Ive been using ubuntu for about 6 months now. Im currently running 10.04 desktop on a ext4 partition but today I am unable to boot, im getting this error -

mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory 
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg  

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
Enter 'help' for a list of built-in commands  


Ive booted from the live cd and tryed to check the filesystem in gparted but i am getting this error -

e2fsck: Device or resource busy while trying to open /dev/sda1

I am also unable to mount the filesystem as to copy the contents from the home folder which is really the only thing im interested in.
I do hope someone can help me as im pulling my hair out here ;)

PJay

---

### Post by PJay3 on 2010-10-13
Anyone? I just really need to mount the filesystem really but it says device is busy. Ive run out of ideas now

PJay

---

### Post by spikoley on 2010-10-13
It sounds like there might be something wrong with your hard drive.  Boot into the live CD and try repairing it with the following command.

```
sudo fsck /dev/sda1
```

The sda1 might be something else.  If you do not know the name of your drive then run *gparted*.  It should list the name of the drive.  Just replace the sda1 with the name of your drive.

I am not sure if this will work, but its a worth a shot.

---

### Post by PJay3 on 2010-10-13
> **spikoley said:**
> It sounds like there might be something wrong with your hard drive.  Boot into the live CD and try repairing it with the following command.

```
sudo fsck /dev/sda1
```The sda1 might be something else.  If you do not know the name of your drive then run *gparted*.  It should list the name of the drive.  Just replace the sda1 with the name of your drive.

I am not sure if this will work, but its a worth a shot.


Thankyou. Worked like a charm :)

---

### Post by mm.ie on 2010-10-21
:)By God or any other metric, you are a saviour of my newbie soul.  Worked for me too!

---

### Post by spikoley on 2010-10-21
I am glad it worked for both of you.  BTW, I am [Agnostic]("http://en.wikipedia.org/wiki/Agnosticism")!

---

### Post by eskalaiyarasan on 2010-10-22
I'm using ubuntu10.04.its works fine but now it shows same error(boot arg not found)
sudo command doesn't work
help me to recover my data
when in trying to boot from live cd it doesn't boot
shows error

---

### Post by spikoley on 2010-10-22
> **eskalaiyarasan said:**
> I'm using ubuntu10.04.its works fine but now it shows same error(boot arg not found)
sudo command doesn't work
help me to recover my data
when in trying to boot from live cd it doesn't boot
shows error



It sounds like you have a different issue since you cannot boot into the live CD.  I recommend starting a new thread.  Once you are able to boot into the live CD then this command might fix your other issue.

---

### Post by Edgeraven on 2010-11-22
I tried using sudo fsck /dev/sda1 and I get an error it says device or resource busy while trying to open /dev/sda1 filesystem mounted or opened exclusivly by another pprogram...I am running live cd because ubuntu 10.10 will not boot and I get the no init found error...please help...I don't want to have to do a clean install...it was working just fine last night then I woke up today and this...thank you in advance...

---

### Post by spikoley on 2010-11-22
The partition cannot be mounted when running the command.  Use Gparted to unmount it from the live CD.  Look in the Gparted menu for the option to unmount it.  Make sure you are working with the right partition.  In the upper right hand corner you can select the partition.

```
gksudo gparted
```

Then run the command.

---

### Post by Edgeraven on 2010-11-22
> **spikoley said:**
> The partition cannot be mounted when running the command.  Use Gparted to unmount it from the live CD.  Look in the Gparted menu for the option to unmount it.  Make sure you are working with the right partition.  In the upper right hand corner you can select the partition.

```
gksudo gparted
```

Then run the command.

Hi...thank you for the reply...I ran gparted and for the partition it says it is unmounted? Do I need it to be mounted maybe? I am really not sure what happened...thank you in advance again...

---

### Post by Edgeraven on 2010-11-22
> **Edgeraven said:**
> Hi...thank you for the reply...I ran gparted and for the partition it says it is unmounted? Do I need it to be mounted maybe? I am really not sure what happened...thank you in advance again...

I also tried to run the check from there and I get an error...

---

### Post by spikoley on 2010-11-22
> **Edgeraven said:**
> Hi...thank you for the reply...I ran gparted and for the partition it says it is unmounted? Do I need it to be mounted maybe? I am really not sure what happened...thank you in advance again...

It needs to be unmounted.  Are you sure you have the right partition?  There might be something else going on.  Post the exact error message and start searching the net with it.

---

### Post by Edgeraven on 2010-11-22
> **spikoley said:**
> It needs to be unmounted.  Are you sure you have the right partition?  There might be something else going on.  Post the exact error message and start searching the net with it.

Hello...it just says an error occured when I try to run the fix. I also tried to fix grub boot but it says grub is not installed...so do I have to have grub installed in order for it to boot correctly? Like I said I woke up today and thee computer was like this...

---

### Post by spikoley on 2010-11-22
> **Edgeraven said:**
> Hello...it just says an error occured when I try to run the fix. I also tried to fix grub boot but it says grub is not installed...so do I have to have grub installed in order for it to boot correctly? Like I said I woke up today and thee computer was like this...

It sounds like this is an issue with grub.  I am not an expert with grub, but try running *sudo update-grub*.  If that doesn't work you might want to start a new thread and post the file /boot/grub/grub.cfg with a description of the the issue.

---

### Post by Edgeraven on 2010-11-22
> **spikoley said:**
> It sounds like this is an issue with grub.  I am not an expert with grub, but try running *sudo update-grub*.  If that doesn't work you might want to start a new thread and post the file /boot/grub/grub.cfg with a description of the the issue.

Ok thanks again for your help...I will keep you posted as to what happened...

---

### Post by nortexoid on 2010-12-04
> **spikoley said:**
> Boot into the live CD and try repairing it with the following command.

```
sudo fsck /dev/sda1
```


This worked for me. Thanks!

---

### Post by baluvix on 2010-12-07
> **PJay3 said:**
> Hi
First post :) 
Ive been using ubuntu for about 6 months now. Im currently running 10.04 desktop on a ext4 partition but today I am unable to boot, im getting this error -

mount: mounting /dev on /root/dev failed: No such file or directory 
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory 
Target filesystem doesn't have /sbin/init. 
No init found. Try passing init= bootarg  

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 
Enter 'help' for a list of built-in commands  


Ive booted from the live cd and tryed to check the filesystem in gparted but i am getting this error -

e2fsck: Device or resource busy while trying to open /dev/sda1

I am also unable to mount the filesystem as to copy the contents from the home folder which is really the only thing im interested in.
I do hope someone can help me as im pulling my hair out here ;)

PJay

Thanks a lot for this post. I got the same error and was thinking that re-install was the only option. I had PCLOS installed on another drive and running fsck /dev/sda8 from PCLOS fixed this (did not have to run LiveCD).  :)

---

### Post by zeezee22 on 2011-03-20
The plan worked for me too - thanx.   I've seen a few threads discussing this error msg - loox common.  I've only been installed a few weeks and am still at a loss over what I did to merit a response such as this. I'll be away for the week so I've written that command on paper to take with me - just in case!    Big ups, dude

---

### Post by umerlqt on 2012-05-21
I was a victim of "Target filesystem doesn't have /sbin/init". I tried using fsck, but it didn't work because of the following problem.*

fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

So here is the solution:
boot from live cd.

->remove the first inode.

> sudo debugfs -w /dev/sda1
debugfs 1.41.11 (14-Mar-2010)
debugfs: clri <8>
debugfs: quit

->Restart into live cd again. and do

> sudo fsck -yv /dev/sda1

It will work this time.*

Cheers
Umer

---

### Post by oldos2er on 2012-05-21
Old thread closed.

---

