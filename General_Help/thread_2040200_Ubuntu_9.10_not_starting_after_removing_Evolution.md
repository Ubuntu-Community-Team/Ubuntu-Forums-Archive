---
title: "Ubuntu 9.10 not starting after removing Evolution"
date: 2012-08-10
forum: General Help
---

### Post by abacki on 2012-08-10
I've had a problem getting Evolution mail, to fetch mail from my hotmail account. It would also cause lockout, of my browser. My first thought was to "fix" it, but instead I had it removed (synaptic package mgr.(?)); and now I cannot get Ubnutu 9.10 to start after login. This must be a dependency issue. Is there a way to re-install Evolution? I think that would be a solution. Grub menu is available.

---

### Post by mörgæs on 2012-08-10
Welcome to the fora.

9.10 reached end of life more than a year ago. Best is to begin with a fresh install of 12.04.

---

### Post by Cheesemill on 2012-08-10
Evolution is one of the dependencies of the ubuntu-desktop package.
By removing Evolution you will probably have forced the removal of the Ubuntu desktop as well.

But I'm with mörgæs, 9.04 reached end-of life more thatn a year ago and as such no longer recieves any support or updates.

---

### Post by abacki on 2012-08-10
Thanks for the replies. However, although upgrade is in my plans, it is not presently an available option. Additionally, I've received no warning that removing Evolution mail, would cause Ubuntu 9.10 to cease operation. Recovery mode is still functioning.

---

### Post by Cheesemill on 2012-08-10
From recovery mode you could try doing:
```
apt-get install ubuntu-desktop
```Although I don't think that will work because the 9.04 repos no longer exist in their default location (because it is no longer supported).

You can try editing your /etc/apt/sources.list file to point to the archived repositories by replacing everything between http:// and /ubuntu with  old-release.ubuntu.com on every line and then trying to install ubuntu-desktop again.

The fact that removing all of the evolution packages also removes ubuntu-desktop is well documented, did you look carefully at the list of packages that Synaptic said it was going to remove?

---

### Post by abacki on 2012-08-10
Talk about exasperating, I wonder why I didn't think to search for a tutorial such as the following. I hope it can still help someone:

[http://www.youtube.com/watch?v=tRax_ehq9Sg](http://www.youtube.com/watch?v=tRax_ehq9Sg)  Set Up Evolution E-mail in Ubuntu 9.10

---

### Post by abacki on 2012-08-10
Thanks, its worth a try! I did look at the list, but it will usually give some sort of warning. I've noticed this even when preparing to install downloaded files. But, I've found now, in an online search that certain files must remain. 



> **Cheesemill said:**
> From recovery mode you could try doing:
```
apt-get install ubuntu-desktop
```Although I don't think that will work because the 9.04 repos no longer exist in their default location (because it is no longer supported).

You can try editing your /etc/apt/sources.list file to point to the archived repositories by replacing everything between http:// and /ubuntu with  old-release.ubuntu.com on every line and then trying to install ubuntu-desktop again.

The fact that removing all of the evolution packages also removes ubuntu-desktop is well documented, did you look carefully at the list of packages that Synaptic said it was going to remove?

---

### Post by abacki on 2012-08-10
Well, nothing beats a try, but a failure. Ubuntu gave a long list of 'failed to fetch' and ended with a 'permission denied.' I'll keep searching. But, if you [or anyone else] have another suggestion, do post it here. Thanks.




> **Cheesemill said:**
> From recovery mode you could try doing:
```
apt-get install ubuntu-desktop
```Although I don't think that will work because the 9.04 repos no longer exist in their default location (because it is no longer supported).

You can try editing your /etc/apt/sources.list file to point to the archived repositories by replacing everything between http:// and /ubuntu with  old-release.ubuntu.com on every line and then trying to install ubuntu-desktop again.

The fact that removing all of the evolution packages also removes ubuntu-desktop is well documented, did you look carefully at the list of packages that Synaptic said it was going to remove?

---

### Post by Cheesemill on 2012-08-10
What are the contents of your sources.list file?
Please post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by abacki on 2012-08-10
The initial response was "permission denied." 

> **Cheesemill said:**
> What are the contents of your sources.list file?
Please post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by dcstar on 2012-08-10
> **abacki said:**
> The initial response was "permission denied."

Use sudo.

---

### Post by Cheesemill on 2012-08-11
> **dcstar said:**
> Use sudo.
I didn't put that because the OP said they were using recovery mode :)

---

### Post by abacki on 2012-08-11
Yes. I already have admin privileges. I'd like to thank you all for your assistance. I took a look at the disc management in win xp, and it shows a 15.35 GB disc for Ubuntu, with 15.35GB of free space. So that OS is gone. I don't usually download an OS, but prefer a CD. I used to order them online, but cannot find the site now. Does Ubuntu still mail CD's? 

Another question; since the grub screen (with recovery mode) is still available, does that mean I will be upgrading from Ubuntu 10., 11, and then 12.00? Or, can I go directly to 12.00? 

Additionally, I should have a backup of 9.10, (stored somewhere), If I want to use the files from that backup, must I reinstall 9.10 before upgrading? To put it another way, should I reinstall 9.10, and then continue with the upgrade? Thanks.

---

### Post by Cheesemill on 2012-08-11
> **abacki said:**
>  I took a look at the disc management in win xp, and it shows a 15.35 GB disc for Ubuntu, with 15.35GB of free space. So that OS is gone.

That doesn't mean that your OS is gone, it just means that Windows doesn't understand linux partitions. You will still be able to recover your old OS.

I would still recommend a clean install of 12.04 though.

Ubuntu no longer sends out free CD's, you can get exactly the same my downloading fron the Ubuntu website though:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

### Post by abacki on 2012-08-11
Is there a way to 'see into the disc' to confirm that it still has Ubuntu 9.10, installed?

I would prefer a clean install of 12.04, but, if 9.10 is still installed, according to info that I've read, I must first upgrade to 10.04 then 11.1, etc.. If this has been changed, I would then, greatly appreciate it.

Ubuntu shop has CD's, which I can order. I get a lot of interference *(also I would suspect, with downloading)* online, and would like to avoid that as much as possible.


> =Cheesemill;12164572]That doesn't mean that your OS is gone, it just means that Windows doesn't understand linux partitions. You will still be able to recover your old OS.

I would still recommend a clean install of 12.04 though.

Ubuntu no longer sends out free CD's, you can get exactly the same my downloading fron the Ubuntu website though:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

