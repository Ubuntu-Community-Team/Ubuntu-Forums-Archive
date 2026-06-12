---
title: "Upgrade thorugh command line"
date: 2010-12-29
forum: General Help
---

### Post by sarin_cv on 2010-12-29
Hi,
I wanted to upgrade from 10.04 to 10.10 through command line. Found this on searching.
sudo do-release-upgrade

Is it really safe to do it from the command line?

I wanted to schedule it as a cronjob since the calculated size was about 1.5 GB and the internet is free only during night hours.

---

### Post by sarin_cv on 2010-12-29
And what option should I use to accept when prompted for continue/abort?

---

### Post by seawolf167 on 2010-12-29
Previously you could use

```
sudo apt-get update
sudo apt-get dist-upgrade
```

However, they changed it so you are supposed to use the GUI update manager now (command-line isn't supported anymore)

---

### Post by seawolf167 on 2010-12-29
A little looking around, it seems this is the new command-line upgrade:

```
sudo aptitude install update-manager-cor[FONT=monospace]e[/FONT]
sudo do-release-upgrade -d
```

---

### Post by sarin_cv on 2010-12-29
I tried it...after doing all setups and calculations it is asking me to continue or not...I have to press Y/N... so how do I bypass this since it has to be scheduled.... for update, I usually set the -y option so that it won't pause...

---

