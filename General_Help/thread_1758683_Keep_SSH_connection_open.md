---
title: "Keep SSH connection open"
date: 2011-05-14
forum: General Help
---

### Post by dmillerw on 2011-05-14
I've got two computers running Ubuntu, and on one, a basic script that (through SSH) sends a command to the other.

Problem is, it has to re-connect every time, so that adds some delay.

Any way to keep the connection open?

---

### Post by jerenept on 2011-05-15
None that I know of, but Telnet is usually considered faster than SSH because it doesn't have encryption.

---

### Post by Lars Noodén on 2011-05-15
> **dmillerw said:**
> Any way to keep the connection open?

Try **ssh -f** or make use of "[ServerAliveCountMax](http://manpages.ubuntu.com/manpages/natty/en/man5/ssh_config.5.html)" with "ServerAliveInterval" in **ssh_config**.

---

### Post by HermanAB on 2011-05-15
If your problem is that SSH fails after a while, the problem is due to a bad LAN switch somewhere.  If you want to keep a running SSH session going after logging off, use nohup or screen.

---

### Post by Lars Noodén on 2011-05-15
You can [multiplex](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Multiplexing) additional connections over the same TCP/IP connection.  That will save startup time.  Just use the options in the previous post to keep one Master connection open all the time.

---

### Post by dmillerw on 2011-05-15
Maybe it'd help if I explained it better.

On CompB I have a launcher which runs the command```
ssh -X dylan@192.168.0.106 "./test"
```

where test is
```
export DISPLAY=:0
zenity --info --title "Mom" --text "Mom needs help!!!"
```

Now, the SSH connection will close every time once the script is executed. So is there anyway to keep it open, making the launcher immediately send the command to run "test"?

---

