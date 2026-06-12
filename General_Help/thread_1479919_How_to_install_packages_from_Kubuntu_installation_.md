---
title: "How to install packages from Kubuntu installation cd."
date: 2010-05-11
forum: General Help
---

### Post by ibrahim.k on 2010-05-11
Hi,

I am using Ubuntu 10.04 Lucid Lynx on my laptop.

I want to install the 
kubuntu-desktop package.

Can I do this using the Kubuntu installation cd ?

Because my internet connection is very slow

Thx

---

### Post by zvacet on 2010-05-11
I don't think you can install desktop metapackage from desktop CD,but I can be wrong.If I'm let somebody correct me.

---

### Post by ibrahim.k on 2010-05-11
When you insert the Kubuntu disc you will get a message that says do start the package manager.

also in the software sources you can see that a new source has been added when you insert the cd.

I hope I can do this anyway !!

---

### Post by klemes on 2010-05-11
I think that you will be able to if you put the Kubuntu cdrom in the drive and make use of the 

```
sudo apt-cdrom add
```

comand.

---

### Post by ibrahim.k on 2010-05-11
> **klemes said:**
> I think that you will be able to if you put the Kubuntu cdrom in the drive and make use of the 

```
sudo apt-cdrom add
```comand.

[SIZE=4]
I did it and I got this.

Please tell me what is the next step and thnx for helping me.[/SIZE]

ibrahim@ibrahim-laptop:~$ sudo apt-cdrom add
[sudo] password for ibrahim: 
gUsing CD-ROM mount point /media/apt/
Identifying.. [064758854386a0f13aced05990e39899-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called: 
'Kubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)'
Copying package lists...gpgv: Signature made Tue 27 Apr 2010 02:49:08 PM EEST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Kubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100427)]/ lucid main restricted
Repeat this process for the rest of the CDs in your set.
W: Skipping nonexistent file /media/apt/dists/lucid/main/binary-amd64/Packages
W: Skipping nonexistent file /media/apt/dists/lucid/restricted/binary-amd64/Packages
ibrahim@ibrahim-laptop:~$

---

### Post by robert shearer on 2010-05-11
> also in the software sources you can see that a new source has been added when you insert the cd.

Looks like it has been recognised as source media.

Try opening synaptic and search for 'kubuntu-desktop and see if it will install ?

You may need some dependent packages to be downloaded so stay connected, should only be a small download though.



Usually to add a cd as source media you would open "software sources" and the 'other software' tab has an option at the bottom right to 'Add CD-Rom'.

When you select this it will prompt you to load the cd and will add it to the sources.list.

Then, when you search synaptic the packages on that cd will be available.

If they are the most recent versions they will be favoured for install over down-loadable ones.

---

### Post by ibrahim.k on 2010-05-11
Thank you very much guys.

709 mb will be used.
154 mb will be downloaded.

it means that cd is considered as a source and only 154 will be downloaded from the internet.
Thnx again :)

---

### Post by robert shearer on 2010-05-11
Thats strange, I am using an up to date Lucid 10.04 and just selected the kubuntu-desktop for install to see how much would be downloaded.

> 138 new packages will be installed
335 MB of extra space will be used.
70.8 MB have to be downloaded.

That is _without_ having the Kubuntu cd to use as a source.

So I think that a) the cd packages must be older than the current repo packages 
and b) your current Lucid install must not be up to date.

Anyhow if 154MB download is good for you then go for it. :)

---

### Post by ibrahim.k on 2010-05-11
> **robert shearer said:**
> Thats strange, I am using an up to date Lucid 10.04 and just selected the kubuntu-desktop for install to see how much would be downloaded.



That is _without_ having the Kubuntu cd to use as a source.

So I think that a) the cd packages must be older than the current repo packages 
and b) your current Lucid install must not be up to date.

Anyhow if 154MB download is good for you then go for it. :)


This is really strange !!
70 mb is so much better than 154 :(
and the installer hasn't asked me to insert the cd yet.
I hope that everything is on the correct way.

---

### Post by ibrahim.k on 2010-05-11
> **robert shearer said:**
> Thats strange, I am using an up to date Lucid 10.04 and just selected the kubuntu-desktop for install to see how much would be downloaded.



That is _without_ having the Kubuntu cd to use as a source.

So I think that a) the cd packages must be older than the current repo packages 
and b) your current Lucid install must not be up to date.

Anyhow if 154MB download is good for you then go for it. :)


Are you having any problems with the new Lucid Lynx ?

as to me to system suddenly stops working. complete freeze.
I have updated the kernel.

---

### Post by robert shearer on 2010-05-11
> **ibrahim.k said:**
> > Are you having any problems with the new Lucid Lynx ?
     **No ** :) (I am using 32bit Lucid. I see from your post that you have 64bit AMD version..at least that is the Kubuntu cd you are using.)


[QUOTE]as to me to system suddenly stops working. complete freeze.
I have updated the kernel.

Several threads here on sudden freezes etc 

This is just one..[http://ubuntuforums.org/showthread.php?p=9276909#post9276909](http://ubuntuforums.org/showthread.php?p=9276909#post9276909)

(installing the kubuntu-desktop is probably not a fix for an underlying problem, you are still going to have to fix it.)

---

### Post by ibrahim.k on 2010-05-11
I am not installing it to fix this issue just want to test it.
I couldn't solve this after searching and all that stuff did not find any answer :(
I will read the threads anyway\thnx

---

### Post by robert shearer on 2010-05-11
> **ibrahim.k said:**
> I am not installing it to fix this issue just want to test it.


Happy testing  :):)

---

