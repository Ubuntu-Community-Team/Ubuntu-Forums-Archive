---
title: "loss of network on uninstall of ConMan"
date: 2011-04-01
forum: General Help
---

### Post by jwspear on 2011-04-01
I am using Maverick on a Dell Vostro 3400.  I recently installed ConMan network manager and it worked flawlessly in my office and home. I had to travel to Virginina and Pennsylvania and ConMan continued to perform. However, when I returned to my home and office, I could not connect to my WiFi regardless of what I tried.  The instructions, from the Web, that I used to install Conman also had uninstalll instructions that promised to return my network manager to its previous state.  I uninstalled Conman and have not had any network activity since - no network of any kind.  What to do to return to Network Manager??
:confused:
jwspear

---

### Post by tredegar on 2011-04-01
To reinstall network-manager:
```
sudo apt-get update
sudo apt-get install network-manager
```
Should do it for you.

---

### Post by jwspear on 2011-04-01
Without network access i get a list of "failed to access..." error messages and nothing else.

---

### Post by tredegar on 2011-04-02
Then you'll either have to connect with an ethernet cable, or set up your wireless from the command-line:
Two [links]("http://www.wikihow.com/Set-up-a-Wireless-Network-in-Linux-Via-the-Command-Line") to [help]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking") you.

---

