---
title: "Pulseaudio/wine sucks"
date: 2010-09-23
forum: General Help
---

### Post by J V on 2010-09-23
Why can't pulse and wine work together? No matter what I do NONE of my wine programs work with this pita pulse...

Even if I use one of the below it always comes out stuttering distorted and just plain painful to the ears...

```
padsp [...]
export WINEDLLOVERRIDES="openal32=n" [...]
```Is there any way to get my wine programs to output sound properly? Hell I'll take an option that disables sound until reboot if I need it cause this is a joke... I'd remove pulseaudio but by now it would probably cause a LOT more harm than good...

Edit: Even installing winepulse from a PPA didn't fix anything: WTF is wrong with wine and why don't they have pulse support now that EVERYONE is using it?...

---

### Post by t.rei on 2010-09-29
[http://art.ified.ca/?page_id=40](http://art.ified.ca/?page_id=40)

check out that site, it works only for lucid, tho.

Since I upgraded to maverick now, I'll have to try and compile this myself, but for lucid the ppa worked like a charm.

*edit* btw: my fallback alsways used to be: 
sudo chmod -x /usr/bin/pulseaudio
killall pulseaudio

but that kills all volume control except the one I put up with some scripts for alsamixer...

---

### Post by t.rei on 2010-09-29
I know, I know, don't reply to yourself, edit.

But since is kindof a seperated thing from the contents above:

Report:
Running maverick with wine patched and compiled as described in the post AND turning off the ptrace security features for the newer kernel (thus making it "only as safe as lucid kernels") Wow and pulseaudio work like a charm while listening to sabaton on rhythmbox and having my pidgin bling bling all the time. 

To get to this:
* Have Maverick installed
* Have your graphiccards drivers installed
* Follow the instructions (step by step, it's really easy): [http://art.ified.ca/?page_id=40](http://art.ified.ca/?page_id=40)
* open a terminal, do 'sudo su -' and then 'echo 0 > /proc/sys/kernel/yama/ptrace_scope' (1 turns the feature back on, if you care)
* run winecfg and enable pulseaudio backend (and turn off the other ones)
* run your game (in my case wow) and be pleased by the sound it makes
* don't be too negative in your posts. :)

---

### Post by Neva on 2011-01-18
I found a pulseaudio-capable wine here:
[http://www.webupd8.org/2010/05/install-wine-with-built-in-pulseaudio.html](http://www.webupd8.org/2010/05/install-wine-with-built-in-pulseaudio.html)

Since I'm using Ubuntu Lucid 10.04, I used the latter repository
sudo add-apt-repository ppa:c-korn/ppa
After that, went to Synaptic package manager and chose to install Wine 1.3 as opposed to Wine 1.2 that's offered from the Ubuntu repositories. Ran winecfg and chose pulseaudio there.

---

