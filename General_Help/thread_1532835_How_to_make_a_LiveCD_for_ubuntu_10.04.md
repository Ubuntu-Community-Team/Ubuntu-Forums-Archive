---
title: "How to make a LiveCD for ubuntu 10.04?"
date: 2010-07-17
forum: General Help
---

### Post by Deirty on 2010-07-17
So i installed Ubuntu 10.04 from windows and then i put the programs on it that i want to use but the problem is that i can't find any clear information about how to make a liveCD in 10.04 Could someone please post a link to a How to or explain to me how?

---

### Post by bodhi.zazen on 2010-07-17
Take a look at remastersys

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

See also

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by Deirty on 2010-07-18
Anyone else have any other how to guides for 10.04?

---

### Post by petrus250 on 2010-07-18
The easiest way to burn a simple live cd is to use the ISO file here [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download).
If you want to change the ISO content in any way, I recommend kiso ($ sudo apt-get install kiso) or through the software centre:)
Ubuntu should give you the option, if not, either use kiso or brasero (already installed

---

### Post by Deirty on 2010-07-18
I looked on [http://kiso.sourceforge.net/problem.php](http://kiso.sourceforge.net/problem.php) and it says this,

**"The image looses it's boot capabilities.**
If you open an bootable image and save it again, it looses it's  bootinformation at the moment.
I hope to have it fixed in KIso 0.9. "


Does this mean it wont boot as a live CD?

---

### Post by techunit on 2010-07-18
> **Deirty said:**
> Anyone else have any other how to guides for 10.04?

Yes in fact I do look in my signature... but I don't cover creating a Live CD yet... But I will...

In windows download imgburn (you can find it on CNET) and use that to create a live CD...

Or in Ubuntu use Brasero...

---

### Post by Deirty on 2010-07-18
I could really use something that explains step by step and what programs to use and how to use them. Anyone have anything like that?


added this: I found some ubuntu how to for 9.something would that work?

---

### Post by techunit on 2010-07-18
> **Deirty said:**
> I could really use something that explains step by step and what programs to use and how to use them. Anyone have anything like that?


added this: I found some ubuntu how to for 9.something would that work?
Never Heard Of It... Um are you on Windows or Ubuntu?

---

### Post by bodhi.zazen on 2010-07-18
> **Deirty said:**
> I could really use something that explains step by step and what programs to use and how to use them. Anyone have anything like that?


added this: I found some ubuntu how to for 9.something would that work?


The links I gave you are exactly what you are asking for. If you work your way through the wiki links you understand the process, although I am almost certain you will want some customizations, so only you can add those.

If you simply want a graphical tool to do this for you, look at remastersys

---

### Post by Deirty on 2010-07-18
This is my mistake, I thought i had posted Custom live CD but i did not. Sorry for the misunderstanding. I'm having trouble making a custom liveCD with the programs i want on it installed and put on a CD for later use incase i lose everything. It takes me forever to re do this stuff and i never have the time.

---

### Post by techunit on 2010-07-18
> **Deirty said:**
> This is my mistake, I thought i had posted Custom live CD but i did not. Sorry for the misunderstanding. I'm having trouble making a custom liveCD with the programs i want on it installed and put on a CD for later use incase i lose everything. It takes me forever to re do this stuff and i never have the time.
Well you could search for ubuntu live cd creator in the Software Center... That  works pretty well. I can't remember how to use it though sorry..

---

### Post by Deirty on 2010-07-19
> **techunit said:**
> Well you could search for ubuntu live cd creator in the Software Center... That  works pretty well. I can't remember how to use it though sorry..

I did the search like you said but it dont show up, however ubuntu live cd comes up is this what you where talking about?

---

### Post by bodhi.zazen on 2010-07-19
> **Deirty said:**
> This is my mistake, I thought i had posted Custom live CD but i did not. Sorry for the misunderstanding. I'm having trouble making a custom liveCD with the programs i want on it installed and put on a CD for later use incase i lose everything. It takes me forever to re do this stuff and i never have the time.

From your description, remastersys fits the bill

[http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

First part of that page reads :

> [Remastersys]("http://www.remastersys.klikit-linux.com/") is  very handy application that allows you to         clone and backup your Linux distribution, including root, home,  other partitions, and all personal, custom         configuration to a fully deployable, bootable live CD

Personally, from what you posted, I suggest you simply back up your data.

You can, IMO, more easily clone your installation with dpkg. It is command line, but it will create a list of all installed applications and then, later, if needed, use the list to restore all applications.

Here is a brief overview

[http://syslog.tv/2010/07/02/using-dpkg-selections-to-backup-and-install-packages/](http://syslog.tv/2010/07/02/using-dpkg-selections-to-backup-and-install-packages/)

---

