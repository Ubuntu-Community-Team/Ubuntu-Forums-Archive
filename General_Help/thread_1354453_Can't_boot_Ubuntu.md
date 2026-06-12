---
title: "Can't boot Ubuntu"
date: 2009-12-13
forum: General Help
---

### Post by drewtam on 2009-12-13
My beautiful daughter decided to unplug the computer while it was being used. :frown: Now Ubuntu Karmic wont boot. :( :( It says something like "unable to mount filesystem" and kicks me to a shell-h? :cry:

I guess the HD is irreparably broken. Right not I am using the same computer, but booted with the XP's HD.

Assuming I am an absolute beginner with Linux, but otherwise technically savvy. Can anyone provide the best path to recover the office files and pictures stored on the Ubuntu HD?

I haven't attempted any recovery yet into the broken HD, since I'm afraid to cause more damage. Lets hear the expert opinions on how to make the best of a bad situation.

---

### Post by zbirdman777 on 2009-12-13
I'm no expert but you could try booting from the live cd and try to see if you can access your files that were saved in your ubuntu partition. If you can boot to your xp partition on the same HD I don't think its broken though.

Someone else can probably give some more insight though.

---

### Post by lmarmisa on 2009-12-13
I hope your HD will be sane. Simply, you will have to repair your system. You will need a Ubuntu Live CD for it.

Please, inform us about your Ubuntu version and if you know how the disk partions were defined.

Best regards,

Luis

---

### Post by drewtam on 2009-12-13
Sorry, if I wasn't clear. Ubuntu was on a dedicated HD, XP is on another dedicated HD.

I didn't really do anything custom with it. It was the recent upgrade to Karmic Koala.

---

### Post by lmarmisa on 2009-12-13
I would like to know if the shell screen that you comment ask for an user/passwd or for a shell command.

Check if one of theses two commands is accepted by this shell program:

```

fdisk -l
sudo fdisk -l

```

---

### Post by drewtam on 2009-12-14
Yes, it asks for the root password.

The fdisk brought up information about the HD, it described the size, number cylinders, blocks, etc. It also described at which blocks Linux started/ended, where "extended" started/ended, etc.


I don't remember seeing it the first times around, but this time it suggested I run fsck manually. Which I did after logging in. It ran through the checks. It didn't tell me what was wrong, but said the Kernel or Linux had changed and told me to reboot.

I rebooted and now it seems to be going ok. I already backed up my important files to a server. So my most worrying concerns are relieved.

Maybe the fsck fixed it?
I'll give it another day of booting a few times before marking this thread resolved.

---

### Post by lmarmisa on 2009-12-14
Yes. I agree. I think that the problem is solved.

---

