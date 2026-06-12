---
title: "&quot;halt&quot; does not power off on Ubuntu Server 12.04"
date: 2012-04-29
forum: General Help
---

### Post by CharlesA on 2012-04-29
Howdy,

I ran into this while I was testing Precise on a VM as well as on the physical machine itself.

If in run this:

```
sudo halt
```

The machine halts but doesn't power off. This didn't occur in 10.04 - halt would power the machine off.

However, if I issue:

```
sudo shutdown -h now
```

The machine powers off fine.

I found a bug for 11.10 here:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240)

But it seems to also apply to 12.04.

Doesn't halt and shutdown -h now do the exact same thing?

Thanks,
Charles

Oh right system specs:

Ubuntu 12.04 x64
i7 2600K
16GB DDR3
Gigabyte Z68XP-UD3 with latest bios
500GB HDD

---

### Post by mips on 2012-04-29
Weird, but does halt not just call shutdown?

---

### Post by CharlesA on 2012-04-29
> **mips said:**
> Weird, but does halt not just call shutdown?

That's what I thought, which is why it seems so strange.

I asked Haqking to test his 12.04 install in VBox and his shutdown fine where mine just sat there at the splash screen after it halted.

So strange and I have no idea where to even look for differences.

I only mention VBox cuz it exhibits the same thing the physical machine does.

---

### Post by Zukaro on 2012-04-29
I've never used the halt command so I know nothing about it, but I know "poweroff" also shuts down a Linux machine.

(*that probably doesn't help you but I've posted it anyways :P*)

---

### Post by haqking on 2012-04-29
CharlesA


There are some differences i believe, however halt should by default call -p which is to halt and poweroff.

Try halt -p to see if that works ?

Edit: ok so in my 12.04 which was upgraded from 11.10 VM halt works.

I just did a fresh 12.04 VM install and halt did not poweroff, however halt -p does ;)

Peace

---

### Post by CharlesA on 2012-04-29
Thanks, that helps clear it up.

I still wonder if it is a bug cuz it works fine on an upgrade but not on a clean install.

I'll try it on an 10.04 machine upgraded to 12.04 and see if it reacts the same.

---

### Post by CharlesA on 2012-04-29
Update: I upgraded a 10.04 vm to 12.04 and halt has the same behavior. **poweroff** works fine and powers off the box. halt -p works fine as well.

That VM was on the same host that exhibits the halt issue.

Physical machine (Core2Duo E8500 3.16Ghz, Gigabyte EP45-UD3R mobo) Same results with halt but halt -p works fine. Clean install of Precise server.

Physical machine (Pentium Dualcore E6500 2.93Ghz, Asus P5Q SE mobo), same halt results and halt -p works fine.

Running:
```
sudo halt -p
```

Powers off fine, but halt just halts the system.


The odd thing is in the bug report I linked in the OP, comment #4 that says:

> This is due to "halt", no longer powering off the machine as well, now one has to tell it to poweroff explicitly.

Where is this documented??

I checked /etc/default/halt on both my 10.04 box (which powers off when halt is issued) and my 12.04 box (which doesn't) and it is the same:

```
charles@Lucid:~$ cat /etc/default/halt
# Default behaviour of shutdown -h / halt. Set to "halt" or "poweroff".
HALT=poweroff

```

EDIT: I just checked on a Ubuntu desktop install and the same thing occurs. I have added a comment to the bug report linked to in the OP.

EDIT2: I asked around on #ubuntu and got the answer to "use shutdown" or "halt -p"

I found a couple different questions on AskUbuntu as well, with different answers.
[http://askubuntu.com/questions/73696/what-is-the-proper-terminal-way-to-shutdown](http://askubuntu.com/questions/73696/what-is-the-proper-terminal-way-to-shutdown)
[http://askubuntu.com/questions/110242/problem-with-halt-command-to-power-off](http://askubuntu.com/questions/110242/problem-with-halt-command-to-power-off)

The man page doesn't help all that much either:
[http://manpages.ubuntu.com/manpages/precise/man8/halt.8.html](http://manpages.ubuntu.com/manpages/precise/man8/halt.8.html)

---

### Post by dmizer on 2012-04-30
With what message does halt halt? Have you tried using the verbose switch to see comments?

I had a Dapper box ages ago with this problem and it had to do with how halt talked to the BIOS. Don't remember how I fixed it though.

---

### Post by CharlesA on 2012-04-30
It just says "system halted" like it did on Lucid except it doesn't power the box off. "halt -p", "poweroff", "shutdown -h now" all power the box off fine.

I updated the launchpad bug asking if this is intended or what, but no response as of yet.

Guess I'll just have to learn a new command as I've always use halt to power off an *nix machine. *shrugs*

EDIT: Filed a new bug report:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/991997](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/991997)

---

### Post by caraboy on 2012-05-03
I have the same problem, "halt -p" seems to work though. 

I don`t mind using this command, as long as the machine stops, but this should be written somewhere, as I lost all night trying to find an answer to why the system was not shutting down. :)

---

### Post by CharlesA on 2012-05-03
> **caraboy said:**
> I have the same problem, "halt -p" seems to work though. 

I don`t mind using this command, as long as the machine stops, but this should be written somewhere, as I lost all night trying to find an answer to why the system was not shutting down. :)
Glad you were able to find a solution.

I just wish they had documented thing change somewhere, but I have a feeling it is a bug. Have you added that the bug affects you to the report in post #9?

---

### Post by deribo on 2012-09-14
hello,

try to edit /etc/init.d/halt and remove this lines:

```
if [ "$INIT_HALT" = "HALT" ]
then
  poweroff=""
fi
```

below
```
poweroff="-p"
```

this fixes the problem for me.

Dennis

---

### Post by angry_johnnie on 2012-09-14
I'm pretty sure that's no bug, but rather standard, expected, behaviour.

Shutdown invokes several scripts to properly stop all running processes and, finally, invokes halt.

It seems that, in many cases, halt has been symlinked to shutdown, so that running sudo halt will have the same effect as sudo shutdown -h now, but it's really not the same.

**halt -p** would be correct.

**man halt** would give you some more info. :)

---

### Post by CharlesA on 2012-09-14
Glad you were able to figure out how to work around the issue.

I have just learned to use poweroff if I want to power the box down.

Thanks.

---

### Post by furynick on 2013-02-22
Had the same issue and learnt that halt command should not be used to shut down a Linux OS as other Unixes, shutdown must be use instead to properly shut down a Linux box.

I guess halt, poweroff and reboot commands (at least) should not be in PATH but in /usr/lib/upstart to avoid confusion.

---

### Post by ulabunt on 2013-05-17
It's clear that "halt" command now  by default does not power off unless you use -p option. 
But why does it not respect the setting from /etc/default/halt?
etc/init.d/halt sources the default file but its used only if $INIT_HALT is empty. 
It seems though that when I call halt, $INIT_HALT has allready value HALT.
So I forced it to act on information from /etc/default/halt, by commenting out the if statement. 
/etc/init.d/halt:

```

[FONT=system]do_stop () {    
     #if [ "$INIT_HALT" = "" ]
    #then
        case "$HALT" in
          [Pp]*)
            INIT_HALT=POWEROFF
            ;;
          [Hh]*)
            INIT_HALT=HALT
            ;;
          *)
            INIT_HALT=POWEROFF
            ;;
        esac
    #fi
[/FONT]
```

---

### Post by johnycage on 2013-06-18
> **CharlesA said:**
> It just says "system halted" like it did on Lucid except it doesn't power the box off. "halt -p", "poweroff", "shutdown -h now" all power the box off fine.

I updated the launchpad bug asking if this is intended or what, but no response as of yet.

Guess I'll just have to learn a new command as I've always use halt to power off an *nix machine. *shrugs*

EDIT: Filed a new bug report:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/991997](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/991997)
Thank you for clarification. I've been using halt for long but it doesnt work on 12.04LTS. Should use 'halt -p' now on.

---

### Post by CharlesA on 2013-06-18
> **johnycage said:**
> Thank you for clarification. I've been using halt for long but it doesnt work on 12.04LTS. Should use 'halt -p' now on.

Welcome.

Getting in the habit of using poweroff hasn't been that big of a deal, and now I don't have to worry about the machine being running but not powered off.

---

