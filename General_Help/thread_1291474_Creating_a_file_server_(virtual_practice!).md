---
title: "Creating a file server (virtual practice!)"
date: 2009-10-14
forum: General Help
---

### Post by RobertBorgersen on 2009-10-14
Hi there,

I am new to linux and virtualbox, but I want to create a linux file server using Xubuntu 9.04 on a extra box I have now. I found a walkthrough to create one ([http://tinyurl.com/2s56ys](http://tinyurl.com/2s56ys) -- I followed all the instructions on this page) and I wanted to do it in a virtual machine first to get the hang of it without formatting and redoing my extra box.

I followed the instructions, but once samba was up and running, I couldn't access the shared directory from my host machine. I'm wondering if it _should_ work at all--I figured it would, but maybe I'm wrong. I noticed that virtualbox created it's own "network card" with its own ip address, and I tried accessing it through that ip address, but I couldn't get it. So I just don't know if the problem is with using VirtualBox or if it is because I set something up wrong.

Thanks for any help

Rob

---

### Post by jbrown96 on 2009-10-14
What is the networking mode? Go into the settings for the virtual machine-->network. It will be something like NAT, Host Only, Internal Network, etc. You definantly won't be able to use NAT, but if you are only going to test it from the host, then you can probably use host only. There may be additional steps to get it to work. Also you will need to make sure that the firewall is opened. For testing the easiest method is to disable it on the virtual machine. ```
sudo ufw disable
``` When you set it up on the physical machine, you will want to just open the specific ports.

---

