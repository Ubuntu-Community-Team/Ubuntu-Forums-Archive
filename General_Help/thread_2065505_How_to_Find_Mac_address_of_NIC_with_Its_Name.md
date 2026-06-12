---
title: "How to Find Mac address of NIC with Its Name"
date: 2012-10-02
forum: General Help
---

### Post by sharma251185 on 2012-10-02
Hello

How can I find the MAC address of my NIC card and its name.

Just for Example.

I've one system with 4 Ethernet port. Now I can get the MAC address by "ifconfig" but the question is which mac address is binded to the particular Ethernet card or port?

So I can connect to the exact network.

---

### Post by SlugSlug on 2012-10-02
sudo lshw |more

Under Network look for serial and physical ID

On mine physical ID 0 is eth0 and its serial is its mac

---

