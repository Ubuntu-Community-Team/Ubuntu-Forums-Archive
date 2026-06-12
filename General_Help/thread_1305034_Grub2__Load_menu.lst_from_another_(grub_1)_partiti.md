---
title: "Grub2 : Load menu.lst from another (grub 1) partition ?"
date: 2009-10-29
forum: General Help
---

### Post by interzoneuk on 2009-10-29
Hi.

As I usually have about 5 OS's installed I usually install grub on each one then add an entry 

(This is from grub1)


root (hd0,*)
configfile /boot/grub/menu.lst

(this is because I have had issues with uuid and other distros.

I kind of like each distro having its own grub menu.lst...

If I try the above on Karmic (grub2) I get various errors .

I notice that the above does work on a grub 2 partition (changing menu.lst to grub.conf)

How to I boot into another grub (grub 1) partition now ?

Cheers

---

### Post by interzoneuk on 2009-10-30
Managed to get an answer to this on kubuntu forums

I have to say that the last few question asked on here have been ignored.

I find that Archlinux/gentoo forums to be much better at getting a response.

If anyone is interested

[http://kubuntuforums.net/forums/index.php?topic=3107371.0](http://kubuntuforums.net/forums/index.php?topic=3107371.0)

---

### Post by alphaniner on 2009-10-30
> I have to say that the last few question asked on here have been ignored.

It's the day after a release for goodness sake.  Just because posts don't get answered doesn't mean they are ignored.

---

### Post by QLee on 2009-10-30
[QUOTE=interzoneuk]
I have to say that the last few question asked on here have been ignored.[/QUOTE]

You are not necessarily being ignored if it takes a while for someone who knows the answer to see the question, very few people trying to help here work at it 365/24/7. I looked at this ready to give you an answer but you already had one. What happened to you was better than what sometimes happens, sometimes lots of wrong answers and false paths litter and confuse a thread before the correct answer appears.

Please have patience with the community here, most people try as hard as they can to help.

Edit: Your statement bothered me so I looked into it a bit further. Since Sept 29 2006 you have made three posts that received 0 replies. Two of them were essentially "how tos" where you gave an answer rather than asking a question and the third was a question about compiling your own kernel, which is something the general Ubuntu user doesn't do. It doesn't surprise me that there weren't a lot of answers for that.

The three posts with 0 replies were:
2009/Jan 29 (how to)
2008/Aug 24 (unanswered question about kernel)
2008/Apr 24 (how to)

Oops, doesn't look like you've been ignored except the one time last year.

---

### Post by VMC on 2009-10-30
> **interzoneuk said:**
> Hi.

As I usually have about 5 OS's installed I usually install grub on each one then add an entry 

root (hd0,*)
configfile /boot/grub/menu.lst

...

How to I boot into another grub (grub 1) partition now ?

Your not booting into a grub1 partition, your just booting that partition. Your title implies your using grub2. If so use chainloading, like so:
```
menuentry "Microsoft Windows XP" {
set root=(hd0,2)
chainloader +1
}
menuentry "Chainload Ubuntu 9.10 on /dev/sda3" {
set root=(hd0,3)
chainloader +1
}
```

Output your grub.cfg file, from "/boot/grub/grub.cfg".

Do you know where that is? do a 'sudo fdisk -l' so we can see your setup.

---

