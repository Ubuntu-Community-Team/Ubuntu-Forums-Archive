---
title: "Advice on cloud image to use for Amazon EC2"
date: 2011-11-12
forum: General Help
---

### Post by dragonfly41 on 2011-11-12
I'm trying to understand how to place a ubuntu 10.10 image on Amazon EC2 (just starting playing with the cloud options).

What is the difference between "EBS" and "instance" images here ..

[http://cloud-images.ubuntu.com/releases/10.10/release/](http://cloud-images.ubuntu.com/releases/10.10/release/)

Which image should I use?

I'm reading the starter guide here ..

[https://help.ubuntu.com/community/EC2StartersGuide](https://help.ubuntu.com/community/EC2StartersGuide)

---

### Post by dragonfly41 on 2011-11-12
Further browsing dug this up .. explaining EBS instance ,,

[http://bitnami.org/tutorials/amazon_machine_images](http://bitnami.org/tutorials/amazon_machine_images)

"There are both regular EC2 images and EBS-backed images. EBS-backed images provide persistent storage between reboots. This means you can start and stop EBS instances as needed and they will keep the data stored in them. Choose one of the images and click the right mouse button to show the list ... "


and here ..

[http://bitnami.org/article/how-to-install-ubuntu-desktop-on-ec2-ebs](http://bitnami.org/article/how-to-install-ubuntu-desktop-on-ec2-ebs)

" Many of the instances of Ubuntu on EC2 are not based on an EBS instance which means you cannot stop/start the service without loosing the data and you cannot create your own ami fresh from the instance. So here is How to create your own Ubuntu Desktop on an EBS based EC2:"



So I assume that it is better to choose an EBS instance?

Cloud newbie.


....

[UPDATE]

I got my first EC2 instance of Ubuntu 10.10 working after some struggles with SSH .. and installed LAMP server

It seems that after connecting through PuTTY  and finally arriving at logging onto Ubuntu instance
the username to use is "ubuntu" and not "root"

This tutorial helped .. [http://alestic.com/2009/04/ubuntu-ec2-sudo-ssh-rsync](http://alestic.com/2009/04/ubuntu-ec2-sudo-ssh-rsync)

---

