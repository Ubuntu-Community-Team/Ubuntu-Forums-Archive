---
title: "help avast anitvirus not starting..."
date: 2010-03-30
forum: General Help
---

### Post by amit.neo2000 on 2010-03-30
help avast anti virus not starting...
hay everybody,
I recently installed avast anti virus in my UBUNTU 9.10 O.S. to check my various external hard discs for Viruses.

avast worked well for some days but now it's not starting up.

its giving the error: "_**An error occured in avast! engine: Invalid argument**_"

i tried to re install it by running the .DEB file.
but no success.
please help...
thanks...

---

### Post by Nisal on 2010-03-30
> **amit.neo2000 said:**
> help avast anti virus not starting...
hay everybody,
I recently installed avast anti virus in my UBUNTU 9.10 O.S. to check my various external hard discs for Viruses.

avast worked well for some days but now it's not starting up.

its giving the error: "_**An error occured in avast! engine: Invalid argument**_"

i tried to re install it by running the .DEB file.
but no success.
please help...
thanks...

remove it completely using "ubuntu software center" and try reinstalling

---

### Post by amit.neo2000 on 2010-03-30
i cant find the avast listed in the ubuntu software center!!!

---

### Post by Nisal on 2010-03-30
> **amit.neo2000 said:**
> i cant find the avast listed in the ubuntu software center!!!

in installed softwares ?

---

### Post by amit.neo2000 on 2010-03-30
yes...
its not even there also...

---

### Post by 2hot6ft2 on 2010-03-30
Mine shows up in Synaptic as avast4workstation so you may be able to purge it with
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get purge avast4workstation
```
You will have to enter your password which wont be displayed just type it in and hit Enter
Then re-install

---

### Post by amit.neo2000 on 2010-03-30
sory no luck still the same error...

---

### Post by 2hot6ft2 on 2010-03-30
Try installing it first then purge it. Or you may check the avast forum to see how many others have had your problem and found a solution.
[http://forum.avast.com/index.php?board=5.0](http://forum.avast.com/index.php?board=5.0)

---

### Post by 2hot6ft2 on 2010-03-30
Go to Places > Home Folder
Click on View and check the box by Show Hidden Files
Open the .avast folder
Right click on 400.vps and Move to Trash
Use the Up Arrow at the top of the Nautilus window.
Click on View and un-check the box you checked.
Try avast again.

You can always restore the file from the trash but that seems to be the issue.

EDIT: Looks like you have to do it as root so open nautilus like this
Open a terminal
Applications > Accessories > Terminal
and run
```
gksu nautilus
```
It should start in your Home Folder
Then do what I said above

> I was able to get by the error message when trying to update my AVAST engine on Ubuntu 9.10.

Make sure you are in your home directory by typing pwd. Next, type ls -a; which should show all hidden files/directories.
Then navigate to the avast directory (cd .avast), you will see the following file name 400.VPS. Remove this file. There seems to be a size limitation or something. You may have to do this with root or sudo.

After removing the 400.vps file from the hard drive, I was then able to launch the Avast Application and run an update.


And while that will work it doesn't solve the issue with the avast program since it's in the way the program is written and the kernel limitations.
[http://forum.avast.com/index.php?topic=57775.msg487331#msg487331](http://forum.avast.com/index.php?topic=57775.msg487331#msg487331)
> As was written earlier, this won't help. So again, once more:

- in some kernels, there's a 32MB limitation for SHM block size by default (which can be altered in runtime, using sysctl)
- in latest VPS, this limit was reached by one part of the 400.vps. so at least in the future, you MUST alter the nonsensually-small default

(removing 400.vps causes the engine to use the spared older one, which will "work", but obviously doesn't solve the real cause)


This below is from the one that wrote the avast program apparently
[http://forum.avast.com/index.php?topic=57775.msg486945#msg486945](http://forum.avast.com/index.php?topic=57775.msg486945#msg486945)
> Starting with the 400.vps, version 100328-1, one of it's internal block reached the inner limit 33554432 bytes. It's a kernel variable which
is (quite artificially) limiting the maximum size of any SHM memory block - and 33554432 was a default for some kernels.

Solution? Set the limit to higher values (as root):

sysctl -w kernel.shmmax=128000000
OR
echo 128000000 >/proc/sys/kernel/shmmax

Place those lines to /etc/init.d/rcS or equivalent file (it's distribution-specific a bit - see /etc/inittab, the sysinit runlevel) to have them set automatically (just after boot).

**[SIZE="4"][COLOR="DarkRed"]I don't know about how running that would affect ubuntu and I would suggest getting more responses before trying it[/COLOR][/SIZE]**, but what it says is to run
```
sudo sysctl -w kernel.shmmax=128000000
```
It appears to me to be changing the shared memory maximum allocation. My guess by looking at the command.

---

### Post by bradshawd on 2010-04-07
> **amit.neo2000 said:**
> help avast anti virus not starting...
hay everybody,
I recently installed avast anti virus in my UBUNTU 9.10 O.S. to check my various external hard discs for Viruses.

avast worked well for some days but now it's not starting up.

its giving the error: "_**An error occured in avast! engine: Invalid argument**_"

i tried to re install it by running the .DEB file.
but no success.
please help...
thanks...


Not sure but try this one  [http://ubuntuforums.org/showthread.php?t=1448803](http://ubuntuforums.org/showthread.php?t=1448803)

---

### Post by Ethan hunt on 2011-01-21
> **2hot6ft2 said:**
> Go to Places > Home Folder
Click on View and check the box by Show Hidden Files
Open the .avast folder
Right click on 400.vps and Move to Trash
Use the Up Arrow at the top of the Nautilus window.
Click on View and un-check the box you checked.
Try avast again.

You can always restore the file from the trash but that seems to be the issue.

EDIT: Looks like you have to do it as root so open nautilus like this
Open a terminal
Applications > Accessories > Terminal
and run
```
gksu nautilus
```
It should start in your Home Folder
Then do what I said above



And while that will work it doesn't solve the issue with the avast program since it's in the way the program is written and the kernel limitations.
[http://forum.avast.com/index.php?topic=57775.msg487331#msg487331](http://forum.avast.com/index.php?topic=57775.msg487331#msg487331)


This below is from the one that wrote the avast program apparently
[http://forum.avast.com/index.php?topic=57775.msg486945#msg486945](http://forum.avast.com/index.php?topic=57775.msg486945#msg486945)

**[SIZE="4"][COLOR="DarkRed"]I don't know about how running that would affect ubuntu and I would suggest getting more responses before trying it[/COLOR][/SIZE]**, but what it says is to run
```
sudo sysctl -w kernel.shmmax=128000000
```
It appears to me to be changing the shared memory maximum allocation. My guess by looking at the command.
I had the same problem and did what 2hot6ft2 said.

run in terminal "sudo sysctl -w kernel.shmmax=128000000"

it works!

Thanks to 2hot6ft2

---

### Post by PcMojo on 2012-02-29
I had the same problem using Ubuntu 10.10. Removing the 400.vps file didn't do much for me. As soon as I tried to update Avast, the error would return. I ran the command that Zilog from the Avast forum mentioned, and it worked.
 sudo sysctl -w kernel.shmmax=128000000 
I followed it up with: 
sysctl -p /etc/sysctl.conf 
to read/reload the values from sysctl.conf  Avast runs fine now, in fact it has already found 2 viri (plural for virus?). They weren't doing much...just hangin' around tryin' to find some M$ files to infect! :grin: Thanks for all the help everyone!

---

### Post by oldos2er on 2012-02-29
Closed, necromancy.

---

