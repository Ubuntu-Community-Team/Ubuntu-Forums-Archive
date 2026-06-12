---
title: "Update Manager will not load"
date: 2010-11-25
forum: General Help
---

### Post by ExTruckie on 2010-11-25
When I click on the update manager in System\Administration, nothing happens. 
I have  tried to find a solution here to no avail 

I do not relish the prospect of having to do a reinstall

---

### Post by pawhtiobo on 2010-11-25
Have try to launch it from the command line?

$gksudo synaptic


See ya...

---

### Post by ExTruckie on 2010-11-25
> **pawhtiobo said:**
> Have try to launch it from the command line?

$gksudo synaptic


See ya...


I tried that after you suggested it and it brought up a read only version of the package manager.

I thing there is something I am missing?

---

### Post by pawhtiobo on 2010-11-26
Hi :)

It should have asked you for the root password, after you put it, everything shold be fine.

After the command **$gksudo synaptic **and after the **root password**, does it appear any error in the terminal?

See ya...

---

### Post by ExTruckie on 2010-11-26
Hi 
I run the command as stated this is what I get see attachment. I can get the package manager from the system\admin cmd.
What else can I do??

---

### Post by sikander3786 on 2010-11-26
It might well be some problem with your repository information or the configuration of packages.

Please post the output of

```
sudo apt-get update
```

And if that contains any errors, you can do these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

But remember, you need to post the output of all of them ;-)

---

### Post by ExTruckie on 2010-11-26
I did as instructed and I still cannot get the update manager to load. I do however get the following, 

Is this the work around???

---

### Post by sikander3786 on 2010-11-26
As I can see from the snapshot you attached, you are running Jaunty support for which has ended a few months ago.

That might be one thing because of which update-manger is unable to run. As there are no updates... But it should open at least :-k

What I would recommend is to do a clean install with some newer version like 10.04 or 10.10.

You can also upgrade your current release to a newer one but you'd have to go step by step from 9.04 > 9.10 > 10.04 and you can stay with that or even upgrade to 10.10.

---

### Post by ExTruckie on 2010-11-26
Thanks 

I was hoping not to have to do a clean install, as this is my file server and I do not have the drive partitioned due to the size of it.
I guess I have a bit of work to do #-o

---

### Post by dino99 on 2010-11-26
first choice, either:

- sudo dpkg-reconfigure update-manager
- into synaptic: remove/purge then reinstall update-manager


second choice:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by ExTruckie on 2010-11-26
Dino 

Thanks I did as you suggested in and this is the result of the first choice

So I guess its off to the second one 

I am Dl the latest ver as I type this and am also transferring the data on my server to my windows box :rolleyes:

---

### Post by ExTruckie on 2010-11-26
Well after numerous attempts to install Ubuntu 10.10 I dug out my 9.04 install disk and reinstalled it, hoping to do upgrades to the higher versions after I get everything configured.:mad::mad:. I never could get webmin to install under 10.10, or get it to reboot into the desktop. I always had to put the install cd in and it would reinstall everything and not allow a reboot.

---

### Post by ExTruckie on 2010-11-27
Update

Well I found out that since I installed a second HD in my Linux box for additional storage and safety (will eventually be installing raid 1 when budget permits) that both drives have to be hooked up to boot, don't ask me why! 

I have upgraded to 10.4LTS now all I need is to get the second HD to mount at boot, and figure out how to get it mapped to my network. I use Webmin to setup my server functions and the drive is configured there. 
So peeps how do I get my new drive to mount at boot and configure the drives???

Thanks :popcorn:

---

### Post by ExTruckie on 2010-11-27
Final update 

I found out that when I mounted the new drive it was given root ownership so I could map the drive but not write to it. I used the sudo -i to logon as root and change the ownership of the drive and everything is working properly.

---

