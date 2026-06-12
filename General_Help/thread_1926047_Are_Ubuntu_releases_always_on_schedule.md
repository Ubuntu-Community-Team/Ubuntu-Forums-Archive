---
title: "Are Ubuntu releases always on schedule?"
date: 2012-02-15
forum: General Help
---

### Post by Advice Pro on 2012-02-15
According to [ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule) of the Ubuntu wiki, 12.04 Beta comes out tomorrow.

Is somewhere that I read what might be in 12.04 Beta or 12.04 in general?  I just want the old Gnome style GUI, which I Alpha 2 has.

---

### Post by JRV on 2012-02-15
According to the release schedule the **feature freeze** is tomorrow.

The beta release is due March first.

It will look about the same as Alpha 2.

As far as I know every release has been on time as long as I have been using Ubuntu.

---

### Post by Advice Pro on 2012-02-15
Thanks for pointing that out.  Is it true that Alpha's & Beta's don't come with repositories or package managers?  If not, how would I install package?

---

### Post by snowpine on 2012-02-15
> **Advice Pro said:**
> Thanks for pointing that out.  Is it true that Alpha's & Beta's don't come with repositories or package managers?  If not, how would I install package?

Completely false. :)

One Ubuntu release has been behind schedule: Dapper Drake was released June 2006 instead of April 2006.

---

### Post by cwklinuxguy on 2012-02-15
^I'm 99% sure that is not true, but I've never been an Ubuntu tester...I don't have the time for any sort of instability on my production machines :P

---

### Post by PaulW2U on 2012-02-15
> **JRV said:**
> As far as I know every release has been on time as long as I have been using Ubuntu.

6.04 was actually released as 6.06. I think that is the only time there has been a delay. Google has plenty of references that suggest that the release just wasn't ready in April.

Before your time, on the forum anyway. :)

---

### Post by pqwoerituytrueiwoq on 2012-02-15
give or take a couple hours 
the lucid image had to be re-spun cause of a small grub bug (IIRC) they did not want in the final product
i was up late that night waiting on the release

---

### Post by dcstar on 2012-02-16
Only fools install the latest Ubuntu for production use on initial release.

Wait at least 2 weeks (preferably 4) for all the major bugs to appear and be resolved and **then** install the freshly released version.

And if anyone has any issues with my first statement, just watch these forums in the first few weeks after **any** new release.

---

### Post by Advice Pro on 2012-02-21
Please answer:

> **Advice Pro said:**
> Is it true that Alpha's & Beta's don't come with repositories or package managers?  If not, how would I install package?

---

### Post by imachavel on 2012-02-21
> **Advice Pro said:**
> According to [ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule) of the Ubuntu wiki, 12.04 Beta comes out tomorrow.

Is somewhere that I read what might be in 12.04 Beta or 12.04 in general?  I just want the old Gnome style GUI, which I Alpha 2 has.

try it on a pen drive first

THIS WORKED GREAT FOR ME:

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

linux mint installed to a pen drive, and I'm about to reboot an boot to my pen drive to see if it worked. Of course this is a windows install method, from linux OS desktop, kde, gnome, or unity compiz plug in the method requires knowledge of linux terminal bash usage

---

### Post by imachavel on 2012-02-21
I don't know the answer to this one, the ubuntu development team will answer the question for you. Keep bumping this thread, this forum moves fast, often times too fast for me. By the time I look up someones question, and find some useful bash terminal commands, ask a question, the thread is on page 2, and then the user often will reply the next day, making it hard to keep up with things on page 2, 3, 4, and what not. It's horrible though to give the impression I'm not interested in helping. I view another forum that mostly deals with windows, it asks difficult questions like vlan forwarding, port rules, server blade builds to set up sockets to quad socket boards, setting up raid with several drives installing an OS to proper install settings with a raid controller installed, boot problems, driver questions, same pain in the *** stuff you see here.
Funny enough though each thread lingers on the first page for sometimes up to a week or two. I'd love to be more involved in ubuntu, which is basically the same concept, an OS with kernel file system support routines, different command line, different interface, more open source, more reliable and stable, less need for virus protection, less supported drivers but often times more stable compiled drivers, and obviously WAY more VERY STRONG community support, but it's hard to keep up on this forum.

some basic stuff for every newbie once the terminal is open

cd directory

sudo su root permission(not necessarily the same as root directory)

ls

pwd

anyway let me not get side tracked, I don't know the answer to your beta question, try testing betas on a flash drive or external hdd:popcorn:

---

### Post by philinux on 2012-02-21
> **Advice Pro said:**
>  Is it true that Alpha's & Beta's don't come with repositories or package managers?

I dont know where you got that from it's completed wrong.

The repositories are up from first loading of the toolchain. Software centre is installed too. Synaptic is not installed by default but can be installed. I have it installed.

---

### Post by forrestcupp on 2012-02-21
> **Advice Pro said:**
>   I just want the old Gnome style GUI, which I Alpha 2 has.
If that's the only reason you want it, you don't have to try to upgrade to an unstable testing version. You can have that in 11.10 right now. If you install Gnome Shell, it will give you the options for Gnome Classic, and Gnome Classic (no effects) in the gear icon next to your login.

---

### Post by Daktyl198 on 2012-02-23
> **Advice Pro said:**
> Please answer:

Absolutely false. 12.04 does not have synaptic, if thats what you mean. Software center still works and you can always install synaptic.
If there were no repositories, there would be no way to update at all.

---

### Post by Daktyl198 on 2012-02-23
> **imachavel said:**
> try it on a pen drive first

THIS WORKED GREAT FOR ME:

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

linux mint installed to a pen drive, and I'm about to reboot an boot to my pen drive to see if it worked. Of course this is a windows install method, from linux OS desktop, kde, gnome, or unity compiz plug in the method requires knowledge of linux terminal bash usage

Also false. If you don't have the knowledge to use the terminal (a simple dd), Linux users always have the option of unetbootin. It is available in Ubuntu repositories. If it is not in the repositories of your specific distro, you can always download the .tar.gz from sourceforge

---

