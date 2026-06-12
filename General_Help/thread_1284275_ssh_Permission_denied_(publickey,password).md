---
title: "ssh Permission denied (publickey,password)"
date: 2009-10-06
forum: General Help
---

### Post by destine on 2009-10-06
Heya,

I hope this is the right place for this post!

I have set up a ssh server on my computer which is running Ubuntu Jaunty 64.
I can ssh to from my laptop locally without any issues. My laptop has ubuntu Jaunty 32.

When i try to connect to my internet address i get the following response:
(name and ip's changed for security)

ssh me@netip port
me@netip's password: 
Permission denied, please try again.
me@netip's password: 
Permission denied, please try again.
me@netip's password: 
Permission denied (publickey,password).

The connection i'm comming from is the wireless at a university. I know that ssh does work through the wireless because i can connect to other servers without an issue.

Both my home computer and laptop have new installations on them.

To make sure that my home computer is set up right i tried connection through a desktop xp pc at work using putty - this works without an issue.

Im using a direct ethernet dsl to connect to the internet and have had my isp forward the ports correctly to my computer.

I also have a sql on the same home computer and it seems to be the samething happening. 

Can anyone help??

---

### Post by CharlesA on 2009-10-06
Has anything changed since it last worked? I had a similar problem, except it was denying my key from another local machine, and not across the internet. I could login with the password just fine.

Just to be clear, you are trying to ssh to your laptop or to yer desktop?

---

### Post by destine on 2009-10-06
I set up everything, connected and it all worked as i wanted (localy).
Shut-down laptop head to work, try to login- fail.

---

### Post by CharlesA on 2009-10-06
It connects to the ssh server but cannot authenticate. I'm not quite sure what could cause that. Sounds like the server doesn't like the password/key that is being sent. Could it be getting scrambled somehow?

---

### Post by destine on 2009-10-06
I'm not sure. i have a shell account on a server in hungary( i think, its ".hu")  and i have the same problem connecting from there. 

The exact network path from work is:

Wireless-> vpn -> isp-router -> home-pc.
Im not using the keys, just a password.

---

### Post by Giblet5 on 2009-10-06
Step 1 in any SSH issue is to invoke the command with "-vvv" (the more 'v's, the more verbose).

---

### Post by destine on 2009-10-06
> **Giblet5 said:**
> Step 1 in any SSH issue is to invoke the command with "-vvv" (the more 'v's, the more verbose).


Ok did that but is seems i had the same problem.
here is what i got
```

Laptop_username@Laptop_username:~$ ssh -vvv home_username@net_ip port
OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to net_ip [net_ip] port 22.
debug1: Connection established.
debug1: identity file /home/Laptop_username/.ssh/identity type -1
debug1: identity file /home/Laptop_username/.ssh/id_rsa type -1
debug1: identity file /home/Laptop_username/.ssh/id_dsa type -1
debug1: Remote protocol version 1.99, remote software version OpenSSH_2.3.0_Mikrotik_v2.9
debug1: match: OpenSSH_2.3.0_Mikrotik_v2.9 pat OpenSSH_2.3.0*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-5ubuntu1
debug2: fd 3 setting O_NONBLOCK
debug2: Original cipher proposal: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: Compat cipher proposal: 3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,rijndael-cbc@lysator.liu.se
debug2: Original cipher proposal: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: Compat cipher proposal: 3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,rijndael-cbc@lysator.liu.se
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: 3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: 3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-dss
debug2: kex_parse_kexinit: 3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes128-cbc,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rijndael256-cbc,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: 3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes128-cbc,aes192-cbc,aes256-cbc,rijndael128-cbc,rijndael192-cbc,rijndael256-cbc,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5,hmac-ripemd160@openssh.com
debug2: kex_parse_kexinit: hmac-sha1,hmac-md5,hmac-ripemd160@openssh.com
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit: none,zlib
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client 3des-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server 3des-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST_OLD(2048) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 192/384
debug2: bits set: 517/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/Laptop_username/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 7
debug1: Host 'net_ip' is known and matches the DSA host key.
debug1: Found key in /home/Laptop_username/.ssh/known_hosts:7
debug2: bits set: 517/1024
debug1: ssh_dss_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/Laptop_username/.ssh/identity ((nil))
debug2: key: /home/Laptop_username/.ssh/id_rsa ((nil))
debug2: key: /home/Laptop_username/.ssh/id_dsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/Laptop_username/.ssh/identity
debug3: no such identity: /home/Laptop_username/.ssh/identity
debug1: Trying private key: /home/Laptop_username/.ssh/id_rsa
debug3: no such identity: /home/Laptop_username/.ssh/id_rsa
debug1: Trying private key: /home/Laptop_username/.ssh/id_dsa
debug3: no such identity: /home/Laptop_username/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
home_username@net_ip's password:
debug3: packet_send2: adding 56 (len 63 padlen 9 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
home_username@net_ip's password:
debug3: packet_send2: adding 56 (len 63 padlen 9 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
Permission denied, please try again.
home_username@net_ip's password:
debug3: packet_send2: adding 56 (len 62 padlen 10 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,password).

```

---

### Post by Giblet5 on 2009-10-06
It doesn't like any of the keys and it doesn't like the password.

Let's eliminate the VPN or router fragmentation that can easily hose up an ssh session.

Make sure you have openssh-server installed locally.

Install your public key in your local .ssh directory and ```
ssh `hostname`
```

Does that work?

If not, you haven't gen'ed/installed your keys properly.

Fix that, then copy all of your local .ssh folder to the remote (except the known_hosts file), and you should be able to ssh back and forth at will.

---

### Post by destine on 2009-10-06
[quote=Giblet5;8062534]

Install your public key in your local .ssh directory and ```
ssh `hostname`
```

Okay, i have installed openssh-server locally. 
Could you explain the public keys steps in a bit more detail as i am still relatively new to ssh.
Or are the keys generated automatically on install??

Thanks

---

### Post by Giblet5 on 2009-10-06
Here's [a really good HOWTO]("http://ubuntuforums.org/archive/index.php/t-30709.html") that describes the process.

Go through that and test against your local system via ```
ssh `hostname`
``` and you'll be a pro in less than an hour.

---

### Post by destine on 2009-10-06
Okay,

Done with the guide. 

ahd to bounce the file through another sever before it got to my home pc since i cannot ssh to it from my laptop at all.


"ssh localhost" on the home pc worked fine but now when i try for my laptop it does nothing. 

with "-vv" it says its connecting but does nothing.

I findng it strange how i can connect to the server using putty on xp easily but not being able to do it from my laptop. 

Would this have anything to do with the fact that i first connected the latop to the home pc on the local network??

---

### Post by destine on 2009-10-06
Leaving it to do its thing it just "connection Time Outs"

---

### Post by needhelp1 on 2009-10-07
Hi there; don't know if this really help you, BUT ...I runned on the same problem after not using ssh for a while and basically forgeting something when trying to ssh to my server; I am posting here because I received the same error:

So, in my case when I try to connect I used:

**ssh 6900:IP_of_myserver:5900 mydomain.com**

after connecting the password was requested; I inserted the password and received the error message permission denied, please try again; Permission denied ( publickey, password ); what I realized after few shots is that ......I have 2 different users on those machines: **USER_1 on the client and USER_2 on the server**;
So when I use the "ssh 6900:IP_of_myserver:5900 mydomain.com" USER_1 (FROM THE CLIENT PC ) is trying to connect to the server; of course, USER_1 has no account on this machine so that's why the connection is refused; so instead of this I had to use:

[B]ssh 6900:IP_of_myserver:5900 [email]USER_2@mydomain.com[/email],
[/B]
Then inserting the proper password for USER_2 and everything went fine afterwords.....

---

### Post by DeBOBAHer on 2009-10-07
I using a little another syntax:
ssh hostname **-l** user_on_remote_comp_name

---

### Post by destine on 2009-10-07
> **needhelp1 said:**
> 

**ssh 6900:IP_of_myserver:5900 mydomain.com**

[B]ssh 6900:IP_of_myserver:5900 [EMAIL="USER_2@mydomain.com"]USER_2@mydomain.com[/EMAIL],
[/B]


Hi,

the syntax I'm using is:

ssh user@net_ip port

the user is the user-name that i use on my home pc.

could explain what your command is doing with the 6900 port, also is "**IP_of_myserver"  **the internet ip that you use or is it internal. 

if I understand correctly then my command could look something like: ssh 6900:internal_ip:5900 user@net_ip

I have a direct Ethernet connection but don't have control over the local network. Its a student village network. We connect to the net by logging in through a browser. 

Thanks

---

### Post by destine on 2009-10-07
> **DeBOBAHer said:**
> I using a little another syntax:
ssh hostname **-l** user_on_remote_comp_name


Ill be back at work tonight where I will try this syntax

thanks

---

### Post by needhelp1 on 2009-10-07
> **destine said:**
> Hi,

the syntax I'm using is:

ssh user@net_ip port

the user is the user-name that i use on my home pc.

could explain what your command is doing with the 6900 port, also is "**IP_of_myserver"  **the internet ip that you use or is it internal. 

if I understand correctly then my command could look something like: ssh 6900:internal_ip:5900 user@net_ip

I have a direct Ethernet connection but don't have control over the local network. Its a student village network. We connect to the net by logging in through a browser. 

Thanks

Hi there again;

The command i'm using is based on the syntax of ssh combined with a desktop remote access program like vnc or freeNX ;
What I am doing with this command is to obtain a secure tunnel over a remote desktop which is not so secure;

[B]ssh 6900:IP_of_SERVER(PUBLIC static or dynamic IP):5900 mydomain.com
[/B]In plain words this will means .....make a secure shell on port 6900 of my local machine with everything you find out to be running on port 5900 of my server from back home 

  Anyway I saw the same problem when googling on another post....; the solution there for the guy facing the same problem was to re-install ssh, therefore reset the public keys and password; then it worked; otherwise you shoul check where the ssh have some files ....in our case I think this is /etc/ssh and edit the ssh_config files .......

---

### Post by destine on 2009-10-07
> **needhelp1 said:**
> Hi there again;

The command i'm using is based on the syntax of ssh combined with a desktop remote access program like vnc or freeNX ;
What I am doing with this command is to obtain a secure tunnel over a remote desktop which is not so secure;

[B]ssh 6900:IP_of_SERVER(PUBLIC static or dynamic IP):5900 mydomain.com
[/B]In plain words this will means .....make a secure shell on port 6900 of my local machine with everything you find out to be running on port 5900 of my server from back home 

  Anyway I saw the same problem when googling on another post....; the solution there for the guy facing the same problem was to re-install ssh, therefore reset the public keys and password; then it worked; otherwise you should check where the ssh have some files ....in our case I think this is /etc/ssh and edit the ssh_config files .......

I'm using tightvnc for remote desktop at home and that uses ports 5901 and 5902. but connecting directly to that is insecure. Instead i want to send my connection through an ssh tunnel. 

It works on windows with a couple of glitches, i.e. the keyboard is mismapped. if i can jsut get my laptop to ssh successfully then im home free.

At home i connected my laptop to my switch, ssh'd in using the keys and passphrase, it worked perfectly. 

The server and my laptop both have new instalations of ubuntu Jaunty on them. the only changes that i have made to the ssh is what is decribed in this forum. 

Thanks

---

### Post by CharlesA on 2009-10-07
Have you tried a different machine, like one running windows and connect using Putty?

Just to see if you get the same issue.

---

### Post by destine on 2009-10-07
> **CharlesA said:**
> Have you tried a different machine, like one running windows and connect using Putty?

Just to see if you get the same issue.

Yup, the windows machine connect no problem, its seem to be only lunix. i have a shell acount on another linux server, run by a site im registered with. i have the same issue there. so i have just tried to use the keys. but now im getting a diferent response 

ssh homeueserid@net_ip port
ssh_exchange_identification: Connection closed by remote host

Now i just get a connection timeout on my laptop. 


Anotherthing i have just tried is to take the network cable from the windows machine and it static ip. put those into my laptop and try to ssh. but it just times out aswell.

All other ssh attempts to other server work fine whether by cable or wireless

---

### Post by destine on 2009-10-13
Heya,

Now i just get a connection time out. I ssh to another server the try to ssh again to my home pc. this is what i get
```
me@diff_remote_server:~$ ssh -vv me@net_ip port
OpenSSH_5.1p1 Debian-5, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to net_ip [net_ip] port 22.
debug1: Connection established.
debug1: identity file /home/destine/.ssh/identity type -1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/me/.ssh/id_rsa type -1
debug1: identity file /home/me/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

```


Would this be due to not having set up the keys for this remote server

---

