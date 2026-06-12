---
title: "/# mv * /var/lib/tftboot"
date: 2011-05-25
forum: General Help
---

### Post by pieterverberne on 2011-05-25
Hello,

yesterday I accidentally did the following:

current working directory was /    (I thought it was /tftpboot/ )
I typed:
`sudo mv * /var/lib/tftpboot/`  [enter]

It gave me some error about directories that could not be moved. Than I realized something. *ooops*

`$ ls`    gave me nothing at all.

I prepared a new USB stick with Ubuntu for a fresh installation only to find out the system does still boot and any file is in place. (I didn't even try to reboot in the first place.) 

How is this possible? I read that `rm -rf /` is not working. Is mv made fool proof in some way?

Kind Regards, 
 Pieter Verberne

---

### Post by yetiman64 on 2011-05-25
> **pieterverberne said:**
> Hello,

yesterday I accidentally did the following:

current working directory was /    (I thought it was /tftpboot/ )
I typed:
`sudo mv * /var/lib/tftpboot/`  [enter]

**It gave me some error about directories that could not be moved.** Than I realized something. *ooops*

`$ ls`    gave me nothing at all.

I prepared a new USB stick with Ubuntu for a fresh installation only to find out the system does still boot and any file is in place. (I didn't even try to reboot in the first place.) 

How is this possible? I read that `rm -rf /` is not working. Is mv made fool proof in some way?

Kind Regards, 
 Pieter Verberne

No mv is not foolproof, it can be a nasty if used wrong with root privileges. It is not as bad as rm though, if the changes are minimal the recovery and repairs can sometimes be done from a live cd. Though it is not a particularly pleasant experience to have to do.

Sounds like you may have been lucky with a bad command and nothing got moved as a result.

In that situation you were attempting to move everything in the root filesystem into a directory that actually exists on the root filesystem, an impossible situation. [B]

You were very lucky it failed[/B].

> `$ ls`    gave me nothing at all. If you included the $ symbol as well you would have got nothing out of the ls command, without it the command would have listed the contents. 
The $ symbol in the terminal indicates you are using your user account where a # symbol indicates you are operating as root user (dangerous). 

If copying and pasting commands into the terminal ensure you don't include either $ or #. **Edit:** the $ and # symbol are often included with instructions as a guide to the privileges required by the command after them.

If you aren't already aware, you can check how to use any command such as mv or rm etc with the code,

```
man <command>
``` replace <command> with the actual command you are about to use especially if you precede it with "sudo" (working as root can kill a system requiring a reinstall at times).

BTW, welcome to the forums,
Regards from yetiman64 :)

---

### Post by pieterverberne on 2011-05-25
When I entered the command, I saw all the Gnome (not using Unity) icons disappear. (Or became a red cross because the image was not found). I was not able to start any application. I went to console (alt+ctl+F1), entered my username but it never asked for my password.

So I thought the move actually did happen, until I rebooted my machine. I should retry it on a virtual machine to see what happens.

I know about $ and #. I typed 'ls' I'm using *NIX for years now. Never made this mistake before.

---

### Post by yetiman64 on 2011-05-25
Ok, I understand better now.

You actually have rebooted the same install and all is Ok, I'm :eek:.

I am astonished that everything is back in place. Hence my assumption nothing actually got moved. I'm very surprised hearing that icons disappeared/changed and are now OK.

Yes that would be a fascinating test in a VM. Please let us know the results and hopefully someone else can explain that better. I'm now baffled :).

---

### Post by pieterverberne on 2011-05-25
I cannot reproduce this in Virtualbox. Fresh Ubuntu install, did:

$ cd /
$ sudo mv * /var/lib
[sudo] password for pieter:
mv: cannot move `dev' to `/var/lib/dev': Device or resource busy.
[same error for 3 other folders]

$ ls /
 [no output, so empty]

shutdown doesn't work, so hard reset:

error: file not found.
grub rescue> _

That is the way it should behave ;-) I really don't know why it kept working om my laptop, but it did.

I do know; changes to the HDD are 'buffered' in internal memory for a moment before the actual change is done on the HDD. Maybe I was very lucky and the move change was still buffered and not written to the drive? Hmm, I can hardly imagine that happened.

O well.. ;-)

---

