---
title: "NFS mount: bg option?"
date: 2010-04-04
forum: General Help
---

### Post by dvrvm on 2010-04-04
Hi,

I mount a filesystem by NFS, which works fine.

Now I want that mount command to time out after, say, 5 seconds if the server is unavailable, and let the computer continue with booting. The documentation says that the 'bg' option will do this for me: send the process to background if it times out or has an error.

But no matter what combination of options I use for the mount: bg, fg, soft, hard, intr, different values for timeo, different values for retrans, the result is always the same: it waits for an eternity before failing.

Do I misunderstand these options? How can I get this usefully working?

---

### Post by terrrorr on 2010-04-04
Hi

This may sound like a hack, but it works for me. I use bash script witch checks first if target host is up and running and if it is then it continues the mount process.

Just add dynamic link into startup process and it will do same thing automagically  

```


ping -c 1 -t 1 SERVER_IP;

if [ $? -eq 0 ]; then
    MOUNT_COMMAND
else 
    exit
fi

```

Hope this helps

---

