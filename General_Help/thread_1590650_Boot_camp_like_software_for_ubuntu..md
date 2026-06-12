---
title: "Boot camp like software for ubuntu."
date: 2010-10-08
forum: General Help
---

### Post by jeetendra.choudhary on 2010-10-08
Hi All,

Just curious to know if there is any software available like boot-camp for ubuntu. I am currently using Vbox for my work but there are some problem with that.

Thanks & Regards
Jeetendra

---

### Post by kerry_s on 2010-10-08
what? isn't that what grub does? or yaboot if your using as ppc.

---

### Post by isoscelesrectangle on 2010-10-08
mmmm... I think you can partition with Gnome Partition Manager, install whatever OS you desire, then choose with GRUB, or install BURG if you prefer a nice GUI kinda like rEFIt.

---

### Post by jeetendra.choudhary on 2010-10-08
Hi All,

Thanks for your helpful replies. I have no idea about BURG or yaboot sorry for that pretty noob about these thing what i wanted and i know about boot camp is its a kind of virtual machine in which you can install other OS (in my case want to install xp) and then you can use that os inside the host OS or you can also use same guest OS (XP) to boot directly as host OS. please correct me if i am wrong. I wanted that kind of functionality is it available for ubuntu.?

Thanks & Regards
Jeetendra

---

### Post by SeijiSensei on 2010-10-08
Well, Virtualbox is the easiest solution.  What's the problem that you mentioned in your original post?

---

### Post by jeetendra.choudhary on 2010-10-10
Hi,

The problem is that for some of the development software we use for our office are not available for ubuntu or linux. So the easiest solution is vbox with xp.
I have assigned 2 gb of ram to guest OS then also when that software runs its vey very slow sometime stops responding at all. One of my peers uses mac and he have same v box kind of software, so when ever he thinks its slow for his working using that software called boot camp (I am not sure its boot camp or parallel) he  just boots the guest os directly (off-course after restart ) and the advantage of this is he can use all the available ram in guest os. I hope it make sense.

Thanks & Regards
Jeetendra

---

### Post by sendblink23 on 2010-10-10
> **jeetendra.choudhary said:**
> Hi,

The problem is that for some of the development software we use for our office are not available for ubuntu or linux. So the easiest solution is vbox with xp.
I have assigned 2 gb of ram to guest OS then also when that software runs its vey very slow sometime stops responding at all. One of my peers uses mac and he have same v box kind of software, so when ever he thinks its slow for his working using that software called boot camp (I am not sure its boot camp or parallel) he  just boots the guest os directly (off-course after restart ) and the advantage of this is he can use all the available ram in guest os. I hope it make sense.

Thanks & Regards
Jeetendra

Bootcamp is Dualbooting - same as if your computer was Windows originally only & afterwards installing ubuntu side by side

In other words Grub is what you use to boot between Ubuntu or Windows - unless Wubi was used

Anyways if your computer is a MAC then Bootcamp is your best option, if your computer is originally Windows then its like i just mentioned previously... then on that case make a dualboot install(partition the hard drive)

---

### Post by VanceVEP72 on 2010-10-10
I just installed VirtualBox on my laptop this afternoon and am running XP Pro in it under an Ubuntu host. Works great with no performance issues. My VB installation setup 20GB of hard drive space for the installation which is probably part of the reason?

---

### Post by sendblink23 on 2010-10-10
> **VanceVEP72 said:**
> I just installed VirtualBox on my laptop this afternoon and am running XP Pro in it under an Ubuntu host. Works great with no performance issues. My VB installation setup 20GB of hard drive space for the installation which is probably part of the reason?

If you read the OP's previous post the person mentioned that the user has been using it already but its had issues

-jeetendra.choudhary
> So the easiest solution is vbox with xp.
I have assigned 2 gb of ram to guest OS then also when that software runs its vey very slow sometime stops responding at all. 

in other words still asking for another solution(since vbox wasn't enough for the users need)....  best way for using their full hardware is really just making a dualboot - install the other OS side by side

---

### Post by jeetendra.choudhary on 2010-10-10
Hi,

Thanks All for your kind response and help. I think there is no other go at this time so i'll make it dual boot actually i never like to work in windows os but unfortunately i have to. I wish all the software should be available for ubuntu one day.

Thanks & Regards
Jeetendra

---

