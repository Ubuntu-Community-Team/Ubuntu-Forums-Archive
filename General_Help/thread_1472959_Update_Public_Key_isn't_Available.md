---
title: "Update Public Key isn't Available"
date: 2010-05-04
forum: General Help
---

### Post by Xorlathor on 2010-05-04
The public key isn't available when I try to use the Update Manager; clicking the "Check" button results in a popup with the following text:

```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
```

I tried adding the public key via:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6E871C4A881574DED

```

Is that the right code to enter? Because when I did that it didn't fix the problem. Any solutions?

---

### Post by sisco311 on 2010-05-04
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 881574DE
sudo apt-get update
```
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

---

### Post by Xorlathor on 2010-05-05
> **sisco311 said:**
> ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 881574DE
sudo apt-get update
```
[https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

The code worked, problem solved. Thanks for your help!

---

### Post by sisco311 on 2010-05-05
> **Xorlathor said:**
> The code worked, problem solved. Thanks for your help!

You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

### Post by phubert28 on 2010-07-07
O.K. I tried the code below and at the end of the process was still getting:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F

How can I tell what is CAUSING this????

---

### Post by sisco311 on 2010-07-08
> **phubert28 said:**
> O.K. I tried the code below and at the end of the process was still getting:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D739676F7613768D
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9BDB3D89CE49EC21
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A6DCF7707EBC211F

How can I tell what is CAUSING this????

Every repository has a unique public key. When you add a new repository you have to add its public key to the list of trusted keys. For more information see the link from my first post.

You have to run:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CE49EC21
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7EBC211F

```in order to add the public keys of your ppa repositories to the list of trusted keys.

---

### Post by Dr.grUDgE on 2011-01-29
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE

I am getting this error and can't figure it out...
Will be glad if someone can help, thanks in advance 8-[

---

### Post by phubert28 on 2011-01-29
Look at the answer below  by sisco311 and I think you will have your solution.

I believe you will have to use:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 881574DE

---

### Post by Dr.grUDgE on 2011-01-29
ok... it doesn't matter anymore, I upgraded my ubuntu to 10.10 using an alternate install iso. Thanks neways for the reply though :)

---

### Post by jayateertha on 2012-04-04
> **sisco311 said:**
> Every repository has a unique public key. When you add a new repository you have to add its public key to the list of trusted keys. For more information see the link from my first post.

You have to run:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com CE49EC21
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7EBC211F

```in order to add the public keys of your ppa repositories to the list of trusted keys.



ThankYou its worked for me...

---

### Post by horsemanoffaith on 2012-12-01
Thanks for your post sisco311. This cleared my problem!!!:)

---

### Post by howefield on 2012-12-01
Old thread closed.

---

