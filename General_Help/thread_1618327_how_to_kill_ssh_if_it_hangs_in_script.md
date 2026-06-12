---
title: "how to kill ssh if it hangs in script"
date: 2010-11-10
forum: General Help
---

### Post by linuxgr on 2010-11-10
Hey all,

I have placed a script in a machine that automatically creates an ssh tunnel with another machine. Problem is, since I am using dyndns, the ssh command hangs for a LONG time if both machines exist in the same network(@home), because the public IP of pc1 is the same with dyndns of pc2, making a loop.

What I have been trying to to is place an "if" statement to check if ssh is possible (in case server is down or in case the public ip is the same).

If I run the command:
```
ssh user@host 'cat /etc/hostname' & sleep 20
```

it runs fine. But when I put it to a script like this:

```
var=$(ssh user@host 'cat /etc/hostname' & sleep 20)
if [-z var]
exit 1
else
do_other_stuff......
fi
```

it eventually exits but it takes a LONG time as if the sleep is not there...

Am I doing something wrong?

I also tried the ssh option -o ConnectTimeout but it doesn't seem to work either

Thanks

EDIT: I just realized that sleep also gives out an output, which would fill "var" and make it useless... So even if we get it to work, I need to figure out how to run sleep without output

---

