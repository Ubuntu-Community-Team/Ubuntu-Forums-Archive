---
title: "NFS with verification by SSH"
date: 2012-07-11
forum: General Help
---

### Post by yuanzhoulu on 2012-07-11
So, I want to create a high-speed file server link between 2 computers across a campus. It has to go over WAN. Data privacy is not a huge concern, so I'm not concerned so much about people snooping my data, but I don't want bot intruders deleting all my files or anything like that.

I have gigabit links on both ends.

SSHFS is too slow.

CIFS/SMB is fast but supposedly insecure and everyone says I shouldn't run it on a WAN but nobody says why.

NFSv3 is damn insecure because someone can just spoof my IP.

NFSv3 over SSH is slow.

NFSv4 is mind-boggling and it can't accept a simple key-based or password-based auth scheme.

FTPFS has its own issues (msktemp failing, etc.)

So here's my proposal ...

I use NFSv3, but a *parallel* SSH connection using SSH keys in reverse to verify that the host is genuine and not spoofed. It goes like this:
- Client requests to connect to NFS share.
- Server tries to initiate SSH connection to client using SSH keys.
- If the SSH connection succeeds, the connection is kept up, and NFS is allowed to proceed as normal (NOT tunnelled)
- If the SSH connection disconnects or fails, the NFS connection should cut off immediately before any bad stuff is done.

1. Does this sound like a super-bad idea?

2. What's the best way to implement the NFS connection cutting off?

Alternatively, is there some kind of offbeat firewall package that I can install that will block ports UNLESS an SSH connection from firewall to the client succeeds?

---

### Post by SeijiSensei on 2012-07-11
How about setting up an OpenVPN tunnel between the two machines?  See this [HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for details.

Used with its default blowfish algorithm for encryption OpenVPN is very fast.

---

### Post by CharlesA on 2012-07-11
> **SeijiSensei said:**
> How about setting up an OpenVPN tunnel between the two machines?  See this [HOWTO]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") for details.

Used with its default blowfish algorithm for encryption OpenVPN is very fast.
That would be the best way to do it. Easier to manage too.

---

