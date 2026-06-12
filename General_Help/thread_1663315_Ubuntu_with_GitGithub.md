---
title: "Ubuntu with Git/Github"
date: 2011-01-09
forum: General Help
---

### Post by AlexBaranosky on 2011-01-09
I'm having trouble setting up Github on Ubuntu.  I've used Github plenty on windows so I'm pretty sure this is an Ubuntu thing, probably something simple since I'm a newbie with Ubuntu.

I follow the instructions for setting up ssh keys here:  
[http://help.github.com/linux-key-setup/](http://help.github.com/linux-key-setup/)

When I get to the end I do ssh -v [EMAIL="git@github.com"]git@github.com[/EMAIL] and get:```

alex@ubuntu:~/proj$ ssh -v git@github.com
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to github.com [207.97.227.239] port 22.
debug1: Connection established.
debug1: identity file /home/alex/.ssh/identity type -1
debug1: identity file /home/alex/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/alex/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-5github2
debug1: match: OpenSSH_5.1p1 Debian-5github2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'github.com' is known and matches the RSA host key.
debug1: Found key in /home/alex/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/alex/.ssh/id_rsa
debug1: Remote: Forced command: gerve AlexBaranosky
debug1: Remote: Port forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Agent forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Server accepts key: pkalg ssh-rsa blen 277
debug1: Remote: Forced command: gerve AlexBaranosky
debug1: Remote: Port forwarding disabled.
debug1: Remote: X11 forwarding disabled.
debug1: Remote: Agent forwarding disabled.
debug1: Remote: Pty allocation disabled.
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.utf8
PTY allocation request failed on channel 0
Hi AlexBaranosky! You've successfully authenticated, but GitHub does not provide shell access.
              debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug1: client_input_channel_req: channel 0 rtype eow@openssh.com reply 0
debug1: channel 0: free: client-session, nchannels 1
Connection to github.com closed.
Transferred: sent 2592, received 2904 bytes, in 0.1 seconds
Bytes per second: sent 44942.9, received 50352.7debug1: Exit status 1
```Seems fine.

Then I go to clone a repo, like I would do on Windows.  I go to the folder I keep all of my projects, and type:
```
git clone git@github.com:AlexBaranosky/Sportello.git
```On Windows this would create the Sportello folder and fill it with the content of my repo.

On Ubuntu, instead, I am receiving this error response:
```
fatal: could not create work tree dir 'Sportello'.: Permission denied
```What am I missing in using git on Ubuntu?  Is it a permissions thing?

Thanks for your help in advance. 

Alex

SOLUTION:

```
rm -rf ~/proj

mkdir ~/proj

git clone git@github.com:AlexBaranosky/Sportello.git
```

---

