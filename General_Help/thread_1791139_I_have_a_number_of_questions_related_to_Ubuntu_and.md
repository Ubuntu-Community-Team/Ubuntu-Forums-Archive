---
title: "I have a number of questions related to Ubuntu and private cloud"
date: 2011-06-26
forum: General Help
---

### Post by Foremost on 2011-06-26
Hello everyone,

I have a number of questions related to Ubuntu and private cloud:
I would be working on cloud computing for my final year project soonest. 

1. Can any one give me suggestions what are the things to be done after installing ubuntu to deploy a privatre cloud.

2. My computer is running 32bit Intel CPU, is there anyway I could possibly install 64bit Ubuntu/Fedora OS on VM installed on this computer?

3. what are the other software applications that I need to install on ubuntu to enable me create a private cloud.

---

### Post by dino99 on 2011-06-26
community help below , following links

[http://www.ubuntu.com/business/cloud/overview](http://www.ubuntu.com/business/cloud/overview)

---

### Post by blueridgedog on 2011-06-26
The concept of a private cloud is a bit odd and still not completely accepted - but it is growing.  Take a look here:

[http://www.infoworld.com/t/cloud-computing/what-the-private-cloud-really-means-463](http://www.infoworld.com/t/cloud-computing/what-the-private-cloud-really-means-463)

As far as your specific questions:

> 1. Can any one give me suggestions what are the things to be done after installing ubuntu to deploy a privatre cloud.

What services do you want available in your cloud?  You will need a web server, file management tools, network storage - so I would start with the standard LAMP setup plus samba.  [http://en.wikipedia.org/wiki/Cloud_computing](http://en.wikipedia.org/wiki/Cloud_computing)

> 2. My computer is running 32bit Intel CPU, is there anyway I could possibly install 64bit Ubuntu/Fedora OS on VM installed on this computer?

Not possible.

> 3. what are the other software applications that I need to install on ubuntu to enable me create a private cloud.

As mentioned above, I suggest you tell this group the services you want in your cloud and they can suggest applications that provide those services.  I would start with Apache/mySQL/PHP/Samba and go from there.

---

### Post by Duncan Williams on 2011-06-26
If you are going to study cloud computing.
A possible option to assist you in certain ways at least.
Is to install `peppermint 2' which is a cloud based distro based on ubuntu 11.04.

Also using browser extensions such as `lastpass' and `xmarks' keep your browser passwords/logins and bookmarks in the cloud.

You could further customise peppermint to be all cloud based.

peppermint:
[http://peppermintos.com/](http://peppermintos.com/)

lastpass:
[https://lastpass.com/](https://lastpass.com/)

xmarks:
[http://www.xmarks.com/](http://www.xmarks.com/)

---

### Post by Foremost on 2011-06-26
Thanks everyone for your reply and for the helpful information provided so far in respect of my post on a way forward on my cloud computing final year project. I appreciated that!

However, in my previous post, I forget to mention the type of service that I would like to provide on the cloud and this is why I'm sending this second post.

I would like to provide Infrastructure as a service (PaaS)in my cloud environment.

Thanks!

---

### Post by Old_Grey_Wolf on 2011-06-26
Here is a tutorial for Ubuntu Enterprise Cloud [https://help.ubuntu.com/community/UEC](https://help.ubuntu.com/community/UEC). Note the prerequisites.

---

### Post by Habitual on 2011-06-27
> **Duncan Williams said:**
> lastpass

+1 for LastPass

---

### Post by Duncan Williams on 2011-06-27
In relation to the post in general.
There are a number of free cloud applications on my blog at:
[http://my.opera.com/internetsecurity/blog/linux-internet-security-software-and-applications](http://my.opera.com/internetsecurity/blog/linux-internet-security-software-and-applications)

---

### Post by Old_Grey_Wolf on 2011-06-28
> **Foremost said:**
> 
I would like to provide Infrastructure as a service (PaaS)in my cloud environment.

Thanks!

The link I provided for Ubuntu Enterprise Cloud (UEC) in my previous post is for exactly that -- Infrastructure as a Service. One problem for you is that it needs rather robust computers that you may not have. UEC can build a enterprise system similar to what Amazon offers with their Elastic Cloud [http://aws.amazon.com/ec2/](http://aws.amazon.com/ec2/).

For a school project you could do something similar to demonstrate the concept of Infrastructure as a Service; however, it is limited to a single computer using Virtualbox [http://www.virtualbox.org/](http://www.virtualbox.org/); but, it can not be expanded to provide the service as a commodity you could sell. You can get pre-built VMs from this site [http://www.oracle.com/technetwork/community/developer-vm/index.html](http://www.oracle.com/technetwork/community/developer-vm/index.html). This page has a list of pre-built VMs with various Linux based OSes [http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html).

On my laptop I run the 32-bit Ubuntu 10.04.2 and Virtualbox. It has a Dual Core, 2GHz processor, and 4GB of RAM. I can run the Host OS (10.04.02) and 2 VMs of other OSes or distros. The Host OS is 32-bit; therefore, the VMs are 32-bit versions. If the Host OS was 64-bit then the Guest OSes could be 64-bit or 32-bit. If I try to run more that 2 VMs the laptop gets real slow. I give each OS/distro 1 virtual CPU (That is  not the same as a physical CPU). For Windows Vista I give it 2GB of RAM. For Linux based OSes/Distros I give them 1GB of RAM.  Remember that the Host OS gets what is left over and Ubuntu 10.04 doesn't work optimally with less that 1GB of RAM.

---

### Post by Foremost on 2011-06-29
Thanks for your reply and for the explicit explanation. I'm grateful..

---

### Post by Old_Grey_Wolf on 2011-07-01
> **Foremost said:**
> Thanks for your reply and for the explicit explanation. I'm grateful..

If you have more questions you can send me a PM. It may take a few days before I reply; because, I have a job and family life. 

I actually worked on building and testing a virtualized datacenter, and I am currently working on building out another. Any group within the organization I work in can request VMs, networks, and storage. We look at their requirements for compute, network, and storage capacity; then, provision what they need. I actually have experience with Infrastructure as a Service. Every time I bring someone new on the team, I have to teach them about IaaS, PaaS., so maybe I could be of help to you. :)

---

