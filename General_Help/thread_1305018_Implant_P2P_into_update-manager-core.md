---
title: "Implant P2P into update-manager-core?"
date: 2009-10-29
forum: General Help
---

### Post by harry71194 on 2009-10-29
In my opinion, there should be a feature to use libbittorrent or some other bittorrent library in the update-manager-core package, when someone does sudo sudo do-release-upgrade....... they will be presented with "HTTP? or Bittorrent?". if they chose bittorrent, they can enjoy the nice p2p speeds if their ISP doesn't limit. If they do, they chose http.. it would be a nice feature, can we have it in the next release please? It would make the process quicker and lighter on Ubuntu's mirrors.

---

### Post by terry_gardener on 2009-10-29
there is an app called apt-p2p which uses peer to peer first and then mirrors if cant use this.

---

### Post by harry71194 on 2009-10-29
I know of the apt-p2p, but I mean it should be implanted into the distro-upgrade commands :D It would be very useful IMO. I run Ubuntu on many servers, and it pains me to (unintentionally) DoS Ubuntu's mirrors simply by downloading updates, when P2P would go quicker and lighten their server load. :)

---

### Post by harry71194 on 2009-10-29
It'd be interesting to see the vnstat -l of the Ubuntu mirror servers right now :p

---

