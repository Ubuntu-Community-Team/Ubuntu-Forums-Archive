---
title: "Ubuntu Minimal Install and Security Updates"
date: 2012-04-04
forum: General Help
---

### Post by carmenin87 on 2012-04-04
I've been following the guide psychocats.net to install a minimal version of Ubuntu.

One of the screens in this tutorial is in regards to security updates.  The screenshot looks like [http://www.psychocats.net/ubuntu/images/minimallucid26.png](http://www.psychocats.net/ubuntu/images/minimallucid26.png)

Rather then choosing Install Security Updates automatically, how do you setup the system like the current Ubuntu whereby you can go into "Update Manager", check for updates and then install them?

---

### Post by jerrrys on 2012-04-04
The package "update-manager" gives you desktop updates.  Remove this package (leave update-manager-core) and you will have to manually update.

To do manual updates install Synaptic Package Manager.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9)

The terminal command for this:

sudo apt-get remove update-manager && sudo apt-get install synaptic

---

