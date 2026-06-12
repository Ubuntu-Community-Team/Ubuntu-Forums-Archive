---
title: "Cannot boot up Ubuntu. &quot;boot from (hd0,0) ext...&quot;"
date: 2010-03-31
forum: General Help
---

### Post by mjmorris84 on 2010-03-31
I previously ran ubuntu on my system.  I just upgraded my MOBO, Video card, RAM and Hard drive. My MOBO is an ASUS P7P55-M.  Video card is a GeForce 9400 GT.  When I first booted up ubuntu ran just fine (minus driver installation issues).  When I attempted to reboot, it was unsuccessful, saying: 

"Boot from (hd0,0) ext fa93fc2c-yada yada...
starting up..."

It never starts up.  I read a little on a similar case and I unplugged my SATA connection to my HD and plugged it into a different SATA port, and it booted up.  Next time I attempted a reboot, it landed me where I am now, same message.


Keep in mind I am a very new linux user and I am not familiar where certain things are and how to run scripts, etc.  I am an intermediate windows user and I am still trying to transition to ubuntu.

Thanks very much in advance for any help!

---

### Post by drs305 on 2010-03-31
Are you getting a Grub menu at all before the boot fails? Do you get a grub prompt instead?

Here is a very simple way to boot if there are no outstanding issues. At the menu, press "c" to take you to the Grub2 command line. Then, if your install is still on sda1, try:

```
set root=(hd0,1)
linux /boot/vmlinuz root=/dev/sdxY ro
initrd /boot/initrd
boot
```

If that doesn't work, type "ls" to see what devices Grub2 finds. If you suspect it's not sda1 on which Ubuntu is found, try the new entry in the above commands. The first drive is 0, the first partition is 1.

You can also let G2 search for the kernel with:
```
search -f /vmlinuz
```

Here is a link to more information on booting from the Grub2 command line:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")

---

### Post by mjmorris84 on 2010-04-01
When i go to type in the command you shared, how do i return down to a new command line to continue typing without using the enter key and making a bad command? I'm not familiar at all with linux. I tried to type the whole command out without returning to a new line and that didn't work either.

---

### Post by drs305 on 2010-04-01
> **mjmorris84 said:**
> When i go to type in the command you shared, how do i return down to a new command line to continue typing without using the enter key and making a bad command? I'm not familiar at all with linux. I tried to type the whole command out without returning to a new line and that didn't work either.


Using ENTER is the way the commands must be executed, so if you are getting an error message it probably means that Grub2 doesn't even have enough basic information to function. 

I don't know which which commands are not working or what the error messages are, but you can try running the following commands before running those in the previous post to help Grub2 find some of the files it might need. You will need to substitute for (hd0,1) if your Ubuntu install and /root aren't on sda1.

```

set prefix=(hd0,1)/boot/grub
insmod (hd0,1)/boot/grub/normal.mod
insmod (hd0,1)/boot/grub/linux.mod

```

If the commands still don't work, the best course is to run meierfra's boot info script from the LiveCD and post the results between "code" tags (by pressing the # icon in the post's menu):
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

