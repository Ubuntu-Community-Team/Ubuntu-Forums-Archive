---
title: "Problem with nvidia drivers"
date: 2012-01-29
forum: General Help
---

### Post by Trentin08 on 2012-01-29
Hi I'm pretty new to ubuntu and I'm having problems installing the nvidia drivers.
It's a Hp dv6 series i3. The os is ubuntu 11.10, and the drivers I am trying to install are for nvidia 105m but nothing is showing up once I follow the instructions under the current nvidia driver thread. Sorry everythings a cluster, just frustrated with all of this. Thank you.

---

### Post by heshoots67 on 2012-01-29
> **Trentin08 said:**
> Hi I'm pretty new to ubuntu and I'm having problems installing the nvidia drivers.
It's a Hp dv6 series i3. The os is ubuntu 11.10, and the drivers I am trying to install are for nvidia 105m but nothing is showing up once I follow the instructions under the current nvidia driver thread. Sorry everythings a cluster, just frustrated with all of this. Thank you.

[http://www.nvidia.com/object/win7-winvista-64bit-280.26-whql-driver.html]("http://www.nvidia.com/object/win7-winvista-64bit-280.26-whql-driver.html")

---

### Post by wolfen69 on 2012-01-29
Try installing the nvidia drivers from *Additional Drivers*.

---

### Post by Trentin08 on 2012-01-29
I'm not sure what I'm doing wrong here. Once I go to additional drivers it just show up that there is no proprietary drivers are in use on your system. Followed all the step by step instructions and still getting nothing.

---

### Post by wolfen69 on 2012-01-29
I found a post that tells me how to disable the nvidia graphics and go with just the integrated graphics. Interested? Problem is, some newer laptops are using Optimus, which is a pain to get going right now.

---

### Post by wolfen69 on 2012-01-29
If you wish to try the Bumblebee drivers, (no guarantees) here you go:

```
sudo add-apt-repository ppa:https://launchpad.net/~bumblebee/+archive/stable
```
then
```
sudo apt-get update
```
then
```
sudo apt-get install bumblebee bumblebee-nvidia
```
then
```
sudo usermod -a -G bumblebee $USER 
```
reboot.

---

### Post by Trentin08 on 2012-01-29
Alright I'll give it a shot and let you know how it turns out. Thanks

---

