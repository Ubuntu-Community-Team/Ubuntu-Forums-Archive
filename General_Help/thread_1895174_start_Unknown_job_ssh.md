---
title: "start: Unknown job: ssh"
date: 2011-12-14
forum: General Help
---

### Post by yawnmoth on 2011-12-14
I do "sudo apt-get install openssh-server" and after all the keys are generated I get "start: Unknown job: ssh".

I do "service ssh start" and get the same thing.

I do "sudo apt-get --purge remove openssh-server" and try to reinstall it and get the same thing.

Any ideas?

---

### Post by MartijnNL on 2011-12-14
The ssh server process is called sshd. ssh is the client.
The server normally starts itself on reboot. You could run:

```
ps ax | grep sshd
``` to check if it's running.

Is the openssh-client package installed? (normally should be on a regular install)

---

### Post by matt_symes on 2011-12-14
Hi

Is the ssh server package installing itself correctly. What's the output of

```
dpkg -l openssh-server
```That is a small L after dpkg.

Also what is the output of

```
ls /etc/init/ss*
```

EDIT

> I do "service ssh start" and get the same thing.

That would require a *sudo service ssh start* comand.

Kind regards

---

### Post by yawnmoth on 2011-12-14
Output of ps ax | grep sshd
```
 6985 pts/0       0:00 grep --color=auto sshd
```

Output of dpkg -l openssh-server

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  openssh-server 1.5.9p1-7ubunt secure shell (SSH) server, for secure access
```

Output of ls /etc/init/ss*

```
/etc/init/ssh.conf
```

---

### Post by matt_symes on 2011-12-14
Hi

What is the output of

```
ls -l /etc/init/ssh.conf
``````
cat /etc/init/ssh.conf
```and 

```
which sshd
```

To see you system

```
cat /etc/lsb-release
```
```
uname -a
```

Kind regards

---

### Post by supercheetah on 2011-12-14
Does /etc/init.d/ssh exist?

---

### Post by yawnmoth on 2011-12-15
ls -l /etc/init/ssh.conf
```
-rw-r--r-- 1 root root 574 2011-04-02 10:06 /etc/init/ssh.conf
```

cat /etc/init/ssh.conf
```
# ssh - OpenBSD Secure Shell Server
#
# The OpenSSH server provides secure shell access to the system.

description    "OpenSSH server"

start on filesystem or runlevel [2345]
stop on runlevel [!2345]

respawn
respawn limit 10 5
umask 022

pre-start script
    test -x /usr/sbin/sshd || { stop; exit 0; }
    test -e /etc/ssh/sshd_not_to_be_run && { stop; exit 0; }
    test -c /dev/null | { stop; exit 0; }

    mkdir -p -m0755 /var/run/sshd
end script

# if you used to set SSHD_OPTS in /etc/default/ssh, you can change the
# 'exec' line here instead
exec /usr/sbin/sshd -D
```

which sshd
```
/usr/sbin/sshd
```

cat /etc/lsb-release
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
```

uname -a
```
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
x86_64 x86_64 GNU/Linux
```

ls /etc/init.d/ssh
```
-rwxr-xr-x 1 root root 4194 2011-07-29 16:02 /etc/init.d/ssh
```

---

### Post by matt_symes on 2011-12-15
Hi

That all looks fine so far. 

What's the output of

```
ls -l /usr/sbin/sshd
```

and 

```
ls /etc/ssh/sshd_not_to_be_run
```

Was the ssh you installed from the main repositories for Oneiric ? Your version number looks different to mine.

Can you start the service without using upstart ? What happens if you type

```
sudo /etc/init.d/ssh start
```You can also stop it with

```
sudo /etc/init.d/ssh stop
```Do you get any feedback if you type

```
sudo initctl start ssh
```Kind regards

---

### Post by yawnmoth on 2011-12-15
ls -l /usr/sbin/sshd
```
-rwxr-xr-x 1 root root 508760 2011-07-29 16:02 /usr/sbin/sshd
```

ls /etc/ssh/sshd_not_to_be_run
```
ls: cannot access /etc/ssh/sshd_not_to_be_run: No such file or directory
```

sudo /etc/init.d/ssh start
```
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service ssh start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start ssh
start: Unknown job: ssh
```

sudo initctl start ssh
```
initctl: Unkwown job: ssh
```

---

### Post by matt_symes on 2011-12-15
Hi

That all looks good as well.

What's the output of

```
initctl list | grep ssh
```

and 

```
ldd /usr/sbin/sshd
```

Kind regards

---

### Post by yawnmoth on 2011-12-16
initctl list | grep ssh returns nothing.

ldd /usr/sbin/sshd:

```
	linux-vdso.so.1 =>  (0x00007ffff65ff000)
	libwrap.so.0 => /lib/x86_64-linux-gnu/libwrap.so.0 (0x00007f6cd9d58000)
	libpam.so.0 => /lib/x86_64-linux-gnu/libpam.so.0 (0x00007f6cd9b4a000)
	libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007f6cd992b000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f6cd970e000)
	libcrypto.so.1.0.0 => /lib/x86_64-linux-gnu/libcrypto.so.1.0.0 (0x00007f6cd935f000)
	libutil.so.1 => /lib/x86_64-linux-gnu/libutil.so.1 (0x00007f6cd915b000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f6cd8f43000)
	libcrypt.so.1 => /lib/x86_64-linux-gnu/libcrypt.so.1 (0x00007f6cd8d0a000)
	libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007f6cd8acb000)
	libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f6cd8802000)
	libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f6cd85fe000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f6cd825e000)
	libnsl.so.1 => /lib/x86_64-linux-gnu/libnsl.so.1 (0x00007f6cd8044000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f6cd7e40000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f6cda1f7000)
	libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f6cd7c17000)
	libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007f6cd7a0f000)
	libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007f6cd780c000)
	libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f6cd75f0000)

```

---

### Post by matt_symes on 2011-12-16
Hi

> initctl list | grep ssh returns nothing.Well everything looks fine apart from this. Upstart knows nothing about your ssh service.

The only thing i can think of at the moment is that upstart is not picking up the configuration file ssh.conf in /etc/init. It is meant to do this automatically using inotify.

From man initctl.
```

reload-configuration

              Requests that the init(8) daemon reloads its configuration.

              This  command  is generally not necessary since init(8) watches its configuration directories with inotify(7) and auto&#8208;
              matically reloads in cases of changes.

              No jobs will be started by this command.
```Let's try to reload manually. From a terminal

```
sudo initctl reload-configuration
```and then

```
sudo service ssh start
```Kind regards

---

### Post by supercheetah on 2011-12-17
This is likely a bug because I just tried installing and running sshd on my computer as well, and I ran into the same issue, and after running *initctl reload-configuration*, I'm still getting *start: unrecognized service*.

A bug report should probably be filed.  I tried finding a relevant bug report on Launchpad, but I couldn't find anything in my initial search.  I am going to keep on looking, though.

Ignore this, I just realized I was using *service* incorrectly (I had *service start ssh* instead of *service ssh start*), sorry.

---

### Post by matt_symes on 2011-12-17
Hi

@supercheetah. Did reloading the configuration work for you ?

> **supercheetah said:**
> This is likely a bug because I just tried installing and running sshd on my computer as well, and I ran into the same issue, and after running *initctl reload-configuration*, I'm still getting *start: unrecognized service*.

A bug report should probably be filed.  I tried finding a relevant bug report on Launchpad, but I couldn't find anything in my initial search.  I am going to keep on looking, though.

Ignore this, I just realized I was using *service* incorrectly (I had *service start ssh* instead of *service ssh start*), sorry.

Kind regards

---

### Post by supercheetah on 2011-12-17
> **matt_symes said:**
> Hi

@supercheetah. Did reloading the configuration work for you ?



Kind regards

It was kind of pointless for me since there were no issues.

One thing that I thought about though is I wonder if there was a problem with the package that was downloaded, and so thus openssh-server may have been installed incorrectly.  Try this:

```

apt-get --purge remove openssh-server
apt-get clean
apt-get install openssh-server

```

It's perhaps a long shot, but...

---

### Post by grndamgt4 on 2012-02-24
> **matt_symes said:**
> Hi

@supercheetah. Did reloading the configuration work for you ?



Kind regards

Hello, I had the same problem and did everything in this thread. After reloading the configuration as you suggested the ssh service started and is working. Thank you for the help.
I'm running a 11.10 live cd off USB with a casper-rw. Thanks again.

---

### Post by sfinktah on 2012-08-24
[edited] thought i had the solution, but i was wrong.  (12.04)

---

### Post by aname4 on 2012-08-25
I just had this problem.   The problem was that the value in
```
hostname
```was not in
```
/etc/hosts
```with 127.0.0.1 assigned.

---

