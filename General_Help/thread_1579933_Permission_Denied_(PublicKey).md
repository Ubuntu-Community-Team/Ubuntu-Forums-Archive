---
title: "Permission Denied (PublicKey)"
date: 2010-09-22
forum: General Help
---

### Post by Fynn on 2010-09-22
Hi,

Is it possible to SSH to a remote computer from within an SSH session?  I'm connecting to my home server via SSH, and trying to connect out to my VPS.

I know the key.ppk file works, as I can use it to connect directly from my PC.

The output I'm getting is shown below:

```
# ssh -i key.ppk -v -l myuser myuser@domain.co.uk

```

(tried various ways of doing this)

```
OpenSSH_4.6p1 Debian-5ubuntu0.1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to mydomain.co.uk [123.456.789.012] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file key.ppk type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-5ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.6p1 Debian-5ubuntu0.1
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'mydomain.co.uk' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:4
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: key.ppk
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key 'key.ppk':
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key 'key.ppk':
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
Enter passphrase for key 'key.ppk':
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: No more authentication methods to try.
Permission denied (publickey).

```

There's nothing I can see in the auth.log file on the VPS.

---

### Post by Jeroensum on 2010-09-22
Your current key.ppk is written in a format that only putty can handle. Go to [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and download the puttygen.exe, start the tool, then load your key, go to the conversions menu and export the key in OpenSSH format. When it's done, upload the key to the box you connect tot your VPS from and you should be ready to go :)

---

### Post by Fynn on 2010-09-23
> **Jeroensum said:**
> Your current key.ppk is written in a format that only putty can handle. Go to [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) and download the puttygen.exe, start the tool, then load your key, go to the conversions menu and export the key in OpenSSH format. When it's done, upload the key to the box you connect tot your VPS from and you should be ready to go :)

Fantastic. Thanks so much.

=D>

---

