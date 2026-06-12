---
title: "How to stop firestarter from automatically loading on boot?"
date: 2012-01-03
forum: General Help
---

### Post by apollothethird on 2012-01-03
Can someone tell me how to stop firestarter from starting when the system boots?  I'm testing ufw which is still being developed and supported.  I prefer not to have to uninstall firestarter.  I would like to leave it installed for now, just not have it start unless I decide to manually start it.

chkconfig (sudo chkconfig --list firestarter) shows:

```

firestarter               0:off  1:off  2:off  3:off  4:off  5:off  6:off

```Thanks in advance for any suggestions or comments.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Lars Noodén on 2012-01-03
Your output from chkconfig shows it to be turned off.  You can use [update-rc.d](http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-rc.d.8.html) to adjust that.  Or you can use [font=Courier New]/etc/init.d/firestarter[/font] to start or stop it manually.

---

### Post by apollothethird on 2012-01-03
> **Lars Noodén said:**
> Your output from chkconfig shows it to be turned off.  You can use [update-rc.d]("http://manpages.ubuntu.com/manpages/oneiric/en/man8/update-rc.d.8.html") to adjust that.  Or you can use [FONT=Courier New]/etc/init.d/firestarter[/FONT] to start or stop it manually.

Maybe I'm missing something.  It appears that you're saying that I have to remove the script using the update-rc.d to stop firestarter from automatically starting.

For all other applications I have always (for the 15 years that I've been using Linux) been able to stop a service from automatically starting with: chkconfig --level [s0123456] service [on/off]

If all the levels are off the service wouldn't start unless I decided to manually start it.

I don't hvae any problems manually starting or stopping the firestarter service.  However, what I want to do is stop it from starting automatically so that it will only start if I manually start it with:

```

sudo service firestarter start

```If I remove the script from the init.d directory, then my manually start option would then fail.

At present I have to manually stop firestarter every time I reboot the machine.  I do that with:

```

sudo service firestarter stop

```I'm hoping for a way to not have it start in the first place.  I don't know enough about it to be sure that everything that it configures when it starts gets removed when it's stopped.  So hopefully that will be a way to not have it start in the first place, short of having to uninstall it.

Thanks again for anyone who has any suggestions or comments.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Lars Noodén on 2012-01-03
Unfortunately, there are three or four ways in Ubuntu to start or stop scripts.  chkconfig is one of them.

I notice that even with a clean install of firestarter there is nothing in the SystemV init scripts for firestarter.  Looking at the files that firestarter installs, there are some outside the control of chkconfig and update-rc.d

```

/etc/network/if-down.d/50firestarter
/etc/network/if-up.d/50firestarter

```

It looks like those are where firestarter is started upon boot.  I don't know which program is supposed to manage options in if-up.d or if-down.d so if you comment out the content of those scripts manually, or remove the scripts, then it will not start automatically.

---

### Post by apollothethird on 2012-01-03
> **Lars Noodén said:**
> Unfortunately, there are three or four ways in Ubuntu to start or stop scripts.  chkconfig is one of them.

I notice that even with a clean install of firestarter there is nothing in the SystemV init scripts for firestarter.  Looking at the files that firestarter installs, there are some outside the control of chkconfig and update-rc.d

```

/etc/network/if-down.d/50firestarter
/etc/network/if-up.d/50firestarter

```It looks like those are where firestarter is started upon boot.  I don't know which program is supposed to manage options in if-up.d or if-down.d so if you comment out the content of those scripts manually, or remove the scripts, then it will not start automatically.

Thanks, Lars.  I commented out the line in the two files and now it behaves like the other services and I can manually start and stop the service with the "sudo serivce start/stop" command.  This way I can test the difference between ufw and firestarter and become more familiar with one best fits my needs.

When firestarter was automatically started, I couldn't be sure if ufw was functioning fully or some of the effect I was seeing were residue left by firestarter.

Everything is working fine now!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

