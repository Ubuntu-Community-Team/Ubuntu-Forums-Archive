---
title: "Ubuntu 10.10 fails to boot; freezes up at text splash screen"
date: 2012-02-10
forum: General Help
---

### Post by LambdaCalculus379 on 2012-02-10
I'm working on a Dell Dimension 4500 with the following specs:

* P4 CPU, 2 GHz (?)
* 1GB RAM
* PS/2 mouse/keyboard
* nVidia-based graphics card (unknown chipset)

I have just upgraded the machine from Ubuntu 10.04 to 10.10, and had to install an nVidia driver to clear up graphics issues. Afterwards, I rebooted the machine and now it doesn't boot up. This is what appears on screen:

* Starting NTP server ntpd             [OK]
* PulseAudio configured for per-user sessions
saned-disabled; edit /etc/default/saned
* Enabling additional executable binary formats binfmt-support [OK]
* Checking battery state...             [OK]

After this, it just sits there. Switching to another terminal works, but the terminal switches right back to the splash screen within seconds, which doesn't give me very much time to do *anything*.

I could try booting a live CD to see if I can read the logs, but does anyone have a pointer as to where to look (besides the /var/log/boot and other syslogs)?

---

### Post by Vishnu V on 2012-02-10
Hi,
i dont know much about logs
but this [link]("http://askubuntu.com/questions/68220/system-wont-boot-with-nvidia-driver-enabled") may have a solution for your problem

---

