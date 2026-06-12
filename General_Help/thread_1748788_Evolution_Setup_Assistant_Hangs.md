---
title: "Evolution Setup Assistant Hangs"
date: 2011-05-03
forum: General Help
---

### Post by Val42 on 2011-05-03
Hello,

For this problem I have searched the net and these forums without finding any answer.  I'm hoping that someone here can tell me what I need to do to fix this.

I have have been using Ubuntu at home since 8.04.  I have been able to migrate my Evolution email throughout upgrades.  Sometimes I've backed up my system, re-installed then copied the data back.  This has worked every time before, but not now.

The upgrade from 10.10 to 11.04 didn't go well.  I did a totally new installation of 11.04.  I started Evolution once.  It began with the Evolution Setup Assistant.  I cancel because I wanted to use the backup that I had.  After I copied the .evolution directory back to my home directory and started Evolution again, the Setup Assistant hangs at the first screen with both "Cancel" and "Forward" ghosted out.  I restored the original .evolution directory that it had created, but it did the same thing.

No matter what I have tried since, I get the same result.  I have even let it go for hours to see if it is just taking its time cleaning up.  However, it seems to not be taking any CPU time so that is not the problem.

When I ran it from the command line I got errors about files in .cache/evolution and .evolution already existing.  When I delete these directories and run it again I get, "(evolution:3178): evolution-network-manager-WARNING **: network_manager_check_initial_state: Timeout was reached".  When I run it again, I get no messages.  There is an implied kill of the process between each run because it hangs as described above.

Is there some lock file that I need to delete before it will stop  hanging?  Once I get it to stop hanging, is there something special I  need to migrate Evolution from Ubuntu 10.10 to Evolution from Ubuntu  11.04?

Thanks,

- Val -

---

### Post by dcstar on 2011-05-04
> **Val42 said:**
> Hello,

For this problem I have searched the net and these forums without finding any answer.  I'm hoping that someone here can tell me what I need to do to fix this.

I have have been using Ubuntu at home since 8.04.  I have been able to migrate my Evolution email throughout upgrades.  Sometimes I've backed up my system, re-installed then copied the data back.  This has worked every time before, but not now.

The upgrade from 10.10 to 11.04 didn't go well.  I did a totally new installation of 11.04.  I started Evolution once.  It began with the Evolution Setup Assistant.  I cancel because I wanted to use the backup that I had.  After I copied the .evolution directory back to my home directory and started Evolution again, the Setup Assistant hangs at the first screen with both "Cancel" and "Forward" ghosted out.  I restored the original .evolution directory that it had created, but it did the same thing.
......

Don't "cancel" things, let it set up and then use the Restore function in Evolution.

Try deleting the ~/.gconf/apps/evolution folder.

---

### Post by Val42 on 2011-05-05
> **dcstar said:**
> Don't "cancel" things, let it set up and then use the Restore function in Evolution.

Try deleting the ~/.gconf/apps/evolution folder.

This didn't work.  I tried deleting the folder that you suggested with the same result.

I have also let it run for hours, but both cancel and forward are ghosted out.  The application has taken on that deathly gray that means that the operating system thinks that it is dead.

Since evolution won't work, I'm going to have to switch to another email program soon.  That's too bad since I have years of email in this email program.

Thanks for your help.  Can anyone else offer a suggestion?

- Val -

---

### Post by Val42 on 2011-05-07
Just before I made this post I figured out how to fix evolution.  However, I'd like to make two points first.

First of all, I'd like to thank the one person who replied to my email.  Even though it didn't work, I'm glad that he was willing to help.

Second, evolution should not be so brittle that canceling out the first time causes this sort of problem.  I created another account on my system and tried to reproduce the problem, but I could not.  The program should at least try something to recover rather than staying wedged.  Nevertheless, as a programmer I know that not all contingencies are thought of.

In order to get evolution to work I created a test account (named "test"), started evolution in that account, found all directories with "evolution" in them (".evolution", ".cache/evolution", ".local/share/evolution" and ".gconf/apps/evolution") and copied them to my account, then restored my ".evolution" directory (containing my email).  It didn't remember any of my passwords or my appointments, but everything else (including email and calendar) seems to be there.

I'm posting this reply so that if this happens to someone in the future, they will know how to solve the problem.

- Val -

---

### Post by dlebauer on 2011-08-15
Hi Val, I had the same problem as you, but only needed to delete the directories that you mentioned, rather than set up a new user and copy them back over.

Thanks for the help!

```
rm -rf ~/.gconf/apps/evolution
rm -rf ~/.cache/evolution
rm -rf ~/.local/share/evolution/
evolution &

```

---

