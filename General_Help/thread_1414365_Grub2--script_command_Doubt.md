---
title: "Grub2--script command Doubt"
date: 2010-02-23
forum: General Help
---

### Post by jsriz on 2010-02-23
Hi All,
I am on my way to coustomize grub2 n believe me i am trying very hard.....
I found out about writing our own scripts
like
--------------------------------------
cat<<EOF
menuentry "Reboot"
{
reboot
}
EOF
------------------------------------
I would like to know what is the similar command for shutdown
P.S. --Halt not working it jus hangs and does not shutdown:D:confused:

---

### Post by jsriz on 2010-02-24
bump

---

### Post by jsriz on 2010-02-26
bump

---

### Post by jsriz on 2010-03-04
shameless self bump

---

### Post by jsriz on 2010-03-05
the bump returns

---

### Post by jsriz on 2010-03-16
bumper bump

---

### Post by rnerwein on 2010-03-16
hi
the harder they come: [COLOR=Red]poweroff[/COLOR]
[COLOR=Black]
it' only a link to reboot but with the option " -f ". you shoudn't use it in that way ( or you like fscks )
ciao
[/COLOR]

---

### Post by jsriz on 2010-03-16
> **rnerwein said:**
> hi
the harder they come: [COLOR=Red]poweroff[/COLOR]
[COLOR=Black]
it' only a link to reboot but with the option " -f ". you shoudn't use it in that way ( or you like fscks )
ciao
[/COLOR]
nope poweroff didnt work it says no such command

---

### Post by oldfred on 2010-03-16
I tested all these entries on my system that I converted from grub legacy. The chainboot is to a grub legacy install in a partition PBR that is a grub legacy only partition. Reboot rebooted and halt totally shut down system.

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}
### END /etc/grub.d/40_custom ###

---

### Post by jsriz on 2010-03-16
> **oldfred said:**
> I tested all these entries on my system that I converted from grub legacy. The chainboot is to a grub legacy install in a partition PBR that is a grub legacy only partition. Reboot rebooted and halt totally shut down system.

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}
### END /etc/grub.d/40_custom ###
nope halt didnt power off the system it just............. halted it:P 
(I mean the system froze on the grub no error msg ,the up down keys didn't work had to press the power button.)

---

