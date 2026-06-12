---
title: "Open SSH, need help"
date: 2011-08-08
forum: General Help
---

### Post by Kuhleen on 2011-08-08
Hi!
I installed Open SSH and don't know how to launch it from the terminal.
Can someone help me with this?

---

### Post by Kira_Belka on 2011-08-08
just type ssh -l "login" "target ip"  in terminal emulator )))
:popcorn:

but you don't need to install OpenSSH .. 
so you can use it too)but as ssh server not as client

---

### Post by Kuhleen on 2011-08-08
> **Kira_Belka said:**
> just type ssh -l "login" "target ip"  in terminal emulator )))
:popcorn:

but you don't need to install OpenSSH .. 
so you can use it too)but as ssh server not as client

Ok but what I must write instead of "login" and "target ip".

My Ubuntu OS password instead of "login" and the ip my computer has instead of "target ip"?

---

### Post by Kira_Belka on 2011-08-08
mmmm... 1. how do you want to use ssh? your pc as client or other pc as clent and your as server for remote connection?

---

### Post by WorMzy on 2011-08-08
If you're running the ssh server daemon, you can connect to it like so:

```
ssh wormzy@127.0.0.1
```

My username is wormzy, and 127.0.0.1 is the loopback IP for the PC.

similarly, I can use my LAN IP:

```
ssh wormzy@192.168.0.140
```

my internet IP:

```
ssh wormzy@88.XXX.XXX.XXX
```

or my website url:

```
ssh wormzy@www.example.com
```

After running one of these commands, you'll get asked for your password, which you enter just like normal. That's all there is to it.

---

### Post by Kuhleen on 2011-08-08
> **WorMzy said:**
> 
My username is wormzy, 
Here you mean your ubuntu username right?


> **Kira_Belka said:**
> mmmm... 1. how do you want to use ssh? your pc as client or other pc as clent and your as server for remote connection?

To be honest I'm learning to use SSH right now so it's good to try them both :).

---

### Post by WorMzy on 2011-08-08
> **Kuhleen said:**
> Here you mean your ubuntu username right?

For the sake of this example, yes. I use Arch instead of Ubuntu though.

Whatever your username is for the local login, will be your username for the remote (ssh) login.


> **Kuhleen said:**
> To be honest I'm learning to use SSH right now so it's good to try them both :).
You'll need to use both anyway. You can't use the client if you don't have a server to connect to. ;)

---

### Post by pqwoerituytrueiwoq on 2011-08-08
here are some examples
```

ssh client@client-desktop.local # default computer name if user name is client
ssh client@bedroom-pc.local # custom computer name
ssh client@192.168.1.57 # using ip address

```
openssh-server must me installed on the system you are connecting to

---

