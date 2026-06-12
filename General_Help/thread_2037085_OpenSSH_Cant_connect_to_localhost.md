---
title: "OpenSSH Cant connect to localhost"
date: 2012-08-03
forum: General Help
---

### Post by Nicky.. on 2012-08-03
Having a problem with OpenSSH for some reason i can not connect to localhost on port 22 using Terminal but i suspect that i might be able to connect remotely as i done that last night cant check that out at the moment.


username@BedRoomPC:/etc/ssh$ ssh -vvv localhost
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to localhost [127.0.0.1] port 22.
debug1: connect to address 127.0.0.1 port 22: Connection refused
ssh: connect to host localhost port 22: Connection refused

so restarted

username@BedRoomPC:/etc/ssh$ sudo service ssh restart
ssh stop/waiting
ssh start/running, process 15358

then checked
username@BedRoomPC:/etc/ssh$ ps aux | grep -i ssh
username     1764  0.0  0.0   4060    24 ?        Ss   Jul27   0:02 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session --session=ubuntu
root     15358  0.0  0.1   6664  2376 ?        Ss   19:07   0:00 /usr/sbin/sshd -D
username    15360  0.0  0.0   4376   820 pts/0    S+   19:07   0:00 grep --color=auto -i ssh

So its running fine just last night i connected remotely and there was not an issue this is the first time i have tried to connect via localhost in a few weeks not a big issue but its annoying as i don't know why it would not work.

---

### Post by papibe on 2012-08-03
Hi Nicky..

Have you changed the port or the listen address on you sshd config?

Could you post the result of this command?
```
grep -i listen /etc/ssh/sshd_config 

grep -i port /etc/ssh/sshd_config 
```
Regards.

---

### Post by Nicky.. on 2012-08-03
No problem here is the results  

nicky@BedRoomPC:/etc/ssh$ grep -i listen /etc/ssh/sshd_config 
# What ports, IPs and protocols we listen for
#ListenAddress ::
ListenAddress 192.168.1.102
nicky@BedRoomPC:/etc/ssh$ grep -i port /etc/ssh/sshd_config
# What ports, IPs and protocols we listen for
Port 22

Strange?

Oh it works when i connect to 

nicky@BedRoomPC:/etc/ssh$ ssh 192.168.1.102
Ubuntu 12.04 LTS
nicky@192.168.1.102's password: 

Must be something i changed in the config file i guess

---

### Post by jerome1232 on 2012-08-03
I believe if your going to bind it to a specific address you need to bind it to localhost as well if you want to be able to connect to localhost.

ie add

ListenAddress 127.0.0.1


alternativly you can bind it to all addresses by not specifying an address or by binding it to 0.0.0.0

I'm just guessing based on my own sshd_config which has no specified bind address, which defaults it to listening on all interfaces.

---

### Post by papibe on 2012-08-03
> **jerome1232 said:**
> I'm just guessing based on my own sshd_config which has no specified bind address, which defaults it to listening on all interfaces.
+1

If you want sshd to bind to all your interfaces, comment all the 'ListenAddress' lines. By default sshd will bind to all its addresses, including 127.0.0.1 (localhost).

Don't forget to restart your service:
```
sudo service ssh restart
```
Regards.

---

