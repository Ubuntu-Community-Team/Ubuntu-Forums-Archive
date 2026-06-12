---
title: "network 3 or more linux machines together not using SAMBA"
date: 2010-11-01
forum: General Help
---

### Post by Vigh on 2010-11-01
Hi, i've been trying to network my machines together, 3 to be exact, without using SAMBA, as there is no point using SAMBA as there are no windows machines on the network at all, have tried using the standard network admin GUI's and following some guides, without success, what is the step by step procedure for creating network shares linux-linux only networking, regards

Ant

---

### Post by HermanAB on 2010-11-02
Howdy,

Use NFS.  NFS is so simple you won't believe the howto guides.  There is only one line to configure for the server and one line for each client:

[http://www.aeronetworks.ca/howtos/nfs-howto.html](http://www.aeronetworks.ca/howtos/nfs-howto.html)

---

### Post by Vigh on 2010-12-19
still having trouble on finding a simple way to network my computers together, also anyone got any experience with VPN remote access to other computers via the internet

---

### Post by KeyserSoze93 on 2010-12-19
> **Vigh said:**
> still having trouble on finding a simple way to network my computers together, also anyone got any experience with VPN remote access to other computers via the internet

I'm not sure what your problem was with NFS as HermanAB suggested. Either use Samba or NFS, they are the industry standard for mixed/Windows and Linux/UNIX networks respectively.

I personally use both. NFS has pros and cons since the UID/GIDs of the users must tie up across machines, hence it is often paired with NIS for network-wide user accounts.

Samba, on the other hand, supports highly configurable mapping of user accounts and groups so it's more suitable for an ad-hoc network where authentication is done on the fly.

---

### Post by tredegar on 2010-12-19
> still having trouble on finding a simple way to network my computers together,
Are they all on the same LAN?

If so, **nfs** is really easy, see HermanAB's post above.

If you are connecting over the internet, **nfs**, on its own is not secure, and you'll need to use **ssh** or **sshfs** and open a port in your firewall. If you are going to do this, please read up on the security implications of running a **ssh** server.

I like to use **ssh** (even over my secure LAN, as it keeps me in practice) and **sftp://username@hostname** in nautilus makes for easy drag & drop between computers.

 I have set up public / private key based authentication, so my connections are secure, and I do not have to enter a password. I just click on the host I want, and the files are there.

Some links for you:

[Public /private keys]("http://www.linuxconfig.org/Passwordless_ssh")
[sshfs]("http://www.linuxjournal.com/article/8904")
[Setting up a VPN]("http://www.faqs.org/docs/Linux-HOWTO/VPN-HOWTO.html")

---

### Post by blueridgedog on 2010-12-19
What have you tried?

---

