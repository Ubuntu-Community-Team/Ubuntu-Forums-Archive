---
title: "force eth0 up"
date: 2009-11-04
forum: General Help
---

### Post by telegraphic on 2009-11-04
Hi All - was wondering if there's a way to force my eth0 interface to stay up, even if it looks like there might not be anything on the other end of the ethernet cable? I know to bring up the interface the command is

```
sudo ifconfig 192.... netmask 255.... up
```

but I find it keeps dropping down, meaning I have to keep issuing the command. Unfortunately fixing what's on the other end of the cable isn't an option...

Cheers

---

### Post by soapBAR2 on 2009-11-04
You can always use the --force option. Also, instead of typing the whole command out, you can do three things:

1) use ```
sudo ifup eth0
``` (Assuming your entry for eth0 in /etc/network/interfaces is good). Here are some common /etc/network/interface values for wired connections:

DHCP:
```
auto eth0
iface eth0 inet dhcp

```

STATIC:
```
auto eth0
iface eth0 inet static
address 192.168.0.10
gateway 192.168.0.1
netmask 255.255.255.0

```

2) Add an alias. Aliases are a tool that let you type one command to mean another, and are useful as either shortcuts or to change an option defaults (eg, making ls to list by default, alias ls='ls -l'). They take the form ```
alias whatyouwanttotype='commandtoexecute'
```. You can instantly make new aliases by typing the alias command into the shell - however, these will disappear when you restart the shell. Or, you can add them to your ~/.bashrc (assuming you're using bash) if you want them to always be up. Same syntax in either case, just one new line for each alias.

3) Add a cronjob to do it for you automatically. Just
```
sudo crontab -e
```
Enter your command, and then save and exit
Crontab entries take the form
> MINUTE HOUR DAY_OF_MONTH MONTH DAY_OF_WEEK COMMAND
and accepts wildcards to ignore options.
For example, 

If you wanted to make it run at 6 minutes past every hour, type
> 6 * * * * ifconfig 192.... netmask 255.... up
If you wanted to make it run every minute:
> * * * * * ifconfig 192.... netmask 255.... up
If you wanted to make it run every 5 minutes:
> */5 * * * * ifconfig 192.... netmask 255.... up
If you wanted it to run at 13:52 every Sunday:
> 52 13 * * 0 ifconfig 192.... netmask 255.... up

You get the idea.

---

