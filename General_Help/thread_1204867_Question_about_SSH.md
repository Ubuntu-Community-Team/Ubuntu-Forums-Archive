---
title: "Question about SSH"
date: 2009-07-05
forum: General Help
---

### Post by mmbathan on 2009-07-05
Hi guys,
 
I creates some tunnels using SSH using spesific ports :
 ssh -D 1080 [EMAIL="user@192.168.137.111"]user@192.168.137.111[/EMAIL]

 
what is the command that can tell me how many SSH tunnel is running?
 
and how can I close the tunnel or tunnels ?
 
Regards,

---

### Post by ju2wheels on 2009-07-05
Im not sure if theres a specific command but this should work out:

```
ps aux | grep ssh
```

That will list all the running ssh clients/tunnels. Then you can just take the process number and kill the process to kill the tunnel.

```
 kill -9 PID 
```

---

### Post by Brandon Williams on 2009-07-05
This command will show you all port numbers being listened to by ssh processing, each of which will represent a local port-forward.
```
$ sudo netstat -lnp | awk '$1 == "tcp" && $7 ~ /\/ssh$/'
tcp        0      0 127.0.0.1:2222          0.0.0.0:*               LISTEN      6140/ssh        
tcp        0      0 127.0.0.1:8080          0.0.0.0:*               LISTEN      6140/ssh        
tcp        0      0 127.0.0.1:3389          0.0.0.0:*               LISTEN      6140/ssh
```

In my example, a single ssh process is listening on ports 2222, 8080, and 3389. If I want to kill the tunnels, the pid of the ssh process is in the last column, which shows pid/program. From this output, I know that 'kill 6140' will kill the tunnel that has those ports open.

---

### Post by mmbathan on 2009-07-05
thank you guys

---

