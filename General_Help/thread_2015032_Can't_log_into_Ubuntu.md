---
title: "Can't log into Ubuntu"
date: 2012-07-02
forum: General Help
---

### Post by SuperFreak on 2012-07-02
I hope some kind soul will help me get my desktop back

I tried to start my computer with a USB hard drive(NTFS) already connected  and on(I was going to back up files). This led to a number of problems. 
First on booting the computer the screen showed this message " The disk drive for /media/Data Copy is not ready yet or not present" then offered option S to Skip, M manual recovery or wait. I tried skip and it gave me the grub menu which is odd as my computer boots through GPT. I rebooted same message again pressed S and I got login screen. However when I enter my password it starts booting and then just goes back to login screen. I am only able to gain access through the guest account. How do I regain access to my own account and get rid of the message on the boot up screen?

I am stuck in an endless login loop

not sure if this helps but here is Output of blkid

guest-b3yQML@david-desktop:~$ sudo blkid
sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [118, -1, -1]: Operation not permitted
guest-b3yQML@david-desktop:~$ blkid
/dev/sda1: LABEL="EFI" UUID="6EE3-8F18" TYPE="vfat" 
/dev/sda3: LABEL="ROOT" UUID="fb91ba53-76d5-41af-aa6f-24035b6de7a4" TYPE="ext4" 
/dev/sda4: LABEL="HOME" UUID="89427c18-2e81-494e-baef-933d3216d968" TYPE="ext4" 
/dev/sda5: UUID="f531caff-a236-4f4c-a401-3b7fbc067c30" TYPE="swap" 
/dev/sdb1: LABEL="STORAGE" UUID="b3aaffec-03c9-40dd-b836-35d9346019cb" TYPE="ext4" 
guest-b3yQML@david-desktop:~$

---

### Post by zombifier25 on 2012-07-02
Log in a tty (Press Ctrl+Alt+F1), then type this command:
```
sudo chown yourusername:yourusername ~/.Xauthority
```
Additional info: You can't sudo in guest because guests are not sudoers.

---

### Post by SuperFreak on 2012-07-02
Thanks for your reply.

I tried the command and I get this message:
Chown: cannot access `//.Xauthority no such file or directory

I did in fact type in ~/.Xauthority not `//.Xauthority

---

### Post by SuperFreak on 2012-07-03
I don't know if it is of any importance but when I hit CTL ALT F1 it gives me a welcome to Ubuntu message followed by "No Directory, Login with Home -/"

The problem I believe is related to the " The disk drive for /media/Data Copy is not ready yet or not present"  message which appears every time I boot the computer.

---

### Post by SuperFreak on 2012-07-03
I should also add that prior to these events login was automatic (I did not have to enter a password)

Development: I realized the External Drive Ubuntu is trying to find is one I had connected before the current one. I connected it and rebooted. The message "The disk drive for /media/Data Copy is not ready yet or not present" was skipped this time but I still can't login to my account just as guest. Looking in Nautilus I can see the drive listed under "Computer". I tried to eject is and get the message in the screenshot. I also tried the command  ```
umount /media/Data\ Copy
``` and get the same message.
Could resolving this issue solve my problem?

Beginning to see the light here. I think my fstab is messed up. Attached is a screenshot of FSTAB and I do not see /Home or / indicated but Data Copy is there. Can someone please help me get FSTAB the way it should be?

---

### Post by SuperFreak on 2012-07-03
I restored FSTAB to an earlier version and I am able to boot normally now. My only remaining question is why did backing up files onto an external USB drive alter my FSTAB file?

---

