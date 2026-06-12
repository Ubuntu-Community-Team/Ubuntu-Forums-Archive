---
title: "Does an rsync transfer require rsync on both machines?"
date: 2012-08-13
forum: General Help
---

### Post by Splooshie123 on 2012-08-13
Does an rsync transfer require the rsync program to be installed on both the local and the remote computers?

---

### Post by drmrgd on 2012-08-13
No, it's only required on the computer executing the rsync.  However,  I believe most Linux distributions come with it built in anyway.  So unless you're copying from a Windows drive, you should be covered I would imagine.

---

### Post by Splooshie123 on 2012-08-13
Thanks

---

### Post by kurt18947 on 2012-08-13
If you're not real comfortable in CLI, You could try Luckybackup in the repositories.  It's a GUI frontend for rsync that seems pretty capable and simple to use.   It also has a synch function which can be pretty useful for keeping folders synched.  Plug in a USB drive, it takes a few seconds to sync the day's work to a removable drive.

---

### Post by asmoore82 on 2012-08-13
Actually, **Yes**! The rsync binary is required on each end of the transfer to perform the rsync algorithm. I'm not sure if there is some sort of fallback mode or not, but I logged into a test server and did this:

```
[COLOR="Red"]#do not run, for testing only
sudo chmod -x /usr/bin/rsync[/COLOR]
```

After that, attempting to rsync with that machine on the remote end caused this error:
```
bash: /usr/bin/rsync: Permission denied
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: remote command could not be run (code 126) at io.c(601) [Receiver=3.0.7]
```

I also tried renaming the remote rsync binary, it caused this similar error:
```
bash: rsync: command not found
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: remote command not found (code 127) at io.c(601) [Receiver=3.0.7]
```

---

### Post by HermanAB on 2012-08-13
Yup, rsync is required on both ends if you run it over a transport protocol such as ssh.

---

### Post by Slim Odds on 2012-08-13
> **HermanAB said:**
> Yup, rsync is required on both ends if you run it over a transport protocol such as ssh.
Indeed, **any protocol** needs support by both transmitter and receiver. That's how any communication works.

---

