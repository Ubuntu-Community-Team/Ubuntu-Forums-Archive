---
title: "can't set passwordless SSH"
date: 2009-11-20
forum: General Help
---

### Post by Eugene_Bondarenko on 2009-11-20
Please help, I really don't know what to do next. I went through this article
[http://swik.net/Ubuntu/Only+Ubuntu/How+to+Create+Passwordless+SSH+Private%2FPublic+Key+Pair+on+Ubuntu/b5t6e](http://swik.net/Ubuntu/Only+Ubuntu/How+to+Create+Passwordless+SSH+Private%2FPublic+Key+Pair+on+Ubuntu/b5t6e)
And here is the output I get
```

OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ip_goes_here [ip_goes_here] port 22.
debug1: Connection established.
debug1: identity file /home/eugene/.ssh/identity type -1
debug1: identity file /home/eugene/.ssh/id_rsa type -1
debug3: Not a RSA1 key file /home/eugene/.ssh/id_dsa.
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/eugene/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.1p1 Debian-3ubuntu1
debug1: match: OpenSSH_5.1p1 Debian-3ubuntu1 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.1p1 Debian-6ubuntu2
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 136/256
debug2: bits set: 507/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug3: check_host_in_hostfile: filename /home/eugene/.ssh/known_hosts
debug3: check_host_in_hostfile: match line 1
debug1: Host 'ip_goes_here' is known and matches the RSA host key.
debug1: Found key in /home/eugene/.ssh/known_hosts:1
debug2: bits set: 544/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/eugene/.ssh/id_dsa (0x4b7b88)
debug2: key: /home/eugene/.ssh/identity ((nil))
debug2: key: /home/eugene/.ssh/id_rsa ((nil))
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred gssapi-keyex,gssapi-with-mic,gssapi,publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/eugene/.ssh/id_dsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,password
debug1: Trying private key: /home/eugene/.ssh/identity
debug3: no such identity: /home/eugene/.ssh/identity
debug1: Trying private key: /home/eugene/.ssh/id_rsa
debug3: no such identity: /home/eugene/.ssh/id_rsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
eugene@ip_goes_here's password: 


```

---

### Post by bodhi.zazen on 2009-11-20
My guess is your key is bad or you did not transer the key to the server properly.

I suggest you start over. delete all the keys on the client and in the server.

Make a new key.

Transfer the key to the server with :

```
ssh-copy-id ~/.ssh/id_dsa user@server
```You can also use ssh agent whick keeps your ssh keys in RAM

Make a second key with a password, give it a different name, transfer it to the server with ssh-copy-id .

ssh-add ~/.ssh/second_key_name
enter your second key password.

You can now

ssh user@server without re-entering the password.

See also : [http://bodhizazen.net/Tutorials/ssh/](http://bodhizazen.net/Tutorials/ssh/)

---

### Post by Eugene_Bondarenko on 2009-11-20
Hi, and thanks for the help! I've cleaned all the previous keys from my local comp and from server and tried again but still no luck. Below is the output I get. Please let me know if you see any mistake there. I've verified server and authorized_keys file got created there.

```

eugene@eugene-desktop:~/.ssh$ ls -al
total 12
drwx------  2 eugene eugene 4096 2009-11-20 23:26 .
drwxr-xr-x 33 eugene eugene 4096 2009-11-20 23:12 ..
-rw-r--r--  1 eugene eugene  442 2009-11-20 01:09 known_hosts
eugene@eugene-desktop:~/.ssh$ ssh-keygen -t dsa
Generating public/private dsa key pair.
Enter file in which to save the key (/home/eugene/.ssh/id_dsa): 
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/eugene/.ssh/id_dsa.
Your public key has been saved in /home/eugene/.ssh/id_dsa.pub.
The key fingerprint is:
fingerprint_goes_here eugene@eugene-desktop
The key's randomart image is:
+--[ DSA 1024]----+
image goes here....
+-----------------+
eugene@eugene-desktop:~/.ssh$ ls -al
total 20
drwx------  2 eugene eugene 4096 2009-11-20 23:28 .
drwxr-xr-x 33 eugene eugene 4096 2009-11-20 23:29 ..
-rw-------  1 eugene eugene  668 2009-11-20 23:28 id_dsa
-rw-r--r--  1 eugene eugene  611 2009-11-20 23:28 id_dsa.pub
-rw-r--r--  1 eugene eugene  442 2009-11-20 01:09 known_hosts
eugene@eugene-desktop:~/.ssh$ ssh-copy-id -i ~/.ssh/id_dsa.pub eugene@server_ip_goes_here
eugene@server_ip_goes_here's password: 
Now try logging into the machine, with "ssh 'eugene@server_ip_goes_here'", and check in:

  .ssh/authorized_keys

to make sure we haven't added extra keys that you weren't expecting.

eugene@eugene-desktop:~/.ssh$ ssh-agent
SSH_AUTH_SOCK=/tmp/ssh-SiSoPl2721/agent.2721; export SSH_AUTH_SOCK;
SSH_AGENT_PID=2722; export SSH_AGENT_PID;
echo Agent pid 2722;
eugene@eugene-desktop:~/.ssh$ ssh-add ~/.ssh/id_dsa
Identity added: /home/eugene/.ssh/id_dsa (/home/eugene/.ssh/id_dsa)
eugene@eugene-desktop:~/.ssh$ ssh server_ip_goes_here
eugene@server_ip_goes_here's password: 

eugene@eugene-desktop:~/.ssh$ 


```

---

### Post by bodhi.zazen on 2009-11-20
the syntax of your ssh command is off

You need to use 

ssh user@server_ip_address

you have to use the same user as with the key :

> bodhi@Succubus:~$ ssh-add ./.ssh/key                                                      
Enter passphrase for ./.ssh/key:
Identity added: ./.ssh/key (./.ssh/key)

[COLOR=red]#This fails[/COLOR]
bodhi@Succubus:~$ ssh server_ip
Empty Moon ...

   ~ Dragon Abyss

Permission denied (publickey).

[COLOR=blue]#This works[/COLOR]
bodhi@Succubus:~$ ssh bodhi@server_ip_address

Second, you do not need ssh agent with an empty(passwordless) key.

I am suggesting you use a key with a password, then use ssh-agent to enter the password only once, when you add the key with ssh-add.

If you are running a default Ubuntu install , with X, you do not nee dto manually start ssh-agent.

If you are not running X and wish to use ssh-agent use```
ssh-agent bash
``` which starts a new shell.

---

### Post by Eugene_Bondarenko on 2009-11-20
ssh user@server_ip_address
fails too :(

yes, I run the default Ubuntu I got from here
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Well, in reality I'd like to have it totally passwordless. Just like I had in windows. My SVN client was using putty there and I had a password flag hardcoded into putty. However if non-blank passphrase is the only way to set this whole thing, I guess I'll then need to write a cron script that access ssh-add and enters a hardcoded password...which is a weird way of doing things :)

---

### Post by bodhi.zazen on 2009-11-20
Can you show the output of 

ssh -i ~./.ssh/id_rsa eugene@server_ip_address

you know you need to both sepcify a key with the -i (if not  using ssh-agent) and change "user" to your log in user ?

---

### Post by Eugene_Bondarenko on 2009-11-20
yeah, sure, I changed user to eugene :)

I am using dsa so I changed rsa to dsa. Also ~./ throws error so I went ahead and changed this too. Here it goes:

```

eugene@eugene-desktop:~/.ssh$ ls -la
total 20
drwx------  2 eugene eugene 4096 2009-11-20 23:28 .
drwxr-xr-x 33 eugene eugene 4096 2009-11-21 00:18 ..
-rw-------  1 eugene eugene  668 2009-11-20 23:28 id_dsa
-rw-r--r--  1 eugene eugene  611 2009-11-20 23:28 id_dsa.pub
-rw-r--r--  1 eugene eugene  442 2009-11-20 01:09 known_hosts
eugene@eugene-desktop:~/.ssh$ ssh -i ~./.ssh/id_dsa eugene@server_ip
Warning: Identity file ~./.ssh/id_dsa not accessible: No such file or directory.
eugene@server_ip's password: 

eugene@eugene-desktop:~/.ssh$ ssh -i ~/.ssh/id_dsa eugene@server_ip
eugene@server_ip's password:

```

Should I clean everything up and try rsa instead?

---

### Post by bodhi.zazen on 2009-11-20
No, time to look server side I think.

ssh in

look in your ~/.ssh , do you see your key in authorized_keys ?

look at /etc/ssh/sshd_config

Is the server looking in the correct place for keys ?

---

### Post by sedawk on 2009-11-20
You can try the same but only on the local machine, so you
enable ssh eugene@localhost without password.

Then you can check from verbose output if there are any
lines different between output of "ssh ... eugene@localhost"
and "ssh ...eugene@other_machine".

---

### Post by Eugene_Bondarenko on 2009-11-20
> **bodhi.zazen said:**
> No, time to look server side I think.

ssh in

look in your ~/.ssh , do you see your key in authorized_keys ?

look at /etc/ssh/sshd_config

Is the server looking in the correct place for keys ?
Yes, authorized_keys does exist. Also here are the lines from the conf file:

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

Should I uncomment that line? I've checked my local conf file and it has that line commented too but I can't sign in to eugene@localhost


> **sedawk said:**
> You can try the same but only on the local machine, so you
enable ssh eugene@localhost without password.

Then you can check from verbose output if there are any
lines different between output of "ssh ... eugene@localhost"
and "ssh ...eugene@other_machine".
I copied mine id_dsa.pub to authorized_keys and yeah, I successfully logged in to eugene@localhost :) I'll be trying to find the different between localhost and server outputs now.

---

### Post by bodhi.zazen on 2009-11-20
I would uncomment that line :

#AuthorizedKeysFile %h/.ssh/authorized_keys

and restart the ssh server

What OS is running on the server ?

---

### Post by Eugene_Bondarenko on 2009-11-23
Hi, I've uncommented that line, restarted server but still no luck. Is there some place on the server where I can check the log of what happens from server point of view (just like -vvv lets me see what happens with authentication from my side).

The server is ubuntu 8.10.

---

### Post by memilanuk on 2009-11-23
here's a link to a tutorial that helped me out greatly with getting ssh keys to work between my clients (Windows PC, Macbook) and my Ubuntu 8.04 LTS server...  maybe it'll help you.

[http://www.andremolnar.com/how_to_set_up_ssh_keys_with_putty_and_not_get_server_refused_our_key]("http://www.andremolnar.com/how_to_set_up_ssh_keys_with_putty_and_not_get_server_refused_our_key")

---

### Post by Eugene_Bondarenko on 2009-12-01
...in the end I found out that my /home/eugene/ folder was 777 and that was the root of the problem. ](*,) I really don't know how this happened since I knew that home folder should have 751 permissions and I was sure I cheked this. Sorry for causing all these troubles

---

