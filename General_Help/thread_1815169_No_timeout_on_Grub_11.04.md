---
title: "No timeout on Grub 11.04"
date: 2011-07-30
forum: General Help
---

### Post by jmumby on 2011-07-30
Im trying to run a headless box but grub has no time out so it sits until I plug in a keyboard and hit enter. I have tried to put a timer on using 'startup-manager' but this seems to be ignored. 

When it boots I get GNU GRUB version 1.99~rc1-13ubuntu13 and a list of operating systems. Unless I hit enter it will wait forever. 

Any way around this?

[IMG]http://i.imgur.com/utqvx.jpg[/IMG]

---

### Post by drs305 on 2011-07-30
I'll assume you have looked at /etc/default/grub, which contains the "GRUB_TIMEOUT" setting...

It's possible it's being stopped by a 'recordfail' event (unless you have set the timeout to -1). To find out, boot normally and open 00_header for editing as root:

```
sudo nano /etc/grub.d/00_header
```

Find the following section and make the change. The "-1" value will stop the machine at the menu so change it to any positive value:

> make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
  set timeout=**[COLOR="Red"]-1[/COLOR]**
else
  set timeout=${2}
fi
EOF
}

New:
> make_timeout ()
{
    cat << EOF
if [ "\${recordfail}" = 1 ]; then
  set timeout=**2**
else
  set timeout=${2}
fi
EOF
}

Run "sudo update-grub" to incorporate the changes and see if it now boots without waiting for user input.

---

### Post by jmumby on 2011-07-30
> **drs305 said:**
> I'll assume you have looked at /etc/default/grub, which contains the "GRUB_TIMEOUT" setting...

It's possible it's being stopped by a 'recordfail' event (unless you have set the timeout to -1). To find out, boot normally and open 00_header for editing as root:

```
sudo nano /etc/grub.d/00_header
```

Find the following section and make the change. The "-1" value will stop the machine at the menu so change it to any positive value:



New:


Run "sudo update-grub" to incorporate the changes and see if it now boots without waiting for user input.

I had a look at that but fearing I would loose everything I wasn't tempted to alter it. If I had I certainly wouldn't have know about `sudo update-grub`. Thanks very much worked a treat.

---

