---
title: "Two little niggles. Please help"
date: 2009-12-19
forum: General Help
---

### Post by dirtylcd on 2009-12-19
Hi,

First time Ubuntu user. Used Linpus Lite so some experience with terminal.

Installed UNR. Ran the update and wifi started working. All good.

On startup, occasionally I will get a black screen with grey text showing something along the linesof 

'GNU GNUB'

Ubuntu, Linux 2.6.31.16

Ubuntu, Linux 2.6.31.16 (Recovery Mode)

Ubuntu, Linux 2.6.31.14

Ubuntu, Linux 2.6.31.14 (Recovery Mode)

Memory Test


This seems to have started appearing after running the update. How do I prevent this screen from appearing? Each time iot appears I just choose the first option.

Second niggle is that when the 'desktop' appears, it always asks for the admin password, so that the networking can allow the wifi to log in. I forget the exact message but it reads like that. Is it possible to make it stop asking for that password, or just skip it altogether?

Thanks!

---

### Post by Chronon on 2009-12-19
The first part is just the bootloader listing the possible boot choices.  It's normal and nothing to be worried about.  The top entry is the newest linux kernel.

I'm not sure about the network manager asking for the admin password each time.

---

### Post by rules on 2009-12-19
It's the keychain asking for a password. Keychain saves your wifi password/s, so you have to enter the keychain password for it to supply your wifi password. Suppose it's handy if you connect to multiple connections.

---

### Post by dirtylcd on 2009-12-19
Can I make the bootloader automatically load the first option? Why is the second option even there- that would usually indicate to me that the OS is installed twice (coming from WindowsLand) but thats obviously not the case here..

---

### Post by wojox on 2009-12-19
Those are different kernel upgrades. It's usually good to have two (one as a back up).

---

### Post by Chronon on 2009-12-19
> **dirtylcd said:**
> Can I make the bootloader automatically load the first option? 
You can set the timeout to be 1 second.  Apparently with Grub 2 there's a new file where you specify boot options.  Check this post: [http://ubuntuforums.org/showpost.php?p=7505203&postcount=1](http://ubuntuforums.org/showpost.php?p=7505203&postcount=1)

Pay attention to the /etc/default/grub part.

---

### Post by dirtylcd on 2009-12-19
> **Chronon said:**
> You can set the timeout to be 1 second.  Apparently with Grub 2 there's a new file where you specify boot options.  Check this post: [http://ubuntuforums.org/showpost.php?p=7505203&postcount=1](http://ubuntuforums.org/showpost.php?p=7505203&postcount=1)

Pay attention to the /etc/default/grub part.

This sound ideal, but it is a read only file that needs root priveleges. How do I edit it with those priveleges? I gather it is sudo something in terminal but every guide I comke across just assumes that you know how to do it =/

I tried sudo gedit etc/default/grub but it just opens up without displaying any text. Open this file through file manager (albeit without root permissions) it shows the test i want to edit.

---

### Post by Greenwidth on 2009-12-19
To edit:
sudo gedit /etc/default/grub

after edit & save, update:
sudo update-grub

---

### Post by dirtylcd on 2009-12-22
Ok, did that. Doesnt seem to have made a difference.

Why does it show that anyway? Is every Ubuntu user presented with that screen? Will every update add another item to the list?

---

### Post by Greenwidth on 2009-12-22
If you have a problem with a kernel upgrade you can revert to an older one or the recovery console.

Yes they are.

Each kernel upgrade will add an entry yes.
You can remove the old ones to make the list shorter: in Synaptic search for linux-image (be careful not to remove the latest one)
Then update grub as above.

You can make the countdown less by changing:
GRUB_TIMEOUT="(no of seconds)" to what you like.
Then update grub.

---

### Post by dirtylcd on 2009-12-22
I did that. It just waits until I press enter. Here is what my file looks like.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="1"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

I also ran the update command afterwards.

---

### Post by Greenwidth on 2009-12-22
Are you moving the selection with the cursor key? It stops the countdown.

---

### Post by dirtylcd on 2009-12-22
I just restarted to check, didnt press anything, yet it still sat there waiting for my input..

---

### Post by Greenwidth on 2009-12-22
That is strange.
My grub is exactly the same, apart from the timeout length.
Not sure what else it could be, sorry.

---

### Post by dirtylcd on 2009-12-22
Okay, many thanks for your time and patience =)

---

