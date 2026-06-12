---
title: "kernel is old, why?"
date: 2010-07-25
forum: General Help
---

### Post by ilna on 2010-07-25
Here

[https://launchpad.net/ubuntu/lucid/+package/linux-image-generic](https://launchpad.net/ubuntu/lucid/+package/linux-image-generic)

I see last kernel version as:

linux-image-generic 2.6.32.24.25 in amd64 (Updates) 

OTOH, I have (with updated and upgraded Lucid) :

~$ aptitude -v -F '%c   %p  %V    %d' search linux-image-generic
i   linux-image-generic   2.6.32.22.    Generic Linux kernel image 

Why? Of course, I have lucid-updates in sourses list.

---

### Post by dcstar on 2010-07-25
> **ilna said:**
> Here

[https://launchpad.net/ubuntu/lucid/+package/linux-image-generic](https://launchpad.net/ubuntu/lucid/+package/linux-image-generic)

I see last kernel version as:

linux-image-generic 2.6.32.24.25 in amd64 (Updates) 
..........

Yeah, published 2010-07-24 01:05:03 EST - why not wait a day or two for it to actually get to the repositories before complaining?

---

### Post by ilna on 2010-07-25
> **dcstar said:**
> Yeah, published 2010-07-24 01:05:03 EST - why not wait a day or two for it to actually get to the repositories before complaining?

Sorry, it wasn't intention to look as complaining - just am interested in :)

I also have proposed in sources list, and for lats one we have:

Published  on 2010-07-06

---

### Post by DeMus on 2010-07-25
> **ilna said:**
> Here

[https://launchpad.net/ubuntu/lucid/+package/linux-image-generic](https://launchpad.net/ubuntu/lucid/+package/linux-image-generic)

I see last kernel version as:

linux-image-generic 2.6.32.24.25 in amd64 (Updates) 

OTOH, I have (with updated and upgraded Lucid) :

~$ aptitude -v -F '%c   %p  %V    %d' search linux-image-generic
i   linux-image-generic   2.6.32.22.    Generic Linux kernel image 

Why? Of course, I have lucid-updates in sourses list.

Is something not working at the moment? Do you need the new kernel so it can "fix" things? If not, stick with the one you have and be satisfied. When the time is right, the newer version will make it to the repos for everyone to download.

---

### Post by CharlesA on 2010-07-25
I upgraded to the new kernel yesterday, but that was the -server kernel, not generic.

Give it a few days.

---

### Post by ilna on 2010-07-25
> **DeMus said:**
> Is something not working at the moment? Do you need the new kernel so it can "fix" things? If not, stick with the one you have and be satisfied. When the time is right, the newer version will make it to the repos for everyone to download.All works fine. As I have mentioned above, I'm just interested in.

---

### Post by iponeverything on 2010-07-25
> **DeMus said:**
> Is something not working at the moment? Do you need the new kernel so it can "fix" things? If not, stick with the one you have and be satisfied. When the time is right, the newer version will make it to the repos for everyone to download.

Just to side track things, @DeMus -- why did you switch back to 32 bit? (looking at your sig)

---

### Post by ilna on 2010-07-27
Ok, returning to my initial question. I also have proposed in sources list, and here we have:

linux-image-generic 2.6.32.24.25     Published  on 2010-07-06

Just want to verify all Lucid users with "proposed" refs in their sources list also use linux-image-generic  2.6.32.22.23 ATM (as I do). Want to be sure all is ok in my update infrastructure.

---

### Post by Lucifer The Dark on 2010-07-27
Nope I'm using 2.6.35-999-generic, I installed it myself to hopefully fix the VERY old usb slowdown bug, it didn't fix it.

---

### Post by wojox on 2010-07-27
> **CharlesA said:**
> I upgraded to the new kernel yesterday, but that was the -server kernel, not generic.

Give it a few days.

Same here. I got Server and Desktop upgraded.

---

### Post by ilna on 2010-07-27
> **wojox said:**
> Same here. I got Server and Desktop upgraded.
Saying "Desktop" - do you mean linux-image-generic? Which PPAs do you use? I mean situation when 

- 'lucid',
- 'lucid-proposed', 
- 'lucid-backpors' and
- 'lucid-updates' 

ones are in use (without any bettas or any kernel-specific PPAs).

If it is so - are there any configuration details why updating on my installation doesn't lead to upgrading to 2.6.32.24.25?

---

### Post by CharlesA on 2010-07-27
I have no PPAs installed and the latest version is 2.6.32-24-generic for me.

---

### Post by ilna on 2010-07-27
> **CharlesA said:**
> I have no PPAs installed and the latest version is 2.6.32-24-generic for me.

Thanks. So, I can conclude, something is wrong with my installation (in fact, initially I had Karmic, and now it is upgraded to Lucid).

Does anybody know where is that secret configuration place which can block kernel upgrade?

I just want to clarify: my local apt cashe *does* have 'linux-image-2.6.32-24-generic  2.6.32-24.38' package, but 'linux-image-generic' package has 2.6.32.22.23 version.

BTW, how to rebuild local cache completely?

---

### Post by CharlesA on 2010-07-27
Huh. Have you tried running this:

```
sudo apt-get dist-upgrade
```

I've always used that to get kernel upgrades, since I don't use aptitude.

As far as I know, there is no setting to "block" kernel updates.

---

### Post by ilna on 2010-07-27
> **CharlesA said:**
> Huh. Have you tried running this:

```
sudo apt-get dist-upgrade
```

I've always used that to get kernel upgrades, since I don't use aptitude.

As far as I know, there is no setting to "block" kernel updates.
Yes, I have. It does nothing wrt kernel upgrading. OTOH, other software (say, recent firefox, openjdk and so on) were catched as expected.

---

### Post by ilna on 2010-07-28
> **ilna said:**
> Why?
I have found a reason. Following this instructions

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

I had such /etc/apt/preferences file:

Package: *
Pin: release a=lucid-security
Pin-Priority: 990

Package: *
Pin: release a=lucid-updates
Pin-Priority: 900

Package: *
Pin: release a=lucid-proposed
Pin-Priority: 400

As a result, security updates did play only. After moving this file I have got plenty of updates.

---

