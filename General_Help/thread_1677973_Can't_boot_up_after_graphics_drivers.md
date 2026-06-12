---
title: "Can't boot up after graphics drivers"
date: 2011-01-29
forum: General Help
---

### Post by TheShader on 2011-01-29
Hello a few weeks ago I made my Ubuntu-server(with GNOME desktop) unbootable after playing with the binary drivers for nvidia(my card is gtx 470). I was able to use it in the past with the proprietary drivers, but somehow I tweaked some settings, tried to install new drivers etc and actually I don't remember much of what I did because I had finals at school so my ubuntu install just remained unbootable like that. All I know is that I can't even boot in recovery mode (command line). I tried to boot with a live cd, chroot into the ubuntu partition and fix the graphics but it didn't work. Can someone help me please? I'm really confused and can't identify the problem :( :confused:

---

### Post by sikander3786 on 2011-01-29
From the command line, please try these commands one by one.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

Remember, all the commands are case sensitive e.g, capital X for X11 in 1st command.

---

### Post by TheShader on 2011-01-29
As I said before I can't boot even in the command line. Can I write those commands by booting a live cd and then chrooting into my ubuntu partition?

---

### Post by psycho5 on 2011-01-29
> **sikander3786 said:**
> From the command line, please try these commands one by one.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

Remember, all the commands are case sensitive e.g, capital X for X11 in 1st command.

Kya baat hai mere bhai, I was about to advise the same thing =)

---

### Post by sikander3786 on 2011-01-29
Sorry I missed that part of your first post.

Can you press and hold down Shift key from your Bios screen and see if Grub menu comes up? If yes, recovery mode is the second option there.

Chroot is another option but the last resort only.

---

### Post by TheShader on 2011-01-29
I select recovery mode in grub but it freezes after some point :D I told I can't boot in to command-line :(

---

### Post by sikander3786 on 2011-01-29
> **TheShader said:**
> I select recovery mode in grub but it freezes after some point :D I told I can't boot in to command-line :(
There should be some error messages. Can you please produce them here?

---

### Post by TheShader on 2011-01-30
> **sikander3786 said:**
> There should be some error messages. Can you please produce them here?

Sorry for the late reply, yes the error message is this(what I see on the screen after the boot messages):

```
fsck from util-linux-ng 2.17.2
/dev/sdb3: clean, 474992/10379264 files, 15588238/41504000 blocks
init: udevtrigger main process (551) terminated with status 1
init: udevtrigger post-stop process (561) terminated with status 1

```
I don't get it? :(

---

