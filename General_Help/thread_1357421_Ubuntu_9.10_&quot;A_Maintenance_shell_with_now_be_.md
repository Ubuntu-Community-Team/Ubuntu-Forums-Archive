---
title: "Ubuntu 9.10 &quot;A Maintenance shell with now be started.&quot;"
date: 2009-12-17
forum: General Help
---

### Post by CharlesA on 2009-12-17
I created a script that would install a bunch of packages after doing a clean install.

I've run it probably 40-50 times to make sure that it runs correctly. It's run fine the last 40 times. >.<

Now I'm getting an error: General error mounting filesystems. A maintenance shell has been started.

The command that is being run is:
```
sudo dpkg-reconfigure exim4-config
```

*The only thing I can think that's changed is that I reinstalled and chose to encrypt my home directory.* :confused:

Does it get stuck since I am running the script as root and said script is located in my home dir?

Also: I created a new VM and install 9.10 without encrypting my home dir, script ran without errors. :confused:

Thanks!

---

### Post by CharlesA on 2009-12-17
Looks like having the home directory encrypted was screwing something up. I copied all the files into /tmp and ran it from there and it still freaked out.

No idea why it did that.

---

### Post by Darael on 2009-12-17
If the encrypted FS that is your home directory isn't mounted (which normally happens when you log in as that user) you can't reach any files in it. Hence, you might want to log in (you could use su in screen if you don't have multiple ttys available) first. Just a thought, if you're logged in already I have no idea.

---

### Post by CharlesA on 2009-12-17
> **Darael said:**
> If the encrypted FS that is your home directory isn't mounted (which normally happens when you log in as that user) you can't reach any files in it. Hence, you might want to log in (you could use su in screen if you don't have multiple ttys available) first. Just a thought, if you're logged in already I have no idea.

Thanks for the explaination.

Basically what I was doing is this:

[LIST]
[*]boot VM
[*]Login
[*]mount cdrom and copy script files to /tmp/
[*]unmount cdrom
[*]cd /tmp
[*]sudo ./clean (which is the script I created)
[*]everything worked fine up until it tried to configure the mail server
[/LIST]

It would also freak out if there was an error in the script, after correcting the errors, it stopped after running:

```
dpkg-reconfigure exim4-config
```

:confused:

---

### Post by CharlesA on 2009-12-18
Apparently it was due to upgrading to the latest server kernel: "Linux 2.6.31-16-server" Since the same thing happened on a machine without an encrypted home directory.

I don't know why either. Wewtskies.

EDIT: I reinstalled 9.10. Ran:

```
sudo apt-get update
sudo apt-get upgrade dist-upgrade
```
Rebooted the machine then ran the script. No problems.

I'm going to try doing the same thing after reinstalling and encrypting my home directory.

---

