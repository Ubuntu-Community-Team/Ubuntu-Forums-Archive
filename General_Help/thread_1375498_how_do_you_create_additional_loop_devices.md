---
title: "how do you create additional loop devices?"
date: 2010-01-08
forum: General Help
---

### Post by yogii on 2010-01-08
Ubuntu 9.10

How do you create additional loop devices? (by default 8 loops)

What i tried so far
Added options max_loop=64 to the /etc/modules file -> no success

Thank you

---

### Post by michy99 on 2010-01-08
Did you re-boot after changing the /etc/modules file?

---

### Post by Black Sun on 2010-01-08
Can anyone explain what are these "loop devices" and what is this "/etc/modules" file is for?

---

### Post by yogii on 2010-01-08
i rebooted after adding it too the \etc\module 
then created /dev/loop 8 to 65 as a mounting point

is loop device setup in the grub with ubuntu 9.10 or module?

---

### Post by tinkerbox on 2010-01-22
> **yogii said:**
> i rebooted after adding it too the \etc\module 
then created /dev/loop 8 to 65 as a mounting point

is loop device setup in the grub with ubuntu 9.10 or module?

Never works for me. Yup, i rebooted :(
/etc/modules
```

loop max_loop=64
lp

```
Im on ubuntu server 9.10 installed on software raid 0
I also tried this page guide: [http://planet.admon.org/howto/create-additional-loop-devices-in-linux/](http://planet.admon.org/howto/create-additional-loop-devices-in-linux/)
No success 

But when i tried on ubuntu server 8.04, the same code in /etc/modules
it just works. After google somemore, I found out that loop modules added in kernel for 9.10
I just dont know how to fix this yet. Anyone?
I dont want to downgrade to 8.04 [-(

---

### Post by tinkerbox on 2010-01-22
I tried install fresh server 8.04 on vmware.
Did upgrade until it reach server 9.04, i checked loop device list,
it was revert back to default. 8 loop device :(
Anyone??

---

### Post by tinkerbox on 2010-01-22
Nvm, found it with google:
```

for i in $(seq 0 255); do
  mknod -m0660 /dev/loop$i b 7 $i
  chown root.disk /dev/loop$i
done

```
add this script to /etc/rc.local
so that it will re-create upon next reboot automatically :)

---

### Post by mungwana on 2010-02-27
None of these options worked for either but after reading up a bit on the matter I found that the loop module has been included in the latest linux kernel and needed to be changed there.

I am  using Ubuntu 9.10.

What I did was is edit **/etc/defaults/grub**

and added the code **max_loop=64** just after the **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash** 

```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash max_loop=64"
GRUB_CMDLINE_LINUX=""

```

** Don't forget to close the ( **"** ) after the **max_loop=64** part!!*

Saved it then ran **update-grub** and rebooted the machine and thats it.

You can run **ls /dev/loop*** just to check it but you should see a total of 64 shiny new loop devices.

:popcorn:

---

### Post by tim000 on 2011-07-18
Here is how I increased loops in GRUB2 in Lupid, it worked.

First see how many loops you have with this command
ls /dev/loop* 

Then edit this grub module 10_linux
gedit /etc/grub.d/10_linux

Inside 10_linux, find the line that looks simular to the line below
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}

Make the lline look like this - 
    linux    ${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args} max_loop=64

Save it, 10_linux

Remember to run the command below (to incorporate the change)
grub-update 

ReBoot your system and rerun this command you should see 64 loops
ls /dev/loop*

---

### Post by yohoho46 on 2011-11-09
I have mixed results doing this.  On a ovh server at some point in time the server will cease to boot.  So far I have never been able to get any one of several back to booting again, so that means I reload the entire server to fix the issue.

Since ovh has some rescue tools it is possible to salvage all the data, but even a reinstall of grub will not get the os partition to ever boot again.

Any thoughts why this would cause a new stable install of ubuntu to never boot again?

---

### Post by scotjam1981 on 2012-12-16
Mungwana's solution worked for me on Ubuntu 12.04 LTS (Precise) - thanks for your insight!

---

### Post by oldos2er on 2012-12-16
Old thread closed.

---

