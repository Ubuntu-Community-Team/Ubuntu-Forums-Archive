---
title: "RAM usage"
date: 2010-05-17
forum: General Help
---

### Post by l3ecl on 2010-05-17
why is my ram usage so high?

I only have chrome open with 1tab and 1 open terminal. is this normal? im running a 1.6ghz laptop with 512 MB of RAM.


```
gg@Ubuntu:/$ free
```            >  total       used       free     shared    buffers     cached
Mem:        501000     463664      37336          0      13332     259520
-/+ buffers/cache:     190812     310188
Swap:      1073144          0    1073144```
gg@Ubuntu:/$ free -m
```             > total       used       free     shared    buffers     cached
Mem:           489        449         39          0         13        250
-/+ buffers/cache:        186        302
Swap:         1047          0       1047

alt focus: what are the "essentials" in making ubuntu run, so i can get rid of everything else like bluetooth

---

### Post by Rhubarb on 2010-05-17
Essentially, a lot of your RAM is being used up by buffers and cache, which is really only temporarily used RAM - to speed up your computer for recently / commonly used processes.

I've done a quick internet search, and this article sums it up quite well:
[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

---

### Post by x-shaney-x on 2010-05-17
<EDITED>

oops

---

### Post by quiritius on 2010-05-17
"Control Center" - "Startup Applications" and turn off all items which you do not need. Of course, you have to know what you do not need.

Usually the highest memory usage on a fresh install is due to "Update user folders". Other items are also not really required. For example, I never use Bluetooth, so it is turned off here.

Also you may may want to `sudo apt-get install bum` to have a more detailed boot-up manager.

To sum it up, a freshly installed Ubuntu is running IMHO in a demo mode with many if not all frills and bells noone would ever really need. It just shows what it can do, but not what it can do for you specifically. So you tweak and adjust.

Normal after-startup memory consumption for a 64-bit system is about 240M (depends, can be less than that), for 32-bit even less (maybe 180M or less)

Also there is a bug in readahead package which yields high memory consumption (actually an unreclaimed memory) after a boot-up profiling was performed, i.e. you sometimes see the bug, sometimes not. If this is the case, try running `echo $1 | sudo tee /sys/kernel/debug/tracing/buffer_size_kb 1024` or just reboot one more time.

PS. And yes, try running top or htop to see a detailed memory information. You are not interested in cache in this case, as is pointed out earlier.

---

### Post by l3ecl on 2010-05-17
> **quiritius said:**
>  for 32-bit even less (maybe 180M or less)



i like the minimalist approach and am planning to strip everything to the bone. 
do you have a list of apps that are essential so i can get rid of everything else?

btw thanks for reminding me that fresh installs can be bloated. i was getting the impression that ubuntu was like windows vista being a memory hog.

---

### Post by quiritius on 2010-05-17
> **l3ecl said:**
> i like the minimalist approach and am planning to strip everything to the bone. 
do you have a list of apps that are essential so i can get rid of everything else?

Not really, depends on your needs. But here what is starting here:
- Certificate and Key Storage
- devilspie *
- GNOME Do *
- Network Manager
- Power Manager
- PulseAudio Sound System
- Secret Storage Service
- xcompmgr *
- Parcellite *
* - apps you may need for usability only. Note the xcompmgr, it is installed instead of compiz to enable only *basic* functionality of Gnome Do (some plugins would not work).

In Boot-up manager I only have these:
vboxdrv (for Virtualbox), hdtemp (for sensors display), pulseaudio, acpi-support.

---

### Post by l3ecl on 2010-05-17
I got rid of the non essential services but the change in memory was not that significant. 

```
gg@Ubuntu:/$ free -m
```>              total       used       free     shared    buffers     cached
Mem:           489        379        110          0         38        220
-/+ buffers/cache:        120        369
Swap:         1047          0       1047I read somewhere that the theme might be responsible. Right now I'm using ambiance but would like to switch to something more minimal.

btw is replacing compiz with xcompmgr fairly straightforward? I'm thinking of switching but I don't want to botch up my computer.

---

### Post by Copernicus1234 on 2010-05-17
> **l3ecl said:**
> I got rid of the non essential services but the change in memory was not that significant. 


Because you seem to have ignored what Rhubarb said...he is correct. Read the article he links to.

---

### Post by l3ecl on 2010-05-17
> **Copernicus1234 said:**
> Because you seem to have ignored what Rhubarb said...he is correct. Read the article he links to.

Thank you both Rhubarb and Copernicus, I'm reading the article right now.

---

### Post by XCan on 2010-05-17
> **l3ecl said:**
> I got rid of the non essential services but the change in memory was not that significant. 

```
gg@Ubuntu:/$ free -m
```I read somewhere that the theme might be responsible. Right now I'm using ambiance but would like to switch to something more minimal.

btw is replacing compiz with xcompmgr fairly straightforward? I'm thinking of switching but I don't want to botch up my computer.

You did manage to shave off 62 MB or 33%, which is quite good imo. :)

---

