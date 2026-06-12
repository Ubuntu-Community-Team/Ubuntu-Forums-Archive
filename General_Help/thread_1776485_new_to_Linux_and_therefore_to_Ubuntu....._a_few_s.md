---
title: "new to Linux and therefore to Ubuntu..... a few ?s"
date: 2011-06-06
forum: General Help
---

### Post by fraser80 on 2011-06-06
Hello. I have recently purchased an ASUS Eee PC (netbook) model 1215T MU10. It has the AMD Athlon II Neo K125 (1.70GHz) processor and a AMD 'nile' platform with an integrated AMD Mobility Radeon HD 4250 graphics card. It has 2 gigs of DDR3 ram. I received the netbook with no OS and installed Ubuntu 11.04 Natty as its only OS. Could someone please give me a bit of advice regarding the steps I should take to make this OS as functional as possible on the computer which it is installed. I have tried to do this myself and noticed I could not access certain plug-ins such as Unity and Compiz ccss. I fiddled with things and eventually ended up having to do a fresh install of the OS and coming to the realization that I have not a clue what I am doing. I have seen video reviews of the unity interface and would absolutely LOVE to have some of the cool things it can do happening on my display. Thank you. :)

---

### Post by pqwoerituytrueiwoq on 2011-06-06
since it is a netbook you may want to use the netbook remix version
[http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-netbook-i386.iso.torrent)
it is light weight and has ui adjustments for lower screen sizes

that said if you want unity (you will not get it with the above) 
check hardware drivers for something for the video card
system->administration->hardware drivers

---

### Post by TBABill on 2011-06-06
+1
 
You must get your video card driver installed properly to use Unity as it's designed. Without 3D support you won't really have a true Unity experience. 
 
If you need codecs ```
sudo apt-get install ubuntu-restricted-extras
```
 
If you need Sun Java (the system comes with open java, which works on some sites, not on others), enable in Synaptic (or software sources) the repository for Canonical Partners or something like that. Then refresh synaptic, search for sun java and install the sun java plugin. That'll pull in dependencies for you. 
 
For Flash, you'll get the repo version of flash from ubuntu restricted extras. If you want to always have the latest flash, either install Ubuntu Tweak or Flash Aid. Flash aid is installed as an extension in Firefox and works beautifully, but you can also do so via Ubuntu Tweak. I'm not sure what repo you have to add to get Ubuntu Tweak, though, but it gives you TONS of extra repos you can select and software you can install.

---

