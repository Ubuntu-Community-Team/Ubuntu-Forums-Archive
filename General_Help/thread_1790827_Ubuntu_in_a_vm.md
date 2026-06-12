---
title: "Ubuntu in a vm"
date: 2011-06-25
forum: General Help
---

### Post by Helveticus on 2011-06-25
Hello

I have Windows 7 64bit as host and I want to install Ubuntu in a vm. I'm using VMware Workstation. I have some questions because I'm new to Ubuntu and I hope that you can help me.

1. Should I install in the vm Ubuntu 32bit or 64bit? Totally I have 4GB RAM. I'm using Ubuntu not so much, only for example for Matlab or for safe browsing.

2. How much memory should I allocate Ubuntu in the vm? Totally I have 4GB RAM.

3. I also want to use Ubuntu for safe browsing. How does I have to take the settings in Ubuntu so that it's safe and if there is an infection it will not be infect the host? So a connection between host and guest should be avoided but it's not totally possible because I want to go in the internet in the vm.

---

### Post by haqking on 2011-06-25
> **Helveticus said:**
> Hello

I have Windows 7 64bit as host and I want to install Ubuntu in a vm. I'm using VMware Workstation. I have some questions because I'm new to Ubuntu and I hope that you can help me.

1. Should I install in the vm Ubuntu 32bit or 64bit? Totally I have 4GB RAM. I'm using Ubuntu not so much, only for example for Matlab or for safe browsing.

2. How much memory should I allocate Ubuntu in the vm? Totally I have 4GB RAM.

3. I also want to use Ubuntu for safe browsing. How does I have to take the settings in Ubuntu so that it's safe and if there is an infection it will not be infect the host? So a connection between host and guest should be avoided but it's not totally possible because I want to go in the internet in the vm.

1.  I use 32 bits for all my VM's even though i run a x64 linux host with 4gb ram. and they work fine, unless you have areason to use x64 such as performance which i think is irrelevant in VM example

2. Depends how your host usually performs, i usually give mine 512 or upwards, my windows & Vm running on my Ubuntu host has 768mb and runs fine ( i know i have things the other way around to you as i use Linux as my host.

3. A chacnce of an infection of any type from a Linux VM coming down to a windows machine is very unlikely.  VM can infect a host in certain circumstance but it is more the other way around as in from Windows VM to Linux host which again is unlikely, a virus say for a .exe would not effect linux as it does not use .exe.

Safe browsing you could use private browsing feature in your browser, run a av if you feel the need like avg, avast, clam av all of which are available for linux, opinion is 50/50 on whether you need it for a linux build however

have fun

---

### Post by Helveticus on 2011-06-25
Thank you very much.

> Safe browsing you could use private browsing feature in your browser,  run a av if you feel the need like avg, avast, clam av all of which are  available for linux, opinion is 50/50 on whether you need it for a linux  build however

What is private browsing and how do I use it? I never heard about it.

---

### Post by haqking on 2011-06-25
> **Helveticus said:**
> Thank you very much.



What is private browsing and how do I use it? I never heard about it.

private browsing does not offer too much other than non storage of history, cookies etc etc and is a feature in Firefox on the tools menu.

there are other methods and other browsers obviously

---

### Post by dcstar on 2011-06-25
> **Helveticus said:**
> Hello

I have Windows 7 64bit as host and I want to install Ubuntu in a vm. I'm using VMware Workstation. I have some questions because I'm new to Ubuntu and I hope that you can help me.
..........

FYI there is a separate Virtualization forum that covers all you need to know about VMs in Ubuntu.

---

### Post by trizrK on 2011-06-25
> **Helveticus said:**
> Hello

I have Windows 7 64bit as host and I want to install Ubuntu in a vm. I'm using VMware Workstation. I have some questions because I'm new to Ubuntu and I hope that you can help me.

1. Should I install in the vm Ubuntu 32bit or 64bit? Totally I have 4GB RAM. I'm using Ubuntu not so much, only for example for Matlab or for safe browsing.

2. How much memory should I allocate Ubuntu in the vm? Totally I have 4GB RAM.

3. I also want to use Ubuntu for safe browsing. How does I have to take the settings in Ubuntu so that it's safe and if there is an infection it will not be infect the host? So a connection between host and guest should be avoided but it's not totally possible because I want to go in the internet in the vm.
Here are my recommendations:
1.It depends if what architecture your processor is designed for. Check if your system is 64 bit or 32 bit.
2.for what you said you were going to use it for i'd say 512gb to 1gb. If intended to run heavy programs then definetly 1gb if you can afford it.
3.Look into Tor. It is Linux compatible.
The Tor website: [www.torproject.org]("http://www.torproject.org")
good luck!:-)

---

