---
title: "updating nvidia messed me up"
date: 2012-04-30
forum: General Help
---

### Post by gychang on 2012-04-30
latest 12.04 was working fine til 2d ago with nvidia driver update.  quick check on the net suggests latest driver update is the problem.

can someone let me know how to install older driver?, I am fairly new to terminal commands but willing ...

thanks,

---

### Post by HolyRoses on 2012-04-30
I did the following:

apt-add-repository 'deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main'

apt-get update

apt-get purge nvidia*
removed: nvidia-common* nvidia-current* nvidia-settings* ubuntu-desktop*

apt-cache showpkg nvidia-current
apt-cache showpkg nvidia-settings
apt-get install nvidia-current='295.33-0ubuntu1~precise~xup1' nvidia-settings='295.33-0ubuntu1~precise~xup1'

echo "nvidia-current hold" | sudo dpkg --set-selections
echo "nvidia-settings hold" | sudo dpkg --set-selections

It still prompts that there is an update available but it is blocked.

---

### Post by pqwoerituytrueiwoq on 2012-04-30
lock it in [synaptic](apt:synaptic) and it will stop bugging you

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
is easier than
apt-add-repository 'deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main'

---

### Post by gychang on 2012-04-30
> **HolyRoses said:**
> I did the following:

apt-add-repository 'deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main'

apt-get update

apt-get purge nvidia*
removed: nvidia-common* nvidia-current* nvidia-settings* ubuntu-desktop*

apt-cache showpkg nvidia-current
apt-cache showpkg nvidia-settings
apt-get install nvidia-current='295.33-0ubuntu1~precise~xup1' nvidia-settings='295.33-0ubuntu1~precise~xup1'

echo "nvidia-current hold" | sudo dpkg --set-selections
echo "nvidia-settings hold" | sudo dpkg --set-selections

It still prompts that there is an update available but it is blocked.

I will try this verbatum to see if it will work.  thanks for your input.

gychang

---

### Post by gychang on 2012-04-30
> **pqwoerituytrueiwoq said:**
> lock it in [synaptic](apt:synaptic) and it will stop bugging you

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
is easier than
apt-add-repository 'deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main'

not sure what locking it in mean...  the long line can be replaced with your sentence to accomplish the same?

gychang

---

### Post by HolyRoses on 2012-04-30
his short line is the same as my long line.  i just didn't know that notation at the time.

---

### Post by gychang on 2012-05-01
> **HolyRoses said:**
> I did the following:

apt-add-repository 'deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main'

apt-get update

apt-get purge nvidia*
removed: nvidia-common* nvidia-current* nvidia-settings* ubuntu-desktop*

apt-cache showpkg nvidia-current
apt-cache showpkg nvidia-settings
apt-get install nvidia-current='295.33-0ubuntu1~precise~xup1' nvidia-settings='295.33-0ubuntu1~precise~xup1'

echo "nvidia-current hold" | sudo dpkg --set-selections
echo "nvidia-settings hold" | sudo dpkg --set-selections

It still prompts that there is an update available but it is blocked.

I get an error message:
E: Version '295.33-0ubunt...~up1\ for \nvidia-current' not found
F:  unable to locate package nvidia-setting

gychang

---

### Post by bogan on 2012-05-01
Hi!, **gychang,**

You Posted > can someone let me know how to install older driver?, I am fairly new to terminal commands but willing ...There is a much easier way to get the older driver if you have version of the nvidia driver installed, and a working Internet link:

You have to run this from a tty text terminal, or shut down the Xserver from a GUI terminal ie```
 sudo service lightdm stop.
``` Login to the tty prompt and enter:```
 sudo nvidia-installer --latest
``` This will confirm the recommended version 295.33, but will not alter anything: it also confirms you have a working Web connection.

Then run: ```
sudo nvidia-installer -f 
 # follow the screen prompts using the arrow keys to select and press 'Enter'
``` This will un-install whatever version is installed, then install the 295.33 driver and renew the Xconf file. Then reboot.

Chao!, **bogan**.

---

### Post by bogan on 2012-05-03
Hi!, All,

There is a new nvidia driver version 295.49 available from nvidia downloads, I've tried it with  GeForce 7650 GTS &  GT 520 cards and it works. [COLOR=DarkOrchid]You can not install it with 'sudo nvidia-installer -f', as that still installs 295.33.[/COLOR] [See Edit below]

EDIT: Noon Friday May 4th; ```
nvidia-installer --latest 
``` now returns: v295.49 and     ```
nvidia-installer -f 
``` will install 295.49 after un-installing the previous version.

 NVNews says of version295.49:> **Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**
Chao!, bogan

---

### Post by pqwoerituytrueiwoq on 2012-05-03
> **gychang said:**
> not sure what locking it in mean...  the long line can be replaced with your sentence to accomplish the same?

gychang
use ctrl or shift to select multiple packages
by default [synaptic](apt:synaptic) is not installed in ubuntu (it is in xubuntu)

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html)

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

     ```
nvidia-installer --latest
``` now returns: v295.53 and the currently installed version, without altering anything.
     

     ```
nvidia-installer -f
``` will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

