---
title: "OpenSSH and port forwarding"
date: 2009-12-22
forum: General Help
---

### Post by Blastnsmash on 2009-12-22
I was just wondering if anyone knew if this was a possibility:

Can you tell OpenSSh to portforward based on who is logged in?

For example, if Jim is logged in, when he tunnels into SSh, ssh will port forward to 2 different services.

When Mary is logged in, she is only allowed to use 1 of the servies. 

I want to specify which user can access which services ( port forwards ) based on the user. 

I know in the sshd_config you can specify global forwards but I want forward different ports based on the user. 

Any help? Thank you very much!

---

### Post by kidders on 2009-12-24
Hi there,

It depends on what you want to achieve. For example, *preventing* access to a service would be tricky, but if all you're interested in doing is *facilitating* access, then that's much easier. 

Suppose, for instance, you wrote a script like this...```
#!/bin/sh

CURRENT_USER=`/usr/bin/whoami`
if [ "$CURRENT_USER" = "mary" ]; then
	SSH_PARAMS="-L3389:localhost:3389"
elif [ "$CURRENT_USER" = "jim" ]; then
	SSH_PARAMS="-L3389:localhost:3389 -L10240:localhost:10240"
fi

/usr/bin/ssh.real $SSH_PARAMS $@
```
Then, suppose you moved /usr/bin/ssh to /usr/bin/ssh.real and saved your script to /usr/bin/ssh. Something like that would have the effect of forwarding different ports on a per-user basis.[LIST]
[*]Obviously, it wouldn't prevent Mary from accessing the services Jim gets to use if Jim were also logged in at the time.
[*]Similarly, you couldn't prevent Mary forwarding Jim's ports herself, manually.
[*]That script is just for demonstration purposes ... One problem with it is that it will try to forward the same ports every time it's invoked. I suppose it should really check another copy of it hasn't already done so.
[*]Also, rather than renaming /usr/bin/ssh, setting up a shell alias might be cleaner.
[/LIST]

That's all irrelevant though, if you're really trying to *prevent* access to services on a per-user basis. That would probably be best handled on the remote side of the tunnels, so it wouldn't matter whether ports were forwarded to services you didn't want Mary using.

---

### Post by Blastnsmash on 2010-01-05
> **kidders said:**
> Hi there,

It depends on what you want to achieve. For example, *preventing* access to a service would be tricky, but if all you're interested in doing is *facilitating* access, then that's much easier. 

Suppose, for instance, you wrote a script like this...```
#!/bin/sh

CURRENT_USER=`/usr/bin/whoami`
if [ "$CURRENT_USER" = "mary" ]; then
	SSH_PARAMS="-L3389:localhost:3389"
elif [ "$CURRENT_USER" = "jim" ]; then
	SSH_PARAMS="-L3389:localhost:3389 -L10240:localhost:10240"
fi

/usr/bin/ssh.real $SSH_PARAMS $@
```
Then, suppose you moved /usr/bin/ssh to /usr/bin/ssh.real and saved your script to /usr/bin/ssh. Something like that would have the effect of forwarding different ports on a per-user basis.[LIST]
[*]Obviously, it wouldn't prevent Mary from accessing the services Jim gets to use if Jim were also logged in at the time.
[*]Similarly, you couldn't prevent Mary forwarding Jim's ports herself, manually.
[*]That script is just for demonstration purposes ... One problem with it is that it will try to forward the same ports every time it's invoked. I suppose it should really check another copy of it hasn't already done so.
[*]Also, rather than renaming /usr/bin/ssh, setting up a shell alias might be cleaner.
[/LIST]

That's all irrelevant though, if you're really trying to *prevent* access to services on a per-user basis. That would probably be best handled on the remote side of the tunnels, so it wouldn't matter whether ports were forwarded to services you didn't want Mary using.

Ideally, by default, when someone tunnels into my Ubuntu box, I want them to have no access at all, not even to the shell. I think this is correctly accomplished by creating a new user with no priveledges. Use the command sudo -usermod -s /bin/false [username] to prevent shell access.

Now you have a user with no shell access. Now, I want to, based on who is logged in allow them certain services. Can that be done?

---

### Post by kidders on 2010-01-05
Hey again,

I think I misunderstood your o/p. It seemed like you were asking about determining which ports to forward based on who was logged into the *client* machine. If you want to base the decision on who's logged into the Ubuntu box, then that can't be done. Looking at it another way, that would amount to forcibly binding a remote service to local ports on other peoples' machines ... so it's impossible by design. You can't exercise that kind of control over someone's network configuration remotely. In any case, at a practical level, there would be no way for the server to know the port it wanted the client to forward was even available.

What kind of services are we talking about, by the way? I'm assuming they don't support authentication in their own right (or you wouldn't be asking your question), but there may still be an easier way to achieve your goal.

SSH tunnels are initiated client-side, so it's up to the users logging in to forward whatever ports they feel like forwarding. That's why I was wondering whether your focus is on facilitating access to services (ie simply making it easier for people to do), or blocking unauthorised access. It's sounding like you may be more interested in the latter, which could be tricky because the services running on your Ubuntu box would be unable to distinguish between local & remote users.

---

### Post by Blastnsmash on 2010-01-06
> **kidders said:**
> Hey again,

I think I misunderstood your o/p. It seemed like you were asking about determining which ports to forward based on who was logged into the *client* machine. If you want to base the decision on who's logged into the Ubuntu box, then that can't be done. Looking at it another way, that would amount to forcibly binding a remote service to local ports on other peoples' machines ... so it's impossible by design. You can't exercise that kind of control over someone's network configuration remotely. In any case, at a practical level, there would be no way for the server to know the port it wanted the client to forward was even available.

What kind of services are we talking about, by the way? I'm assuming they don't support authentication in their own right (or you wouldn't be asking your question), but there may still be an easier way to achieve your goal.

SSH tunnels are initiated client-side, so it's up to the users logging in to forward whatever ports they feel like forwarding. That's why I was wondering whether your focus is on facilitating access to services (ie simply making it easier for people to do), or blocking unauthorised access. It's sounding like you may be more interested in the latter, which could be tricky because the services running on your Ubuntu box would be unable to distinguish between local & remote users.

ok. Yes, I see what you are saying. Once your logged in through ssh, it is as if you're logged in to the actual machine and it cannot tell the difference between local and remote.

I am trying to secure mysql server. My thought process was to block all ports using Ubuntu firewall and require users to SSH into the Ubuntu server. I was hoping there was a way, based on login to limit access to services and of course by default all users that would ssh into the machine would not be allowed a shell to execute anything.

I would like certain users to be able to see mysql on certain ports. So I could use mysql login@xxx capability. In this way, if Mary logs in, she could only see mysql on port 8888 and mysql will be setup to accept a user name and password for her on this port only.

It was just a thought experiment I was having, I'm not sure if this could work.

---

### Post by kidders on 2010-01-06
Damn... Making people use SSH tunnels to access a MySQL server has *major* security advantages you're not likely to want to give up. In terms of what ports to use, I think you have two options:

[LIST]
[*]You could keep things simple and run just one server on port 3306, right where your users would expect it to be. Anyone with SSH access could forward that port, but it wouldn't be much use without a valid MySQL username & password. Basically, you'd be relying on MySQL to keep people out of other users' data & on the database owners not to do silly things like grant password-less access to their own private databases. This approach has the added advantage of allowing you to share data straightforwardly with multiple users.
[*]The only reason I can think of for wanting to make MySQL available on multiple ports is so you could run multiple database servers, and give each user free rein on an entire instance, rather than just a collection of databases on a shared instance. There are a few odd situations where you might need to do something like this, eg your users may each require different versions of MySQL.
[/LIST]

If you really do want to go with the multiple ports option, you could give iptables' per-user packet filtering a try, but I don't *think* you'll be able to get it to work over a tunnel. I suspect your users may turn out to need shell access ... You see, you'd need to find some way of ensuring individual users' network packets always originate from a process they own, which could get very hairy.

> **Blastnsmash said:**
> I am trying to secure mysql server.This is off-topic, but you don't need to rely on a firewall to block remote (technically, tunneled = local) access to your MySQL server. For best security, you should configure it not to listen on any externally accessible network interfaces ... that way, it wouldn't matter if you had no firewall at all.

Anyhow, I hope there's *something* helpful in there.

---

### Post by Blastnsmash on 2010-01-06
Well. Perhaps that is secure is I can probably make it.

By disallowing shell access and setting ssh to allow forward to only mysql - I think that is good as it gets.



If there is another approach that is optimal, I'm all up for suggestions. From what I've read though, SSH tunnels are pretty solid as long as you use PKI.

Thanks for your suggestions. It is incredibly powerful to just get some thoughts on the table from other minds.

---

### Post by kidders on 2010-01-07
> **Blastnsmash said:**
> If there is another approach that is optimal, I'm all up for suggestions.I don't think so, tbh. Interacting with MySQL over SSH tunnels is pretty common practice & works quite well.

> **Blastnsmash said:**
> From what I've read though, SSH tunnels are pretty solid as long as you use PKI.That depends on your users. Key-based authentication can be very unsafe if your user base isn't accustomed to handling private keys with due care. Quite often, it's something I tend to disable.

---

### Post by Lars Noodén on 2010-01-08
On the server side you can use the **Match group** directive in sshd_config to determine which groups of users can forward ports.  Combine that with the **PermitOpen** directive and you can limit that group to specific ports.

```

# just a guess for the tail of /etc/ssh/sshd_config ot allow 
# members of *mysqlusers* to forward port 3306
Match group mysqlusers
      PermitOpen *xx.yy.zz.aa*:3306

```

The drawback to the **PermitOpen** directive is that you must enter the hostname or ip number exactly, no pattern matching, wildcards or globbing.

---

### Post by Blastnsmash on 2010-01-08
> **Lars Noodén said:**
> On the server side you can use the **Match group** directive in sshd_config to determine which groups of users can forward ports.  Combine that with the **PermitOpen** directive and you can limit that group to specific ports.

```

# just a guess for the tail of /etc/ssh/sshd_config ot allow 
# members of *mysqlusers* to forward port 3306
Match group mysqlusers
      PermitOpen *xx.yy.zz.aa*:3306

```

The drawback to the **PermitOpen** directive is that you must enter the hostname or ip number exactly, no pattern matching, wildcards or globbing.

I think that's what I'm looking for, thanks.

---

