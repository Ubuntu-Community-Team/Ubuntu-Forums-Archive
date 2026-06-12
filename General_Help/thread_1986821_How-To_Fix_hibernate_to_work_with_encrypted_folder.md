---
title: "How-To: Fix hibernate to work with encrypted folders and swap"
date: 2012-05-25
forum: General Help
---

### Post by Paddy Landau on 2012-05-25
[SIZE=4][COLOR=Red]IMPORTANT[/COLOR][/SIZE]

**This thread has been moved to the [Community Wiki]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap"). I shall no longer update this thread (although you are welcome to post queries here); I shall update the Wiki instead.**

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?p=12062069#post12062069](http://ubuntuforums.org/showthread.php?p=12062069#post12062069)

Thread closed.

__________________________________________________

[SIZE=4][COLOR=Red]RAISON D'ÊTRE[/COLOR][/SIZE]

[LIST]
[*] Many people have asked how to get hibernation to work with encrypted folders. The problem is that the swap partition is also encrypted, but with a random key, so on restarting there is no way to resume.
[/LIST]

[LIST]
[*] Now sharney, who uses Linux Mint, has found [a way to solve this problem]("http://forums.linuxmint.com/viewtopic.php?f=42&t=18743&p=190446#p190446") (on Mint, of course). The idea is to replace the random key with a password of your choice (you could use the same password as your login, but see [COLOR=Red]Disclaimers & Warnings[/COLOR] below, point 6).
[/LIST]

[LIST]
[*] I thought I'd see whether or not I could get this working on Ubuntu, which is a little different from both Mint (despite Mint's origins in Ubuntu) and sharney, who uses full-disk encryption.  I succeeded! Hence, this how-to.
[/LIST]

[LIST]
[*]Of course, as new information comes to light or as errors are discovered, I shall update this first post.
[/LIST]
     __________________________________________________

[SIZE=4][COLOR=Red]DISCLAIMERS & WARNINGS[/COLOR][/SIZE]

[LIST=1]
[*]I presume that you know how to use the Terminal. (This how-to quite advanced — well, for me it is — so if you don't know how to use the Terminal, this how-to is not for you.)
[*]I tested this both on a virtual machine using Virtual Box and on a native installation. The **Virtual Box** had a strange problem — when resuming, the screen remained black, although the applications were still open. But the **native installation** worked correctly.
[*]I tested this on **Ubuntu Precise 12.04** (fully updated), so I don't know whether or not it will work on other versions.
[*]Canonical does not support this function (yet), so **use it at your own risk**. I disclaim responsibility, because I'm not terribly technical and I discovered the method through reading and trial-and-error, not by any cleverness.
[*]Please follow the instructions carefully, otherwise you may find your system unable to boot (but you can recover with the Recovery Option or a Live CD).
[*]If more than one person uses your machine, **every user will need to know the encryption password for the swap**.
[/LIST]
__________________________________________________

[SIZE=4][COLOR=Red]EXPLANATION[/COLOR][/SIZE]

[LIST]
[*]Your existing encrypted swap partition uses a random key, generated each time you boot.
[/LIST]

[LIST]
[*]You will be replacing that random key method with a fixed key using a password of your choice.
[/LIST]

[LIST]
[*]It is possible to replace the password with a file, meaning that you wouldn't have to remember an extra password — but that file would be visible to anyone with physical access to your computer (e.g. via a Live USB).
[/LIST]

[LIST]
[*]If you forget your password, you will still be able to boot (after trying three times), but you won't have a swap partition. However, you can repeat this How-To to set it up again, so it's not a big deal.
[/LIST]

[LIST]
[*]Wherever there is coding in this How-To, I shall use [FONT=Lucida Console][COLOR=Blue]blue[/COLOR][/FONT] for anything *you* need to type, with *[FONT=Lucida Console][COLOR=Blue]italics[/COLOR][/FONT]* where you need to adjust something.
[/LIST]
 __________________________________________________

[SIZE=4][COLOR=Red]PREPARATION[/COLOR][/SIZE]

[LIST=1]
[*]Your computer must already be set up for encryption. If not, please [set up encryption]("http://ubuntuforums.org/showthread.php?t=1987630") and come back here.
[*]Think of a password (or passphrase) for your swap partition. You *can* use the same as your log-in — but don't do that if other people have accounts on your computer! (See [COLOR=Red]Disclaimers & Warnings[/COLOR] point 6.)
[*]Find out which is your encrypted swap partition.```
[COLOR=Blue]swapon --summary[/COLOR]
Filename                        Type            Size    Used    Priority
/dev/mapper/cryptswap1          partition       1998844 0       -1
```If you don't see output like mine (the numbers may differ), you don't have encryption.```
[COLOR=Blue]sudo cryptsetup status cryptswap1[/COLOR]
/dev/mapper/cryptswap1 is active and is in use.
  type:    PLAIN
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
[COLOR=Red]  device:  **/dev/sda1**[/COLOR]
  offset:  0 sectors
  size:    3997696 sectors
  mode:    read/write

```Make a note of the **device**. Mine says [FONT=Lucida Console]/dev/sda1[/FONT] — but yours could say something else, e.g. [FONT=Lucida Console]/dev/sdb3[/FONT].
[*]**Back up.**
[/LIST]
 __________________________________________________

[SIZE=4][COLOR=Red]HOW TO SET UP HIBERNATION[/COLOR][/SIZE]

[LIST=1]
[*] Turn off swap.```
[COLOR=Blue]sudo swapoff /dev/mapper/cryptswap1[/COLOR]
```
[*]Undo the existing mapping.```
[COLOR=Blue]sudo cryptsetup luksClose /dev/mapper/cryptswap1[/COLOR]
```
[*]Set up swap again, but this time with your chosen passphrase. The command will prompt you, twice, for your passphrase.
**Replace [FONT=Lucida Console]/dev/sdXN[/FONT]** with the device from [COLOR=Red]Preparation[/COLOR] point 3.```
[COLOR=Blue]sudo cryptsetup luksFormat --cipher aes-cbc-essiv:sha256 --verify-passphrase --key-size 256 */dev/sdXN*[/COLOR]
WARNING!
========
This will overwrite data on /dev/sda1 irrevocably.

Are you sure? (Type uppercase yes): [COLOR=Blue]**YES**[/COLOR]
Enter LUKS passphrase: *[COLOR=Blue][type your passphrase][/COLOR]*
Verify passphrase: *[COLOR=Blue][type your passphrase][/COLOR]*
```
[*]Re-map the swap.
**Replace [FONT=Lucida Console]/dev/sdXN[/FONT]** with the device from [COLOR=Red]Preparation[/COLOR] point 3.```
[COLOR=Blue]sudo cryptsetup luksOpen */dev/sdXN* cryptswap1[/COLOR]
Enter passphrase for /dev/sda1: *[COLOR=Blue][type your passphrase][/COLOR]*
```
[*]Set up the partition as swap.```
[COLOR=Blue]sudo mkswap /dev/mapper/cryptswap1[/COLOR]
```
[*]Turn on the swap (so you have swap again).```
[COLOR=Blue]sudo swapon --all[/COLOR]
```
[*]Check that it is working. You should see output similar to mine (the numbers may differ).```
[COLOR=Blue]swapon --summary[/COLOR]
Filename                        Type            Size    Used    Priority
/dev/mapper/cryptswap1          partition       1996796 0       -1
```
[*]Edit (using [FONT=Lucida Console][COLOR=Blue]gksudo gedit[/COLOR][/FONT] or your favourite editor) the file [FONT=Lucida Console]/etc/crypttab[/FONT]. Comment out the existing line by adding [FONT=Lucida Console]#[/FONT] to the front (or just delete the line), and add the following line.
**Replace [FONT=Lucida Console]/dev/sdXN[/FONT]** with the device from [COLOR=Red]Preparation[/COLOR] point 3.```
[COLOR=Blue]cryptswap1   */dev/sdXN*   none   luks[/COLOR]
```
[*]Edit the file [FONT=Lucida Console]/usr/share/initramfs-tools/scripts/local-top/cryptroot[/FONT]. Search for the following line (should be line 288, but this could change over time):```
message "cryptsetup: unknown error setting up device mapping"
```Skip to the next blank line (should be 291, *before* [FONT=Lucida Console]FSTYPE=''[/FONT]), and insert the following line.
**Replace [FONT=Lucida Console]/dev/sdXN[/FONT]** with the device from [COLOR=Red]Preparation[/COLOR] point 3.```
[COLOR=Blue]/sbin/cryptsetup luksOpen */dev/sdXN* cryptswap1[/COLOR]
```
[*]Edit the file [FONT=Lucida Console]/etc/acpi/hibernate.sh[/FONT]. At the first blank line, insert the following line.```
[COLOR=Blue]DEVICE='/dev/mapper/cryptswap1'[/COLOR]
```
[*]Edit the file [FONT=Lucida Console]/etc/initramfs-tools/conf.d/resume[/FONT]. *Replace* the existing RESUME line with the following line.```
[COLOR=Blue]RESUME=/dev/mapper/cryptswap1[/COLOR]
```
[*]Register these changes.```
[COLOR=Blue]sudo update-initramfs -u -k all[/COLOR]
```
[*]Ubuntu disables the *Hibernate* option in the menu. Restore it as follows. Create (using [FONT=Lucida Console][COLOR=Blue]gksudo gedit[/COLOR][/FONT] or your favourite editor) the file:
[FONT=Lucida Console]/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla[/FONT]
Fill the file with the following text and save.```
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
```
[/LIST]
 __________________________________________________


[SIZE=4][COLOR=Red]USING YOUR NEW SWAP FOR THE FIRST TIME[/COLOR][/SIZE]

[LIST=1]
[*]Reboot your machine.
[*]You will receive a prompt for swap's encryption passphrase. Remember that your mouse does not work at this point. Type your passphrase and press Enter.
 __________________________________________________
The prompt for your passphrase.
[attach]218696[/attach]
 __________________________________________________
If you mistype a passphrase three times, the system will  boot anyway but without your swap enabled. Repeat the How-To if you have  forgotten your passphrase.
[attach]218697[/attach]
 __________________________________________________
After correctly typing your passphrase.
[attach]218698[/attach]
[/LIST]
 __________________________________________________


[SIZE=4][COLOR=Red]HOW TO HIBERNATE[/COLOR][/SIZE]

Either:

[LIST]
[*]Use *Hibernate* from the shut-down menu
[/LIST]
Or:
 
[LIST]
[*]Press Alt-F2 and type```
[COLOR=Blue]gksudo pm-hibernate[/COLOR]
```(If you do this from a terminal, you can use [FONT=Lucida Console]sudo[/FONT] instead of [FONT=Lucida Console]gksudo[/FONT])
[/LIST]
Once your machine has shut down, restart. Did your programs resume normally? If so, hibernate and resume work!

---

### Post by inneedofsomehelp on 2012-06-04
Hi,

I created a post [here]("http://ubuntuforums.org/showthread.php?t=1994938"), but was told to ask in this thread.. I wonder if you can give any advice..

To summarise so far, I tried to hibernate before finding this thread and so had encrypted swap with a random key. On trying to restart, it hung saying that it could not stat **/dev/dm-0**. I could only boot by modifying the boot command to add **noresume**.

I have since tried unencrypting swap, which has no effect. I have also followed the steps in the above tutorial. Then, I managed to restart without locking up (didn't try hibernate). I then tried to undo each step in the hope that it had cleared whatever flag thinks it still wants to resume from hibernation but I am now back to square one.

I do not want to be able to hibernate.. I just want the system to boot normally again!

I have also noticed that when I try **update-initramfs**, I get the following error:
```
cryptsetup: WARNING: failed to detect canonical device of /dev/dm-0
```
This looks to be related to the boot problem, so don't know if it helps to clarify at all?? This is with swap totally decrypted.

Thanks for any suggestions!!

---

### Post by Paddy Landau on 2012-06-04
> **inneedofsomehelp said:**
> To summarise so far, I tried to  hibernate before finding this thread and so had encrypted swap with a  random key...
There is a number of problems needing diagnosis, so I have [post=11998296]answered you in your original thread[/post].

---

### Post by inneedofsomehelp on 2012-06-05
Thanks :)

---

### Post by nothingspecial on 2012-06-29
This thread is closed.

The information is now held on the community wiki at [https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap](https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap)

Thank you for your thread and the work you have done in keeping it current and of use to the community.

A thread for discussion of the wiki can be found at [http://ubuntuforums.org/showthread.php?t=2012408](http://ubuntuforums.org/showthread.php?t=2012408)


Support threads regarding the wiki and it's content should be created in a suitable forum.

---

