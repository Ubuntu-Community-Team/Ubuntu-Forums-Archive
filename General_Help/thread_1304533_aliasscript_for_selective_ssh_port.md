---
title: "alias/script for selective ssh port"
date: 2009-10-29
forum: General Help
---

### Post by SpecialEdd on 2009-10-29
One local BOFH just set up some of the machines to ssh on a new port.  Security through obscurity, I suppose.  Won't a decent port scan figure that out?

Anyway, it is a PITA to put in a -p xxx (or -P xxx for scp, thanx for the consistent interface!) for those machines.

I tried to use a 2 string alias, but that doesn't seem to work.

Is my only hope a bash script?  replace my ssh/scp with a script to recognize when you are going to a machine?  What about passing through all the other optional commands?

Thanks!

---

### Post by Lars Noodén on 2009-10-29
Moving the port won't help security.  It will inconvenience the users.  However, like Web2.0, some people feel compelled to do it because it is there.

You can set up an alias in the shell.  Or you can set up something in [~/.ssh/config](http://manpages.ubuntu.com/manpages/karmic/en/man5/ssh_config.5.html) in your own local account.  

```

Host farginbastage1
    HostName farginbastage1.example.org
    Port *xxxx*

Host farginbastage2
    HostName farginbastage2.example.org
    Port *xxxx*


```

If you make many concurrent connections to those machines you can speed up the connections using multiplexing.  First make a place for the control file:
[INDENT][FONT="Courier New"]
mkdir --mode=700 ~/.ssh/controlmasters/
[/FONT][/INDENT]

Then have it ask if you want to use multiplexing, if there is already a master connection open.

```

Host farginbastage1
    HostName farginbastage1.example.org
    Port *xxxx*
    ControlMaster autoask
    ControlPath ~/.ssh/controlmasters/%r@%h:%p

Host farginbastage2
    HostName farginbastage2.example.org
    Port *xxxx*
    ControlMaster autoask
    ControlPath ~/.ssh/controlmasters/%r@%h:%p


```

YMMV.

---

### Post by DaithiF on 2009-10-29
personally i'd just take the hit of typing out the -p and -P params, but you could create a wrapper bash function, something like:

```
function ssh() {
  NON_STD_PORT_MACHINES="machine1 machine2 machine3"
  tmp=${@##*@}
  machine=${tmp%% *}
  if [[ "$NON_STD_PORT_MACHINES" =~  .*$machine.* ]]; then
     \\ssh -p xxx $@
  else
     \\ssh $@
  fi
}
```

a couple of things to note .. the tmp= / machine= lines are to try to extract the hostname from the command you enter.  the slashes before the ssh commands are to indicate to bash to run the unaliased versions of ssh, ie. run ssh, not this function ... otherwise infinite loop...

---

### Post by SpecialEdd on 2009-10-29
> **Lars Noodén said:**
> Moving the port won't help security.  It will inconvenience the users.  However, like Web2.0, some people feel compelled to do it because it is there.


```

Host farginbastage1
    HostName farginbastage1.example.org
    Port *xxxx*
    ControlMaster autoask
    ControlPath ~/.ssh/controlmasters/%r@%h:%p

Host farginbastage2
    HostName farginbastage2.example.org
    Port *xxxx*
    ControlMaster autoask
    ControlPath ~/.ssh/controlmasters/%r@%h:%p


```YMMV.

Thanks a ton!  I figured there was a way but I did not run across it in a few searches I tried.  I appreciate your help!

---

