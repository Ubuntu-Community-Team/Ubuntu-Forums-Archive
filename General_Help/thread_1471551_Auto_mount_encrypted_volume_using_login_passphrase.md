---
title: "Auto mount encrypted volume using login passphrase"
date: 2010-05-03
forum: General Help
---

### Post by alexanda on 2010-05-03
I recently installed Ubunutu 10.04 Netbook Remix onto a Dell Vostro A90.  During install I selected "Require my password to log in and to decrypt my home folder", and this is working great.

What I would like to figure out, is how to have a second encrypted volume that lives on my SD Card that is also decrypted automatically upon login.  

I've tried a variety of things, but they all require me to re-enter my password at some point during the boot/login, once for user login and the other time to decrypt/mount the volume.  I am trying to avoid this, and hopefully will only have to enter my password once.  Maybe I can piggyback on the default Ubunutu home directory decryption and make it all appear seamless?

Thanks in advance for any pointers.

---

### Post by arbrandes on 2010-05-06
I'm looking for the exact same thing.  10.04 UNE, trying to decrypt SD or USB drive (or any partition, for that matter) automatically on login.  No luck so far.

---

### Post by arbrandes on 2010-05-06
I asked on #ecryptfs (irc.oftc.net), and anrxc was nice enough to give me some pointers.  I'm still setting things up, but basically, yes, it is possible.

I'm following his excellent article here:

[http://sysphere.org/~anrxc/j/articles/ecryptfs/index.html](http://sysphere.org/~anrxc/j/articles/ecryptfs/index.html)

It seems that the easiest way to do what we want is to start by using the same exact passphrase for /home/<user> and for /media/<mount>, because PAM can only insert one passphrase to the kernel keyring on login.

After that, one would insert a few bash commands to $HOME/.bashrc to mount the external SD.  I'm still not there yet, will post results.

---

### Post by arbrandes on 2010-05-06
Ok, I can confirm it works.  It's quite simple, really:

1) Mount an arbitraty directory on the SD with ecryptfs, using exactly the same passphrase that you jotted down when first logging in after installation.

2) After mounting it, edit /etc/mtab and paste the line referring to your mount into /etc/fstab, adding mount options "rw,user,noauto,exec".  It should look something like this:
```

# Encrypted SD
/media/<your_private_partition> /media/<your_partition> ecryptfs rw,user,noauto,exec,ecryptfs_sig=<your_sig>,ecryptfs_cipher=<your_cypher>,ecryptfs_key_bytes=<your_bytes>,ecryptfs_fnek_sig=<your_sig>,ecryptfs_unlink_sigs 0 0

```

3) Insert the following lines at the end your $HOME/.bashrc, substituting <your_partition> for where you encrypted mount is:
```


# Automount encrypted partition.
MPOINT=/media/<your_partition>
mount | grep -q "${MPOINT} type ecryptfs"
if [ $? -ne 0 ]; then
    mount -i "${MPOINT}"
fi

```

That's it!

---

