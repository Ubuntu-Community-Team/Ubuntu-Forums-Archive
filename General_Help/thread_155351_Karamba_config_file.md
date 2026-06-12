---
title: "Karamba config file"
date: 2006-04-04
forum: General Help
---

### Post by gregleimbeck on 2006-04-04
I am running Karamba, and have been able to get everything working in this theme except for the network load monitors.  I am trying to get it to monitor my wireless card (eth1) but the graphs stay idle, and I am not sure what part I need to edit.  I have the ip address part working.  Here is the part of the config file in question.

################################################################################
# Network
################################################################################
<group> x=10 y=275
text  x=70 y=2 value="IP:" color=185,36,36 fontsize=10 font="nimbus sans l"
text x=85 y=2 sensor=program program="/sbin/ip addr show eth1 | grep 'inet ' | cut -d t -f2 | cut -d / -f1 | cut -b 2-" color=0,0,0 fontsize=10 font="nimbus sans l"

################################################################################
# Sensor network upload
# range is up to 100 kb. change 'max' value if needed.
image x=10 y=20 path="img/netgrid-up.png"
graph x=10 y=19 w=200 h=28 color=185,36,36 sensor=network format="%in" interval=1000 max=1000
text  x=40 y=48 sensor=network color=0,0,0 format="%in Kb"  fontsize=10 font="nimbus sans l" decimals=1
text  x=100 y=48 value="(incoming)" color=0,0,0 fontsize=10 font="nimbus sans l" DECIMALS=1

################################################################################
# Sensor network upload
# range is up to 16 kb. change 'max' value if needed.
image x=10 y=65 path="img/netgrid-down.png"
graph x=10 y=64 w=200 h=28 color=185,36,36 sensor=network format="%out" interval=1000 max=1000
text  x=40 y=93 sensor=NETWORK color=0,0,0 format="%out kb" fontsize=10 font="nimbus sans l" DECIMALS=1
text  x=100 y=93 value="(outgoing)" color=0,0,0 fontsize=10 font="nimbus sans l" DECIMALS=1

text  x=20 y=110 value="Total: IN" color=0,0,0 fontsize=10 font="nimbus sans l"
text x=110 y=110 sensor=program program="/sbin/ifconfig eth1 | grep 'RX byte' | awk '{print $3 $4}'" color=0,0,0 align=right fontsize=10 font="nimbus sans l"
text  x=120 y=110 value="OUT" color=0,0,0 fontsize=10 font="nimbus sans l"
text x=190 y=110 sensor=program program="/sbin/ifconfig eth1 | grep 'RX byte' | awk '{print $7 $8}'" color=0,0,0 align=right fontsize=10 font="nimbus sans l"

image x=160 y=105 PATH="img/icons/network.png"
text x=15 y=130 value="Network Load" color=0,0,0 fontsize=16 font="neuropol"
</group>


################################################################################
image x=25 y=430 path="img/line.png"
################################################################################



Any help is greatly appreciated!

---

### Post by gregleimbeck on 2006-04-05
Any idea where I could post this to get some help?  I have no idea what to do here.

---

