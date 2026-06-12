---
title: "How to update nvida drivers185.18.36 to 190.42  on 9.04"
date: 2009-10-31
forum: General Help
---

### Post by lout on 2009-10-31
I have driver version 185.18.36 how to update to 190.42 thnx

---

### Post by cviorel on 2009-10-31
Here's a script wich will add the nvidia PPA, import the key and install the latest driver.

```

#!/bin/bash

## Nvidia Vdpau Team PPA
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767
sudo touch /etc/apt/sources.list.d/nvidia.list
echo '## Nvidia Vdpau Team PPA' | sudo tee -a /etc/apt/sources.list.d/nvidia.list
echo deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/nvidia.list
echo deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu `lsb_release -cs` main | sudo tee -a /etc/apt/sources.list.d/nvidia.list
sudo apt-get -q update
sudo aptitude -y install nvidia-190-modaliases nvidia-glx-190

```

---

### Post by lout on 2009-10-31
thnx

---

