---
title: "AMD APU and black screen of death on install and boot"
date: 2012-05-05
forum: General Help
---

### Post by rimtotem on 2012-05-05
I need help. Decided to install 12.04 (x64) on an AMD A8 3870K APU machine....but after I select install or boot from live CD it just goes to a black screen and disconnects from the monitor. 

As a workaround I used the alternative x64 cd and installed it via text installer...however I face the same problem after install, the system won't load up, it disconnects from the monitor (monitor goes into idle).

How can I install the proper drivers for the GPU? Getting tired of it...started thinking of going only with win 7 on the machine..

Nvm, gave up on it. Will just use win 7.

---

### Post by Zerqy on 2012-05-19
Hello! I had the same problem when installing 11.04 and 11.10. The problem is, the free open-source driver for ATI/AMD is outdated and does not work with AMD APU. You need to install proprietary "fglrx" driver (and, optionally, the Catalyst Control Center "fglrx-amdcccle"). The solution is here:
[http://askubuntu.com/questions/79416/black-screen-after-installing-ubuntu-11-10-amd-64-altenate-radeon-graphics-card](http://askubuntu.com/questions/79416/black-screen-after-installing-ubuntu-11-10-amd-64-altenate-radeon-graphics-card)
Omitting some unnecessary words and fixing mistakes, that's what you need to do (on installed system):

1. Hold Shift at boot time to enter Grub menu.

2. Enter Recovery Mode. There you should see a menu with several items. First, enable networking. Then enter root shell.

3. Edit /etc/apt/sources.list with a terminal-friendly editor like nano:
nano /etc/apt/sources.list

Uncomment the lines that add "partner" sources by removing the '#' in lines containing word "partner":
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

If there are no such lines, you may add them. This lines can be in another file - /etc/apt/sources.list.d/precise-partner.list (they are on my 12.04 upgraded from 11.10), so you may issue:
nano /etc/apt/sources.list.d/precise-partner.list

Use Ctrl-X to exit, then press Y to save.

4. Update your repositories:
apt-get update

Then install the 3rd Party ATI/Radeon driver:
apt-get install fglrx fglrx-amdcccle

5. Reboot:
shutdown -r now

That worked for me, hope for you too!

---

### Post by tanics on 2012-05-24
The solution posted here is about the problem after installation - but my problem is - _**how to install it when Kubuntu 12.04 LiveCD comes with a**_ **_Black Screen._**
My configuration: AMD A8-3870k processor, Corsair Vengeance RAM, ASUS Board.

I have tried booting Scientific Linux 6.1 LiveCD (sl6.1) and Ubuntu 9.04.LiveCD. Scientific Linux booted without problem but Ubuntu 9.04 booted into "intramfs" prompt.

Thanks in advance.

---

### Post by steeldriver on 2012-05-24
you can modify the installer's boot options to include 'nomodeset' on the command line, then the graphical install should run as normal (using a default driver - possibly the VESA driver? I didn't check)

at least that worked for me with 11.10 in a recent Mythbuntu install on an A8-3870 box

then reboot and install the proprietary drivers as described by Zerqy - or from the latest package downloaded directly from AMD/ATI

---

### Post by tanics on 2012-05-29
Just read it - where AMD admits their shortcomings with Linux support for APU-

[http://www.theinquirer.net/inquirer/news/2180336/amd-admits-improving-linux-opencl-support]("http://www.theinquirer.net/inquirer/news/2180336/amd-admits-improving-linux-opencl-support")

---

### Post by HanDez on 2012-07-09
See my post using this link:

[http://ubuntuforums.org/showthread.php?t=1968155&page=5](http://ubuntuforums.org/showthread.php?t=1968155&page=5)

If this works for you come back and quote and then "^ bump" this post please!

:popcorn:

---

