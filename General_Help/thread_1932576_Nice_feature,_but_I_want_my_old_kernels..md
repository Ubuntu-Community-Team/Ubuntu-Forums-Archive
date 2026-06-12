---
title: "Nice feature, but I want my old kernels."
date: 2012-02-27
forum: General Help
---

### Post by Disabled20240622 on 2012-02-27
I've searched for this relentlessly, but I can only find peopke trying to get rid of old kernels (ironic).

I've been shafted by the last update I ran, which came with a new kenrnel (3.0.0-12), and now wake on lan is broken, and the previos kernel (3.0.0-9) is no longer available as a binary, joy!

In an attempt to see that this is or isn't fixed in the latest available kernel (3.0.0-16) I find that it is not, and the nVidia driver is totally unworkable.

What I'm looking for is a way to keep one previous kernel, or a way to qualify a new kernel, even when the previous one is no longer in the repo. So that I never get shafted again.

Anyone know if there is an easy setting to configure this?

---

### Post by audiomick on 2012-02-27
Well, the old kernels are definitely still there. They don't get removed when you get a kernel update.

I gather you have an install with only one OS, so you don't see the grub menu when you boot. If you did, you would see the old kernels, and could simply choose the last known working one to boot into.

I'm afraid I don't know for sure how to show the boot menu when you boot. I think you have to press shift, but I never have had to do this, so I don't really know.

Wait, found something.

Have a look here
[http://askubuntu.com/questions/24586/how-to-alyways-show-the-menu-in-grub2](http://askubuntu.com/questions/24586/how-to-alyways-show-the-menu-in-grub2)

---

### Post by JC Cheloven on 2012-02-27
It's strange. The normal behavior is to keep old kernels until you eventually remove them manually. Only, at boot time they appear now in grub under "previous linux versions". Have you checked that?

Also, could you please check whether your old kernels appear as installed in synaptic or not ?

---

### Post by JC Cheloven on 2012-02-27
> **audiomick said:**
> I gather you have an install with only one OS, so you don't see the grub menu when you boot. If you did, you would see the old kernels, and could simply choose the last known working one to boot into.

Clever point.
To always see the grub menu, please open a terminal and ```
sudo nano /etc/default/grub
```
and comment (put a # character as the first one in the line) these lines:
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=TRUE

so that they look as
```
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=TRUE
```

Edit: oh... save (ctrl-o), exit (ctrl-x), and run ```
sudo update-grub
``` for the changes to take place.

---

### Post by Disabled20240622 on 2012-02-27
Sorry, I should have appeared less n00bish, I do see my grub at boot, and I see the contents of /boot, and I see my package manager.

There are no old kernels on my box, the updates do remove them. Seems t be a change of behaviour in either 11.10 or something prior.

I want to either keep all old kernels (the old way) or keep one.

---

### Post by audiomick on 2012-02-27
> **BigglesPiP said:**
>  Seems t be a change of behaviour in either 11.10 or something prior.

Well, now that you mention it... :-k

I've had 11.04 on my desktop at home, and put 11.10 on there last week. I suspect you might be right, but I can't check, as I am not at home again until the day after tomorrow.
I'm afraid I just haven't paid enough attention to the boot menu to be able to say for sure.

---

### Post by Paqman on 2012-02-27
> **BigglesPiP said:**
> 
There are no old kernels on my box, the updates do remove them. Seems t be a change of behaviour in either 11.10 or something prior.


Even if that's true, you could still reinstall any kernel in the repos.

---

### Post by Disabled20240622 on 2012-02-27
> **Paqman said:**
> Even if that's true, you could still reinstall any kernel in the repos.

As I said, the working kernel (3.0.0-9) is not in the repos now.

They get removed regularly, they also seem not to be archived anywhere. YOu can clone the git repository and checkout the tag for 3.0.0-9 then compile it, but I don't much like compiling your own kernels, it becomes really high mintenence.

---

### Post by yetiman64 on 2012-02-27
> **BigglesPiP said:**
> ... the updates do remove them....
No the update doesn't by design. 

My kernels from 3.0.0-12 to 3.0.0-16, similar situation as you but without missing kernels, some other mistake has been made in your system, maybe even with updates, but it is NOT default behaviour for the distro what you are experiencing, see code box below.

```
yetiman@***********:~$ ls /boot | grep vmlinuz
vmlinuz-3.0.0-12-generic
vmlinuz-3.0.0-13-generic
vmlinuz-3.0.0-14-generic
vmlinuz-3.0.0-15-generic
vmlinuz-3.0.0-16-generic
yetiman@***********:~$
```As you can see I am up to date and still have my old kernels.

Edit:Sounds as if a hardware issue may be in play if you absolutely require the older kernel 3.0.0-9

Edit 2: some specific hardware details may also help. Make, model etc of mainboard and other parts. if a WOL issue.

---

### Post by Disabled20240622 on 2012-02-28
> **yetiman64 said:**
> No the update doesn't by design. 

My kernels from 3.0.0-12 to 3.0.0-16, similar situation as you but without missing kernels, some other mistake has been made in your system, maybe even with updates, but it is NOT default behaviour for the distro what you are experiencing, see code box below.

```
yetiman@***********:~$ ls /boot | grep vmlinuz
vmlinuz-3.0.0-12-generic
vmlinuz-3.0.0-13-generic
vmlinuz-3.0.0-14-generic
vmlinuz-3.0.0-15-generic
vmlinuz-3.0.0-16-generic
yetiman@***********:~$
```As you can see I am up to date and still have my old kernels.

Edit:Sounds as if a hardware issue may be in play if you absolutely require the older kernel 3.0.0-9

Edit 2: some specific hardware details may also help. Make, model etc of mainboard and other parts. if a WOL issue.

Looks like you're on the latest kernel and it's kept just the ones which still exist in the repository.

And yes, I do have a "hardware issue" (software problem actually) which means I need an older kernel, wake on lan is broeken. Which is normally not a bad thing but this is on my HTPC.

---

### Post by yetiman64 on 2012-02-28
I never remove a kernel from the original install off disc. To have a 3.0.0-9 kernel, did you update your install via the update manager from a previous version ? 

If so you may need to look into the repos of the previous version and manually dowload and install the kernel and its headers etc from .deb files instead. Once installed manually you will have to set it as the default boot in grub.

Also please post the hardware details of the mainboard and other hardware involved, someone may be able to search with your details and find a fix or workaround posted elsewhere involving your issue.

Doing so may also lead to an explanation of the behaviour you have noted, it most definitely isn't standard practice to remove an older kernel (or in particular, ALL of them).

---

