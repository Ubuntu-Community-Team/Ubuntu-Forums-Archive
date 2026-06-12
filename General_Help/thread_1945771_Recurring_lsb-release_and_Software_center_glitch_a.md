---
title: "Recurring lsb-release and Software center glitch after installing MATE in 11.10"
date: 2012-03-23
forum: General Help
---

### Post by infomorph on 2012-03-23
I'm having an issue where the text of /etc/lsb-release and /etc/issue get altered to Linux Mint specs every time I reboot, which breaks the Software Center.

Background: I just recently upgraded to Ubuntu 11.10. Not a fan of Unity, so I  decided to try out the MATE desktop from Linux Mint. I added the Mint  repository, grabbed and installed the MATE packages, and got rid of the  repo so I wouldn't be downloading any other Mint packages. I did have  some glitches with the packages (missing dependency stuff), but I fixed  it.  

As other users have reported, installing MATE temporarily breaks the  Ubuntu Software Center because /etc/lsb-release and /etc/issue show the machine as Linux  Mint rather than Ubuntu. This is how they read:

~$ cat /etc/lsb-release
 DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=12
DISTRIB_CODENAME=lisa
DISTRIB_DESCRIPTION="Linux Mint 12 Fluxbox"

 ~$ cat /etc/issue
 Linux Mint 12 Fluxbox \n \l

  I can fix it as noted in [this answer]("http://askubuntu.com/a/84076") by editing /etc/*release and /etc/*issue back to:

~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"


~$ cat /etc/issue
  Ubuntu 11.10 \n \l

Problem is, this only works until I reboot the machine. Every time I  reboot, /etc/lsb-release and /etc/issue revert to Linux Mint. This breaks the  Software Center again (it simply won't run) until I edit those files again. It also looks like it might be breaking the automatic update check.

FWIW, I'm not even using the MATE desktop, since it turned out to be too glitchy and didn't play well with some of my apps. Hopefully it will get better. I'm using Gnome Classic in the meantime, but still having this issue (can't really uninstall MATE without a fresh install it seems).

Can anyone help me pin down what keeps changing these files on reboot? Much appreciated, thanks.

---

