---
title: "Keyboard/Mouse problem &amp; Mountall: Disconnected From Plymouth&quot; Error?"
date: 2010-12-27
forum: General Help
---

### Post by RallyDarkstrike on 2010-12-27
Hey folks, I had posted this in the Virtualization section of the forums, but as that was a day ago with no replies, and there is vital info on my Ubuntu system that I need back for a project, I'm am reposting here...mostly because I have figured out that the issue is les with my VM program and more with the OS itself, so my apologies in advance! If anybody can help me I would be extremely grateful, I've been looking around the net for a case with both these symptoms and found none (the cases I find are either one or the other, and nobody has been able to help me.)

I haven't used my VirtualBox install for about a month, but this morning  I started it up and updated to the latest Vbox release. After that I  booted my Ubuntu 10.10 VM to let it update and then reinstall the Guest  Additions so I can use Seamless mode as I always do after any Vbox  update....however, I went upstairs to do a bit of cleaning while Ubuntu  was updating, and when I came back down my Ubuntu VM seemed somewhat  frozen in a sense. To reiterate, this can't be my VM because the problem started when Ubuntu was updating itself.

The screensaver was on and working fine, however when I moved the mouse  for the login to come up to check on the status of my updates, all it  gave me was a black screen with a cursor. Since the HDD activity was nil  and it had been about 40 mins since I started the updates, I figured  the updates were done and simply tried restarting because I couldn't see anything and the computer seemed frozen, however, then, and every time since then I cannot get  the mouse or keyboard to work in my Ubuntu VM (they do work in my 2  Puppy Linux VMs so I know it's Ubuntu and not the VM program). Vbox says the VM is running, but I cannot click or  type at the login screen.

Basically I can start my Ubuntu VM and it will boot to the login, but  there I can't move the mouse, I can't type, etc...however, if I boot to the recovery console, the keyboard works there but all the console gives me is the usual startup jargon and then a "Mountall: Disconnected from Plymouth" error....from what I've read, the Plymouth error is bad, but I am holding out hope that somebody has some idea that would save me from a reinstall?

Thoughts, queries, theories? :sad: 

I'm running Vbox under Win7 Ult. 64-bit with a 2.4ghz Core 2 Duo, 2gb RAM, and a 1gb Radeon HD3850 vid card (but running Guest Addition Vbox drivers rather than ATi drivers in Ubuntu)

Thanks again if anybody can give me any assistance!

---

### Post by vandal47 on 2010-12-27
I'm having this problem with my Maverick/Vista dual-boot setup. It's the same story, but without the VM. I updated yesterday, got the black screen upon my return, and did a hard-reboot after all else failed. On normal login the keyboard does not work. In safe mode the keyboard works, but the boot process does not get past the mountall error.

---

### Post by RallyDarkstrike on 2010-12-27
Well, glad to see I am not the only one! I was wondering if I had a one in a million error :S

---

### Post by vandal47 on 2010-12-27
I figured out my problem. I rebooted during an update, which left some packages in a bad state. To fix this, I had to boot using a live CD, and continue the update from that environment.

From the live environment, I mounted my root partition and chroot'd that.
```

sudo mount /dev/sda1 /mnt
chroot /mnt

```

Then I
```
sudo apt-get install update
sudo apt-get install -f
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm

```

This took care of it. I'm not sure how you will do with with a VM, but it would start with mounting the virtual disk from your host (if that is even possible).

Good luck.

---

### Post by RallyDarkstrike on 2010-12-27
Thanks Vandal!

It should be possible, although I will have to dload the Live CD again...I appreciate your response though as it gives me something to go on!

Cheers, I'll reply later once I have a "Fixed" or "Not Fixed" answer to my issue.

Cheers!

[COLOR=Sienna]EDIT - I should say I should be fine with my VM; the keyboard and mouse should work fine if I boot from a live CD...here's hoping anyway, I'm torrenting the Ubuntu ISO now and I'll try it later on tonight.[/COLOR]

---

### Post by RallyDarkstrike on 2010-12-27
Ok, so, booted from Live CD and sitting in my Terminal atm...tried the commands you listed and...

"sudo apt-get install update" (without the quotes of course) won't do anything; giving me the "Unable to locate package update" error.

I tried "sudo apt-get update" though, and that seemed to list a number of packages, but seeing as I am a n00b at this, I am not sure if it installed them or not.

"sudo apt-get install -f" lists 0 packages as being installed or removed, and lists 213 as being not upgraded.

[COLOR=Sienna]EDIT - Ok, I'm also getting an error of "unable to resolve host ubuntu," which I know how to fix, but I can't get access to my hosts.conf file in my /mnt file to stop that error....? I just get some message about

"No protocol specified
(Gedit:4539) GTK-WARNING **: cannot open display 0.0"

when I try the command "gedit /mnt/etc/hosts" to fix the conf file?[/COLOR]

---

### Post by RallyDarkstrike on 2010-12-27
Ok, I went back to the start to begin from scratch...it appears when I try the "chroot /mnt" command, all I get is an error telling me that the operation isn't permitted :(
[COLOR=Sienna]
EDIT - Ok, stumbled my n00b way around that one, not signed in as the root user (whoops...:oops:)

Still getting the "Unable to resolve hostname Ubuntu" error on "sudo apt-get install update" though.[/COLOR]

---

### Post by RallyDarkstrike on 2010-12-27
Alright, problem solved and crisis averted, thanks to Vandal for his posts, and thanks to everybody for the views :)

---

