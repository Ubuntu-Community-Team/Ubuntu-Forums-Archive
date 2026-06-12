---
title: "Multioption bootable usb key"
date: 2012-02-28
forum: General Help
---

### Post by viktorjano on 2012-02-28
I work in a school where we utilizing the potentials of Edubuntu! So far, I have a bootable usb disk where I boot and choose from 2 options, sort of like two images... Since we have one image for instalation on the profesor's desktop, and also one image for pupils' desktop. I hope you get the idea...
But, since those two images are actually Feisty Fawn, I would like in near future to upgrade to some newer version. But, the problem is that I don't have technical support and knowledge for how to configure that kind of bootable usb key that will allow installaton of two different images (and that is by my opinion the the easiest way when you have many computers - booting from usb key)! 

Would someone help?

---

### Post by oldfred on 2012-02-28
I have not used clonezilla, but it sounds like what you want. You configure a system the way you want and then create an image. Clonzilla works with CDs or USB.

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

Some other info:
Kickstart - Unattended Ubuntu installations made easy
[http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/](http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/)

Document system backup or multiple install:
[http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm](http://users.telenet.be/mydotcom/howto/linux/autoinventory.htm)

Multiple installs with rsync.
[http://askubuntu.com/questions/5938/how-can-i-do-mass-installs-on-multiple-computers](http://askubuntu.com/questions/5938/how-can-i-do-mass-installs-on-multiple-computers)
Up to 10 free
[http://puppetlabs.com/puppet/puppet-enterprise/](http://puppetlabs.com/puppet/puppet-enterprise/)
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

### Post by Paddy Landau on 2012-02-28
> **oldfred said:**
> I have not used clonezilla, but it sounds like what you want.
I'm not sure that this is the right tool. CloneZilla will let you back up and restore or clone drive images. It is not used to make installation disks.

Try booting from a computer. Use either Disk Utility or GParted to create two partitions on a USB stick. (Warning: use a fresh USB stick because you will lose *everything* on the stick.) Then use Startup Disk Creator to install one version of Ubuntu onto one USB partition; choose to have "persistence" when prompted. Repeat the exercise to install the other version onto the other USB partition.

Your USB stick will need to be large enough to do this; I would recommend 8Gb at a minimum, with each partition at 4Gb.

The only problem is that your professor has obviously tailored the two images in some way, and you'd have to duplicate that tailoring somehow.

---

### Post by viktorjano on 2012-02-29
Hmmmm!!!
Clonezilla rings a bell... It seems to me that in the process of installation I see that name on the screen... I'll try both ways... Thank you **oldfred**, thank you **Paddy Landau**...
I'll give a try and I'll write down if I achieve something!!!

---

