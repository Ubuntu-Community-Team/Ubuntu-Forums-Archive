---
title: "icarus verilog installation problem."
date: 2012-07-24
forum: General Help
---

### Post by yaami on 2012-07-24
Hi all,

I've installed iverlog from the the repositories 

```
apt-get install iverilog
``````
iverilog -v
Icarus Verilog version 0.9.5  (v0_9_5)

``````
 vpp
No command 'vpp' found, did you mean:
``````
 Command 'pp' from package 'libpar-packer-perl' (universe)
 Command 'xpp' from package 'xpp' (universe)
 Command 'gpp' from package 'gpp' (universe)
 Command 'vps' from package 'util-vserver' (universe)
 Command 'vpe' from package 'texlive-latex-extra' (main)
 Command 'vp' from package 'atfs' (universe)
 Command 'vop' from package 'via-bin' (universe)
 Command 'wpp' from package 'wpp' (universe)
_** Command 'vvp' from package 'iverilog' (universe)**_   <== _**[COLOR=Red]already installed this pkg[/COLOR]**_
 Command 'tpp' from package 'tpp' (universe)
 Command 'cpp' from package 'cpp' (main)
vpp: command not found
``````
uname -a
Linux ubuntu 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

```pls let me know if I need to install any other pkg to get this working.

Thanks,
Yaami.

---

