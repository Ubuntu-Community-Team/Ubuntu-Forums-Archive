---
title: "Downgrading"
date: 2011-08-16
forum: General Help
---

### Post by Hosmion on 2011-08-16
Hello everyone!

So first of all, I upgraded to 11.10.  A little bit prematurely.  Where I don't want it because of all it's problems.  Now I know it was a stupid move so please don't come at me with all these insults saying how I was stupid to upgrade so early.  I watched a YouTube video on it and it seemed pretty stable so I wanted to try it out.

Now to the point of this thread.  My usb port is...  not working at the moment.  Don't really know why.  So I went to [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto) trying to find help, and I did.  I got the script and executed it to spit out all the programs and everything, but then it says:

```
The above script will spit out a list of packages to downgrade, and the version numbers to downgrade to. If everything looks ok, hold your breath, do a little good luck dance and **uncomment the relevant line.**
```

What does uncomment the relevant line mean?  How would I do that?

Thanks for the help,
Leonard

---

### Post by haqking on 2011-08-16
> **Hosmion said:**
> Hello everyone!

So first of all, I upgraded to 11.10.  A little bit prematurely.  Where I don't want it because of all it's problems.  Now I know it was a stupid move so please don't come at me with all these insults saying how I was stupid to upgrade so early.  I watched a YouTube video on it and it seemed pretty stable so I wanted to try it out.

Now to the point of this thread.  My usb port is...  not working at the moment.  Don't really know why.  So I went to [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto) trying to find help, and I did.  I got the script and executed it to spit out all the programs and everything, but then it says:

```
The above script will spit out a list of packages to downgrade, and the version numbers to downgrade to. If everything looks ok, hold your breath, do a little good luck dance and **uncomment the relevant line.**
```What does uncomment the relevant line mean?  How would I do that?

Thanks for the help,
Leonard

remove the comment # from the line that pertains to you so that line runs.

However if i was you i would just do a re-install, the page says it is buggy.

11.10 is only an alpha so is only to be installed for bug testing and reporting to stabilise the final realease etc.

If i was you i would back up if not already my data and do a clean re-install

---

### Post by MG&amp;TL on 2011-08-16
I have absolutely no specific ideas, but on a linux-wide basis, you could try opening with text editor, then decommenting relevant line (remove #)

 If I were you, I'd burn a cd, backup your filesystem and whatnot, reinstall, away you go. But that's me. Do stuff in VirtualBox next time. (not calling you dumb, just pointing out the Vbox option)

EDIT: arrgh, beaten to it. :P

---

### Post by haqking on 2011-08-16
> **MG&TL said:**
> I have absolutely no specific ideas, but on a linux-wide basis, you could try running it, seeing the output, then opening the script with a text editor to 'uncomment the relevant line' -comments in bash are preceded by a '#'.

Or do that first, before you run the script. If I were you, I'd burn a cd, backup your filesystem and whatnot, reinstall, away you go. But that's me. Do stuff in VirtualBox next time. (not calling you dumb, just pointing out the Vbox option)

Thats ok but virtualisation is not meant for Alpha releases.  The whole point of Alpha and Beta releases is for testing and bug reporting.

If you run 11.10 in a Vm you are running it on virtualised hardware which is not the same thing and so you cant provide thorough testing and bug reporting which is what the Alpha releases are for.

---

### Post by MG&amp;TL on 2011-08-16
True, but he said 'upgraded to' not 'tested', so what I assumed he meant was that he'd heard about it, thought 'oh, new release', got the .iso and away he went.

My bad.

---

### Post by Hosmion on 2011-08-16
I cannot do a fresh install because Ubuntu is on a flash drive, and the usb ports are not working.  Ordering from the Canonical Store (the 5 cd pack) takes up to 31 days to deliver.  I was just looking for a quicker way to get back to 11.04.  

When you say to remove the #, what do you mean?  In the script?  what part of the script would I remove it from?

Sorry for all the stupid questions, but I don't really know how to do this.  I appreciate all of your help.  

Please note: all my files are already backed up, so that is not an issue.

---

### Post by haqking on 2011-08-16
> **MG&TL said:**
> True, but he said 'upgraded to' not 'tested', so what I assumed he meant was that he'd heard about it, thought 'oh, new release', got the .iso and away he went.

My bad.


Yes i agree.  I was just saying for others who may read the thread so they are clear on what a Alpha release is and why not to bother using it in a VM unless it is just for curiosity, just expect it to be buggy and have flaws

---

### Post by MG&amp;TL on 2011-08-16
Uhh...any problem with burning a cd?

---

### Post by Hosmion on 2011-08-16
> **MG&TL said:**
> Uhh...any problem with burning a cd?

I don't have any CD's with over 2 GB of space.  I only have 700 MB I think.

---

### Post by MG&amp;TL on 2011-08-16
I burned an 11.04 cd on a 700mb cd. Where are you getting your .iso from? The only thing I know of that takes 2GB is Edubuntu. Even Kubuntu fits on a 700mb disk-that's the point.

[http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download") Here's where I get mine.

---

### Post by haqking on 2011-08-16
> **Hosmion said:**
> I don't have any CD's with over 2 GB of space.  I only have 700 MB I think.

You mean your instalation media is on a flash drive ?

Just download the iso image it is only around 685 mb and burn it to a cd

---

### Post by Hosmion on 2011-08-16
I read somewhere that you needed at least a 2 GB flash drive and I thought the same about disks.  I'll try that real quick, thanks!

---

### Post by haqking on 2011-08-16
> **Hosmion said:**
> I read somewhere that you needed at least a 2 GB flash drive and I thought the same about disks.  I'll try that real quick, thanks!

no just choose your .iso image and download it should be under 700mb

---

### Post by Hosmion on 2011-08-16
Well I didn't get the CD to work but I finally got the Flash Drive working!

Yay!  I finally have a stable laptop again!

---

