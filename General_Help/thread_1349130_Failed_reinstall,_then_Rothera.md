---
title: "Failed reinstall, then Rothera?"
date: 2009-12-07
forum: General Help
---

### Post by liddell on 2009-12-07
Hello folks, I have been trying to figure a series of issues out for a while now, but I'm stuck here - 
I was reinstalling Kubuntu with my only disk, the 9.10RC, and it failed the install with numerous attempts at 57% citing "too many symbolic links". Whatever that is, is not really an issue as the few files I needed re-written/repaired had been gone through and I am now once again able to boot. Yet alas, strangely, when I am taken to the login screen it displays my user name correctly but the computer has mysteriously been renamed 'rothera'. I assure you, I have never entered that word into that machine and her name before this was 'daisy'. The real issue now, is that when I attempt to login to my only user account - 'liddell' I am told the password is incorrect. The case is the same for 'root'.
What is this Rothera, some form of transitional install name? And how do I log into it?
I appreciate any assistance or elucidation anybody might be able to give,
-Liddell

[ a few notes: 
If I click on the 'power' looking icon that gives the restart x server/shutdown options and go to the 'switch user' the only option is 'unused'.
Also, I checked the integrity of the disk and it checks out. 
Also the failed install was being done over my old install without any partition changes.
I'm guessing the failed install did not finish my user accounts setup, so is there perhaps a way to access the system with say, a LiveCD, and edit something to add a user on the non-liveCD install on the hard drive?
If this is possible, I may be able to log in proper to this 'Rothera' that has no users. ]

---

### Post by snova on 2009-12-08
> **liddell said:**
> I was reinstalling Kubuntu with my only disk, the 9.10RC, and it failed the install with numerous attempts at 57% citing "too many symbolic links".

That's an odd error.

> Whatever that is, is not really an issue as the few files I needed re-written/repaired had been gone through and I am now once again able to boot.

That seems like a recipe for instability, but if it works...

> Yet alas, strangely, when I am taken to the login screen it displays my user name correctly but the computer has mysteriously been renamed 'rothera'. I assure you, I have never entered that word into that machine and her name before this was 'daisy'. The real issue now, is that when I attempt to login to my only user account - 'liddell' I am told the password is incorrect. The case is the same for 'root'.
What is this Rothera, some form of transitional install name? And how do I log into it?

I can only speculate on how that happened. "rothera" happens to be the name of one of Launchpad's build servers, which probably has something to do with it, though I can't imagine any good reason for that to somehow be your hostname.

> I'm guessing the failed install did not finish my user accounts setup, so is there perhaps a way to access the system with say, a LiveCD, and edit something to add a user on the non-liveCD install on the hard drive?

This is probably fixable, though I have some concerns over the integrity of your system with one-and-a-half installs. :)

First I would like to check that your username still exists. If your password is no longer valid the user probably does not exist anymore. Could you post the contents of  /etc/passwd (there are no passwords here, only usernames) from a live CD?

If it is the case that a user must be recreated, there are instructions for similar repairs [here]("https://help.ubuntu.com/community/LiveCdRecovery"), so it is possible to do so from a live CD. Adding a new user is hopefully a similar task:

```

sudo mount /dev/sda1 /mnt
sudo chroot /mnt
adduser liddell
```

(sda1 might not be the right partition, but it has to be the new / partition)

Then, to give the user administration permission:

```
adduser liddell admin
```

That might not be everything necessary to restore it to the way it was, but I think it will let you log in.

---

### Post by klausner on 2009-12-13
I just had the same problem. Screwed up Ubuntu 9.10 install, then the system thinks its named "rothera".

---

### Post by liddell on 2009-12-13
What Snova recommended worked for me - I could log on to my system, but much was broken. After fixing thread after thread of dysfunctional things, I decided to just back stuff up and do a clean install.
[I forgot to thank you for that. Thank you, Snova!]

---

### Post by klausner on 2009-12-13
> **liddell said:**
> What Snova recommended worked for me - I could log on to my system, but much was broken. After fixing thread after thread of dysfunctional things, I decided to just back stuff up and do a clean install.
[I forgot to thank you for that. Thank you, Snova!]

Unfortunately, a re-install did ***not*** work for me. See [this thread]("http://ubuntuforums.org/showthread.php?t=1353645"). :(

---

