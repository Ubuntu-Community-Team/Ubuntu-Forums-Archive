---
title: "CRON an rsync command"
date: 2011-04-08
forum: General Help
---

### Post by ondemanddesign on 2011-04-08
I am setting up a backup plan for the business I am at. I am having an issue where when I run an rsync command I am prompted for a password to sudo. This is all fine and dandy, but how do I get the CRON to insert the password, additionally, is this a security issue if I have CRON running sudo commands? Is there another way I should handle this? Thanks.

---

### Post by sanguinoso on 2011-04-08
Put them in the root users crontab instead. ```
sudo crontab -e
```

---

### Post by ondemanddesign on 2011-04-08
Great, but rsync also prompts for a password, how do I tell it to process that?

---

### Post by blind2314 on 2011-04-08
If it's in root's cron that shouldn't happen...what flags are you giving rsync?

---

### Post by ondemanddesign on 2011-04-08
I am sending files from one server over the internet to another server, the user profile on the other server is password secured so rsync prompts for that password.

```
sudo rsync -acv /var/www backups@[IP_ADDRESS}:/home/backups/ubuntuProduction
```

---

### Post by CharlesA on 2011-04-08
Ah.

You'd need to create a passphrase-less key for it to not prompt for the password of the remote machine.

Run this to create a keypair:

```
ssh-keygen
```

Then use this to transfer it to the remote machine:

```
ssh-copy-id user@remotehost
```

---

### Post by ondemanddesign on 2011-04-15
> **CharlesA said:**
> Ah.

You'd need to create a passphrase-less key for it to not prompt for the password of the remote machine.

Run this to create a keypair:

```
ssh-keygen
```

Then use this to transfer it to the remote machine:

```
ssh-copy-id user@remotehost
```

Awesome, now does this create a security loophole since no password is required? I assume not as the connection is only trusted if both servers have their respective passphrase-less key.

---

### Post by CharlesA on 2011-04-15
It depends. I'd use the "force" command to only allow that key to run rsync.

[http://binblog.info/2008/10/20/openssh-going-flexible-with-forced-commands/](http://binblog.info/2008/10/20/openssh-going-flexible-with-forced-commands/)

---

