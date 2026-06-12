---
title: "How do I force install vlc 1.1.x in Lucid?"
date: 2012-08-12
forum: General Help
---

### Post by Steve Francis on 2012-08-12
How do I get rid of vlc 1.06 in Ubuntu 10.04, and replace it with vlc 1.1.x, please?

I tried:
```
                                                               
sudo apt-get purge vlc
sudo add-apt-repository ppa:ferramroberto/linuxfreedomlucid
sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc

```but it just reinstalls version 1.06.

---

### Post by mc4man on 2012-08-12
If you wanted to purge vlc completely you'd be better off with 
sudo apt-get purge vlc-data, that will remove all the vlc packages - 6-7 usually
Why don't you either - 
open update-manager & see if there are several vlc package upgrades available
open up synaptic & do the same (preferred
run sudo apt-get upgrade (that ppa has a lot of packages so beware

---

### Post by Steve Francis on 2012-08-12
> **mc4man said:**
> If you wanted to purge vlc completely you'd be better off with 
sudo apt-get purge vlc-data, that will remove all the vlc packages - 6-7 usually
Why don't you either - 
open update-manager & see if there are several vlc package upgrades available
open up synaptic & do the same (preferred
run sudo apt-get upgrade (that ppa has a lot of packages so beware

Great, this worked for me. Thanks!

To install vlc 1.1.13 in Ubuntu 10.04, I did the following

Opened terminal and typed
```
sudo apt-get purge vlc-data
```as suggested by mc4man, followed by
```
sudo add-apt-repository ppa:lucid-bleed/ppa
```and then entered my sudo password and hit return.

I was informed that a public key for "Launchpad lucidbleed" had been imported.

Then I entered
```
sudo apt-get update
```which retrieved 7 packages.

Went to Ubuntu Software Centre 'Edit' menu and clicked on 'Software Sources...' In the dialogue box that opened, I clicked on the 'Other Software' tab and made sure that [http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu](http://ppa.launchpad.net/lucid-bleed/ppa/ubuntu) was checked.

I then shutdown and reopened the Ubuntu Software Centre. Now 'lucidbleed' showed under the Get Software tree.

I clicked on 'lucidbleed' which showed a lot of software modules available for installation. The only one I highlighted was 'multimedia player and streamer vlc'. I then clicked on the install box next to this module and the installation started.

Installation completed. I noted that some (but not all) other VLC plug-ins were also showing as installed.

Went to Sound & Video on the Applications menu and VLC was now present in the sub-menu. Started VLC and clicked on the 'About' tab to find version. It was version 1.1.13 The Luggage.

Haven't fully tested it yet and may have to download some more VLC plug-ins to make it fully operational. However, my initial problem has been solved.

Thanks, mc4man. :)

---

