---
title: "Netcat server, need a little help please."
date: 2009-09-23
forum: General Help
---

### Post by HPD2 on 2009-09-23
Hey everyone, For my intro to comp forensics class one of our assignments was to create a batch file to collect some information and send it over the network using netcat. I made the batch files and it works great, in windows. Now I'm trying to send it over netcat to Ubuntu and I'm running in to an issue.

In windows I use "netcat -L -p #### > data.txt." The -L switch is for listen hard, re-listen on socket close, witch allows me to do some thing like```
systeminfo | nc %1 %2 -w %3
netstat -ano | nc %1 %2 -w %3
```in a row, without the netcat server stoping. However when I try this in Ubuntu I only see the -l switch that doesn't re-listen and stops the server after the first command.

Is there a way I can get the -L switch or an equivalent on Ubuntu?

Thanks

---

### Post by HPD2 on 2009-09-23
bump

---

### Post by StuartN on 2009-09-23
> **HPD2 said:**
> bump

Possibly the -L option is omitted by design in Linux because it leaves unsecured access open indefinitely. You would have to script with -l and recall after the connection closes.

---

### Post by HPD2 on 2009-09-23
Would a script be the only way to go about it, and the script would need to be on the linux side correct?

---

### Post by StuartN on 2009-09-25
> **HPD2 said:**
> Would a script be the only way to go about it, and the script would need to be on the linux side correct?

The Windows side already seems to be running as you want it, so you could send stuff to Windows. In Linux there must be many solutions, but a script would work. You could add this as a cron job:

```
if ps | grep nc$; then echo "nc running"; else nc -l >> text.txt;  fi
```

If ps lists a running process ending in nc (**nc$**) then ignore it, else restart nc and add to the end of text.txt file. You would need to run it often enough that the sender didn't timeout, but not so often that you swamp the receiver.

---

