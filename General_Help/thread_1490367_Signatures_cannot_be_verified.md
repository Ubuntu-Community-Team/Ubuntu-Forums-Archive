---
title: "Signatures cannot be verified"
date: 2010-05-22
forum: General Help
---

### Post by CheekyCheeze on 2010-05-22
I'm trying to update Karmic to Lucid. 
I try to update Karmic to the most recent update before I upgrade I get this error.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

Can you please help.

Thanks :)

---

### Post by DeadlyOats on 2010-05-22
I'm having the same problem with this issue too, but with a different repository.

[COLOR="Red"]W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783[/COLOR]

I tried doing this:

[COLOR="Red"]wget -q [http://packages.medibuntu.org](http://packages.medibuntu.org) -O- | sudo apt-key add -[/COLOR]

But I got this as a result:

[COLOR="Red"]gpg: no valid OpenPGP data found.[/COLOR]

I'm using Ubuntu 9.10.  I'm not trying to upgrade to 10.04.

How can this issue be resolved?

---

### Post by bashphoenux on 2010-05-22
^it should be 
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

or go [here]("http://packages.medibuntu.org/lucid/medibuntu-keyring.html")

---

### Post by DeadlyOats on 2010-05-23
bashphoenux, that's what I needed to do.  It worked.  Thanks very much.

Then does that mean, that for CheekyCheeze's problem, he should do this?

[COLOR="Red"]wget -q [http://ppa.launchpad.net/launchpad-key.gpg](http://ppa.launchpad.net/launchpad-key.gpg) -O- | sudo apt-key add -[/COLOR]

Or would his solution be different?  That's just a raw guess....

I ask, because this is his thread, originally, and he hasn't gotten a solution to his problem, yet....

Thanks again.

---

### Post by albinootje on 2010-05-23
> **CheekyCheeze said:**
> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0


Here's an answer :
[https://answers.launchpad.net/ubuntu/+question/106357](https://answers.launchpad.net/ubuntu/+question/106357)

---

