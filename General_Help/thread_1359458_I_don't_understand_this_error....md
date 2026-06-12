---
title: "I don't understand this error..."
date: 2009-12-19
forum: General Help
---

### Post by Jotaro on 2009-12-19
When I start my computer, I always get this message:

One or more of the mount listed in /etc/fstab cannot yet be mounted:swap:waiting for UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1
Press ESC to enter recovery shell

I can press ESC to get on my computer, just that the screen is annoying. Does anyone know how to get rid of it?

---

### Post by Darael on 2009-12-19
Yes: you'll need to edit your /etc/fstab and move the line containing the word "swap" below the one with "UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1". That **ought** to do it.

---

### Post by Jotaro on 2009-12-19
> **Darael said:**
> Yes: you'll need to edit your /etc/fstab and move the line containing the word "swap" below the one with "UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1". That **ought** to do it.
I don't know where that is...

---

### Post by Leppie on 2009-12-19
the file is in /etc/ and is called fstab (so the complete path is /etc/fstab).
if you open this file with a text editor (from a terminal):
```
$gksudo gedit /etc/fstab
```
you should find the line indicated.

---

### Post by utnubuuser on 2009-12-19
If you can only get at a recovery shell, use nano instead of gedit. ie:> sudo nano /etc/fstab  use arrow keys for navigation, ctrl+x to save.

---

### Post by Jotaro on 2009-12-22
Ok, I still don't understand what I need to do...
Can someone give me a step by step walkthrough?
Sorry if I am being a little difficult...

---

### Post by wojox on 2009-12-22
Post the response to this back up here please:

```
sudo blkid
```

---

### Post by Dunatotatos on 2009-12-22
Hi

Here is the step by step :
Open a shell (Applications > Accessories > Shell)
Then type "sudo nano /etc/fstab"
Scroll with arrows keys until the line containing the word "swap".
Cut this line, then paste it just below the one with "UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1"
Press [Ctrl] X to quit, then O to save the file.

And it's OK...

---

### Post by avtolle on 2009-12-22
Take a look at [http://www.ubuntu.com/getubuntu/releasenotes/910#Login%20screen%20presented%20before%20optional%20filesystems%20are%20mounted](http://www.ubuntu.com/getubuntu/releasenotes/910#Login%20screen%20presented%20before%20optional%20filesystems%20are%20mounted)

---

### Post by Jotaro on 2009-12-22
> **Dunatotatos said:**
> Hi

Here is the step by step :
Open a shell (Applications > Accessories > Shell)
Then type "sudo nano /etc/fstab"
Scroll with arrows keys until the line containing the word "swap".
Cut this line, then paste it just below the one with "UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1"
Press [Ctrl] X to quit, then O to save the file.

And it's OK...
1. I don't have "shell", so I am assuming it is the terminal.
This is where I am now:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=71707c52-5c84-4b21-b902-05af0d02b337 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0






                               [ Read 13 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```
2. The commands there say:
"^K Cut Text" Does that means I type a "K" and press enter to cut the text?
Does that mean I need to type "^K" to cut the text?
Also, there is a number sign next to it. Do I type it next to the number sign or is it somewhere else?

---

### Post by wojox on 2009-12-22
Those directions are wrong. You need to run:

```
sudo blkid
```

To find the proper UUID of Swap.

Press Ctrl+x to get out of there for now.

---

### Post by Jotaro on 2009-12-22
> **wojox said:**
> Those directions are wrong. You need to run:

```
sudo blkid
```To find the proper UUID of Swap.

Press Ctrl+x to get out of there for now.
Ok, I did that, and now I am here:
```
jordanfaulkner@jordanfaulkner-desktop:~$ sudo blkid
/dev/sda1: UUID="71707c52-5c84-4b21-b902-05af0d02b337" TYPE="ext4" 
jordanfaulkner@jordanfaulkner-desktop:~$ 

```
What next?

---

### Post by wojox on 2009-12-22
So you don't want a Swap partition then. I see you removed it. Then just open /etc/fstab back up and remove the Swap line.

---

### Post by Jotaro on 2009-12-22
> **wojox said:**
> So you don't want a Swap partition then. I see you removed it. Then just open /etc/fstab back up and remove the Swap line.
Ok, I am back to here:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=71707c52-5c84-4b21-b902-05af0d02b337 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0






                               [ Read 13 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```
So, where it says "# swap was on /dev/sda5 during installation", I just remove that?

---

### Post by wojox on 2009-12-22
Remove all this:

```

# swap was on /dev/sda5 during installation
UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1 none            swap    sw           $


```

---

### Post by Jotaro on 2009-12-22
> **wojox said:**
> Remove all this:

```

# swap was on /dev/sda5 during installation
UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1 none            swap    sw           $


```
Ok, I highlighted it. What do I press to delete it?

---

### Post by wojox on 2009-12-22
Ctrl+k should do it.

---

### Post by Jotaro on 2009-12-22
> **wojox said:**
> Ctrl+k should do it.
Ok, I did that. It looks like this now:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=71707c52-5c84-4b21-b902-05af0d02b337 /               ext4    errors=remoun$
UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0







                               [ Read 13 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

```
So, how do I save and close out now, or did I do something wrong?

---

### Post by wojox on 2009-12-22
You still need to remove this line:

```
UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1 none            swap    sw           $

```

and Ctrl+x to save and exit.

---

### Post by Jotaro on 2009-12-22
> **wojox said:**
> You still need to remove this line:

```
UUID=20c20631-4060-4d94-876c-5edf2dd4bdc1 none            swap    sw           $

```and Ctrl+x to save and exit.
Ok, I did that. Then, I restarted my computer, and it told me the same error message. I still have to use a recovery shell. What should I do now?

---

### Post by susanw on 2009-12-23
I just had similiar problems making a swap partition and these links helped me lots:

[HTML]https://help.ubuntu.com/community/SwapFaq[/HTML]

[HTML]http://ubuntuforums.org/showthread.php?t=1362005&highlight=Swap+partition+UUID[/HTML]

susan

---

