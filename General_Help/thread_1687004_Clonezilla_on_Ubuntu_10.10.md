---
title: "Clonezilla on Ubuntu 10.10"
date: 2011-02-13
forum: General Help
---

### Post by meharts on 2011-02-13
Hi guys and girls!
I need some help with a project I am working on......:)
OK! The situation is this:
I have a home network with several computers and now I want to add a server computer which can multicast. 

I have a test server with an inbuilt network card and a separate pci card to help with the project. I intend to separate the server from the network for the multicasting.

I have installed Ubuntu 10.10 desktop version at the moment and have tried to follow to separate versions of how to install Clonezilla on Ubuntu.

The first I looked at was from [Geeky Projects]("http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/") and the second was from The [Packrat Studios]("http://packratstudios.com/index.php/2008/04/20/how-to-setup-clonezilla-on-linux-ubuntu-quick-start-guide/").

The second network card is for the multicasting and I will have a cable to a switch eventually and then connect in several computers for multicasting at once.

I haven't a switch at the moment so a crossover cable is in place for testing. I might have configured everything …..wrong, so I don't mind starting over from a fresh install....

At the moment when I start my test computer – I am getting no DHCP or PROXY received, so it might be just a configuration glich....:)

Can anyone lead me through the process from start to finish?

Like I said I don't mind the work...just want to get this working properly. I will then have a purpose built server for multicasting and backing up images from customer computer etc.

Thanks as always!

meharts

---

### Post by meharts on 2011-02-14
Hi folks!

OK! I have decided to make this some sort of account of what I do from start to finish, so that we can see what might be wrong....
As I said - I am not afraid of a little work, so here goes...

I have just reinstalled Ubuntu Maverick 10.10 (desktop version) and the first thing I have done is remove the network manager

```


sudo apt-get remove network-manager


```

OK! I know this is basic stuff just thinking ahead to those in the same boat....

After removing the network manager I proceeded to set up my network interfaces. I have two as mentioned and I set up both of them at the same time.

I used "Gedit"

```


Sudo gedit /etc/network/interfaces



```

I have attached my settings fot the network cards. I created a subnet to detach my server from the rest of my home network when using Clonezilla.

After adding the information to my /etc/network/interfaces I saved the file and restarted the network.

```


sudo /etc/init.d/networking restart


```

I am now going to update Ubuntu with all updates available.

I just went via System > Update Manger for this one...:)

I will update this later when I have started with the install of DRBL and Conezilla.


meharts

---

### Post by meharts on 2011-02-14
Hi again!

Well, I have updated Ubuntu and followed the [Geeky Projects]("http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/") "How To" to the letter, but it comes up error every time I try to start the Clonezilla Server.

I am attaching that image. I will now do a reinstall and try the Packrat "How To" again.

Take a look at this in the mean time.

meharts

---

### Post by meharts on 2011-02-14
Hi again!

Well, I don't know what it is but I can't get this working?!

I have tried all combinations even from Clonezilla and I can't get anywhere?

I will updtate this if I find the answer..If it is so simple as the "How To's" say why can't I get it working?

meharts

---

### Post by meharts on 2011-02-14
Hi again!

It would be nice for someone to come along and say they are running Ubuntu Maverick with Clonezilla Server Edition...

Just reinstalled with Packrats Instructions and I am getting the same errors?!

I have had enough for one day....

meharts

---

### Post by meharts on 2011-02-15
bump

---

### Post by meharts on 2011-02-15
Hi again!
Ok! I am up and running.........feeling like the guy from "Only Fools and Horses...you know who I mean...Rodney..Dell Boy calls him a "plonka"....LOL

I have reinstalled the desktop version and (not updated it) I then run the instructions from the [Geeky Projects]("http://geekyprojects.com/cloning/setup-a-clonezilla-server-on-ubuntu/")the only thing I changed was the 

```


Which CPU architecture kernel do you want to assign for the DRBL client computer(s)?
0 -> i386 CPU architecture
1 -> i586 CPU architecture
2 -> Use the same architecture as this DRBL server
Note! Note Note! Note! Note! Note! Note!
NOTE!!! If the client computer(s) is not the same architecture as this server, please pick “0&#8243; or “1&#8243;, otherwise your client computer(s) will NOT be able to boot.
If you use wrong architecture type kernel, the glibc and openssl package might use i686 or i386 while the kernel might use i686, i586, or i386, which might be not suitable for all your computer(s).
[2] 2



```

I chose 2 because I forgot what processor was on my test computer...a little intel core 2 duo....LOL

I then was given a choice of which kernel to install and I took the one from apt and not drbl in this case.

I can now boot the client and pxe image loads.....  

Here I am getting a bit lost at the moment. I have rum on my server fro my cloned images, but am not sure of what I should choose to get it to take from my Client and save it on the server?


Has anyone worked with this and can lead me through it?


meharts

---

### Post by meharts on 2011-02-15
Hi again!
Well, I have got going now...LOL. I am now testing pxe creating images and restoring images.
At the moment I am testing Vista!

meharts

---

### Post by meharts on 2011-02-16
Hi again;)
_Question:_

Example:
If I have Windows Vista installed on a partition and the partition is 100GB - how do I image just what is there and not need space for a 100GB?

Even though the partition is a 100GB the files could be 25GB...It isn't a problem with space for 25GB, but it would be expensive on storage if I need the whole 100GB

meharts

---

