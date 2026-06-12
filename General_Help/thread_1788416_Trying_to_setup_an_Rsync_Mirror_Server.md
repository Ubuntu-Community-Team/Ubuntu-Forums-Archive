---
title: "Trying to setup an Rsync Mirror Server"
date: 2011-06-22
forum: General Help
---

### Post by dudemanbubba on 2011-06-22
I am trying to setup a secondary machine in our office to simply maintain a complete up to date copy of all of our data files.

I followed the tutorial in this link to the T:  [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

I can not seem to get the system to allow this to happen without entering the password manually.  There were some messages at the end of this tutorial that people had a similar issue that was resolved with some basic syntax in the authorized_keys file.  I have tweaked that everyway possible with no success.

When I run the rsyc command in verbose mode, it gives the following output:

```
administrator@BS1:~$ sudo rsync -avz --delete --exclude=**/stats --exclude=**/error --exclude=**/files/pictures -e "ssh -v -i /root/rsync/mirror-rsync-key" bserver@LS1:/var/www/ /var/www/
OpenSSH_5.3p1 Debian-3ubuntu6, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to LS1 [192.168.0.103] port 22.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/rsync/mirror-rsync-key type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH_4*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu6
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'ls1' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:3
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Offering public key: /root/rsync/mirror-rsync-key
debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: password
bserver@ls1's password:
debug1: Authentication succeeded (password).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
debug1: Sending command: rsync --server --sender -vlogDtprze.iLsf . /var/www/
receiving file list ... done

sent 71 bytes  received 86 bytes  62.80 bytes/sec
total size is 45  speedup is 0.29
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: channel 0: free: client-session, nchannels 1
debug1: fd 0 clearing O_NONBLOCK
debug1: fd 1 clearing O_NONBLOCK
Transferred: sent 2272, received 2248 bytes, in 0.0 seconds
Bytes per second: sent 253938.5, received 251256.1
debug1: Exit status 0
administrator@BS1:~$

```

I am a noob... so bear with me.  Any help is greatly appreciated!

---

