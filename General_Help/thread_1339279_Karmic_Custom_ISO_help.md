---
title: "Karmic Custom ISO help"
date: 2009-11-27
forum: General Help
---

### Post by loneowais on 2009-11-27
I have created a custom live cd based off Karmic desktop image.

My problem is that I cannot login to gnome from the LiveCD.
The live cd is supposed to have a user called ubuntu which is automatically logged in but my custom live cd does not do so and  does not accept any combination of usernames and passwords.

please help me out.

---

### Post by nerdopolis on 2009-11-27
I think that if you create a user account without a password, it disables the account. 

there must be some way but I can't find a command to enable it but jonmmc at linuxquestions.org (this thread: [http://www.linuxquestions.org/questions/linux-newbie-8/how-to-add-an-user-without-password-204674/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-add-an-user-without-password-204674/)) suggested:

> There is a hack to do this which works. Replace the user's /etc/shadow password entry with this string...
$1$VNMbpxGH$sew7cnwH9ixU.x27UbFNn.
...e.g...
anon1:$1$VNMbpxGH$sew7cnwH9ixU.x27UbFNn.:14284:0:99999:7:::

---

### Post by bodhi.zazen on 2009-11-27
How did you make the iso ?

You probably need to extract the iso, chroot in, and make a user "ubuntu" with a uid of 999 and a gid of 999, in the admin group.

You may need to  modify the password and or configure sudo (visudo).

Then re-package the iso.

---

### Post by loneowais on 2009-11-27
I'm doing exactly that right now. I don't think it has to be done because no tutorial suggests such an option. Anyways, I'm trying this thing out.
Will let you know guys know about the result.

---

### Post by bodhi.zazen on 2009-11-27
> **loneowais said:**
> I'm doing exactly that right now. I don't think it has to be done because no tutorial suggests such an option. Anyways, I'm trying this thing out.
Will let you know guys know about the result.

There are multiple tutorials on how to make a custom CD, you really should indicate which one you are following.

Personally, IMO, the tutorials are somewhat incomplete and just because a step is not mentioned in a tutorial does not mean you need to do is, as evidenced my your problem.

---

### Post by loneowais on 2009-11-27
Adding ubuntu user with password in chroot did the trick.
It works fine now. However, I now am facing another issue.
Some apps like Gnome-DO, Docky, Blueproximity are firing up automatically at startup. I removed entries from /etc/xdg/autostart but that nothing changes.

---

### Post by bodhi.zazen on 2009-11-27
You will have to edit the config files. They may be located in any of several areas, /etc/skel , /usr/share ...

---

### Post by loneowais on 2009-11-27
Thanks. I'll handle it.

I was wondering if I can write the normal live cd image and an apt-on-cd image to the same disk.

I mean, merging the the two ISOs into one and then burning to a disk.

I know this deserves a separate thread. I'm sorry for continuing here.

---

### Post by bodhi.zazen on 2009-11-27
What are you trying to accomplish ?

---

### Post by loneowais on 2009-11-27
We are having a local Linux meet next week and we want to distribute a customized Ubuntu with custom artwork, multimedia codecs, flash, java and some other stuff.

That's easy. In fact it's done.

We don't want to bloat the distro and at the same time we don't want the users to be dependent on Internet for packages.

So we are making another apt-on-cd disk which will contain extra stuff like Inkscape, Mono, LAMP etc etc.

I  want to have both the disks as ONE.

It should boot up as a live cd and should act as a repository with synaptic.

One way to do so is to install all the packages first then remaster the system, but this bloats the distro. We want minimal install + availablity of additional offline packages on the same Disk.

---

