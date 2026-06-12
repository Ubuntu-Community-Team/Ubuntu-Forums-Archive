---
title: "Need Help On Broken Packages"
date: 2011-09-30
forum: General Help
---

### Post by jeju20 on 2011-09-30
First of all I'm ubuntu newbie if you're going to help me, please show me what code to type, this is really hard battle for me to entering linux from windows.

I installed Ubuntu 11.04 on my machine.. Everything is working fine but this [problem]("http://ubuntuforums.org/showthread.php?t=1851892") (which haven't resolved).
Yesterday I click the update manager and installed new kernel 2.6.38-11-generic and other updates which i forgot because there are dozens of them then I turn off the computer.

Today I turn it on and found Ati Catalyst Control Center on my System --> Preferences but unable to load it said I have to install aticonfig. Then I go here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)  have ATi Radeon 2100 and download [this driver]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.2.3.2&lang=English") from official website after that using this command

> sudo sh ati-driver-installer-9-3-x86.x86_64 --buildpkg Ubuntu/maverickBut no maverick so I use Ubuntu/9.04 (packages created) then

> sudo dpkg -i *.debnone of them installed so i use synaptic to fix broken packages.

Then I try to open the ati catalyst > Error could not launch amdcccle (no such file or directory) Locate amdcccle

> locate amdcccle
/etc/alternatives/amdcccle
/etc/alternatives/amdcccle_desktop
/etc/alternatives/amdccclesu_desktop
/usr/bin/amdcccle
/usr/lib/fglrx/bin/amdcccle
/usr/share/applications/ubuntu-amdcccle.desktop
/usr/share/applications/ubuntu-amdccclesu.desktop
/usr/share/ati/amdcccle
/usr/share/ati/amdcccle/amdcccle_cs.qm
/usr/share/ati/amdcccle/amdcccle_da_DK.qm
/usr/share/ati/amdcccle/amdcccle_de.qm
/usr/share/ati/amdcccle/amdcccle_el_GR.qm
/usr/share/ati/amdcccle/amdcccle_es_ES.qm
/usr/share/ati/amdcccle/amdcccle_fi_FI.qm
/usr/share/ati/amdcccle/amdcccle_fr_FR.qm
/usr/share/ati/amdcccle/amdcccle_hu_HU.qm
/usr/share/ati/amdcccle/amdcccle_it_IT.qm
/usr/share/ati/amdcccle/amdcccle_ja.qm
/usr/share/ati/amdcccle/amdcccle_ko_KR.qm
/usr/share/ati/amdcccle/amdcccle_nl_NL.qm
/usr/share/ati/amdcccle/amdcccle_no.qm
/usr/share/ati/amdcccle/amdcccle_pl.qm
/usr/share/ati/amdcccle/amdcccle_pt_BR.qm
/usr/share/ati/amdcccle/amdcccle_ru_RU.qm
/usr/share/ati/amdcccle/amdcccle_sv_SE.qm
/usr/share/ati/amdcccle/amdcccle_th.qm
/usr/share/ati/amdcccle/amdcccle_tr_TR.qm
/usr/share/ati/amdcccle/amdcccle_zh_CN.qm
/usr/share/ati/amdcccle/amdcccle_zh_TW.qm
/usr/share/doc/fglrx-amdcccle
/usr/share/doc/fglrx-amdcccle/changelog.Debian.gz
/usr/share/doc/fglrx-amdcccle/copyright
/usr/share/fglrx/amdcccle.desktop
/usr/share/fglrx/amdccclesu.desktop
/usr/share/lintian/overrides/fglrx-amdcccle
/var/cache/apt/archives/fglrx-amdcccle_2%3a8.840-0ubuntu4_i386.deb
/var/lib/dpkg/info/fglrx-amdcccle.list
/var/lib/dpkg/info/fglrx-amdcccle.md5sumsI can't install my driver but instead i'm broking something..
Anyone knows how to resolve this?

Thanks

---

### Post by hhh on 2011-09-30
I don't think you broke anything, just the driver didn't install. To be sure, run...```
sudo apt-get -f install
``` It should report back 0 upgraded, 0 installed, 0 removed, 0 not upgraded.

---

### Post by jeju20 on 2011-09-30
> **hhh said:**
> I don't think you broke anything, just the driver didn't install. To be sure, run...```
sudo apt-get -f install
``` It should report back 0 upgraded, 0 installed, 0 removed, 0 not upgraded.

Yes it report back like that but still my ati broken. Same error

btw i forgot to mention that I have 1 broken package but unable to repair

status : broken
xvba-va-driver - XvBA-based backend for VA API (AMD fglrx implementation)

---

