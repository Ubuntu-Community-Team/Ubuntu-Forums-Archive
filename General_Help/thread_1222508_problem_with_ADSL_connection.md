---
title: "problem with ADSL connection"
date: 2009-07-25
forum: General Help
---

### Post by abhi90 on 2009-07-25
hello guys...
I am in a serious problem.
I have making the ADSL(pppoe) connection a long time but I cant.
**So please anyone there help me.**
I go to the terminal and do the thing [B]sudo pppoeconf
I enter my user name and password.... then
the message will appear if you want the “noauth” and “defaultroute” options and to remove “nodetach” - I choose Yes.
                  Use peer DNS - I choose Yes.
                  Limited MSS problem - I choose Yes.
   When I had asked if you want to connect at start up, I choose yes.

and then I start the ADSL connection by giving the command in the terminal 
_sodo pon dsl-provider    _
 But nothing happen....

Tell me is there driver or package that I have to install....
If anyone there who knows this stuff then please help me.
[/B]
                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=7673763")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=7673763")

---

### Post by vmikac on 2009-07-25
Try playing lowering max mtu parameter. I'm connecting to the Windows server on the other side, and it worked after I set 

mtu 1416

in /etc/ppp/options

---

### Post by ZhuaSD on 2009-07-25
Can you confirm the line is plugged in and should be able to work.

The pppoe handling is a bit buggy, you have to play with it.

What version are you on?  It makes a difference.

When you startup, execute these two commands:

```
plog
```

```
ifconfig
```

and save the results.

Then, go through pppoeconf, and shorten the mtu to 1408, just in case.

Then, again, 

```
plog
```

```
ifconfig
```

and save output.

Post all output here.

Then, if still no connection, try this:

```
sudo poff dsl-provider
```

```
sudo pon dsl-provider
```

And post your results in this thread, with version.

---

