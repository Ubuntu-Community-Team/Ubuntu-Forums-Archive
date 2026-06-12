---
title: "I have no idea what's going on..."
date: 2012-07-23
forum: General Help
---

### Post by BerZerkker on 2012-07-23
Hello.

I came into some serious problems with my system and I'm writing this post form elinks, so please, don't bash me if my problem was already answered as I tried to search forums but came up with nothing and I have already lost an entire detailed post due to unfamiliar keybindings...

What happened:
Last time I rebooted everything was ok, I haven't changed any config files, nor have I installed any additional software (except some games through wine, but that shouldn't count, should it?).
I have installed the recommended updates through aptitude, and nothing more.

Now my system starts, I see a brief (50 miliseconds maybe) view of the loading screen, then it redirects me to tty1 with the login prompt.
Last thing on tty7, where X should start is:
```

* Stopping Userspace bootsplash [OK]
                                        [OK]

```
then there's just a blinking cursor.

service lightdm status answers with lightdm stop/waiting
when I try to start it it says
```

start: Rejected send message, 1 matched rules; type="method_call", sender="1.24" (uid=1000 pid=13837 comm="start lightdm ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name=(unset) requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

```
and when I try to stop it it says:
```

stop: Unknown instance:

```

I really have no idea what's going on, I'm a newbie, help me or at least point me in the right direction.

I would've reinstalled the system already, but my laptop is in really bad shape and can't even navigate through boot selection menu...

Thanks in advance.

---

