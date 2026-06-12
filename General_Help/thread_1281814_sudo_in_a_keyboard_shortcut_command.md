---
title: "sudo in a keyboard shortcut command"
date: 2009-10-03
forum: General Help
---

### Post by Dr Belka on 2009-10-03
So I want to kill the Network Manager Process with the click of a key.  

I wrote this line and assigned it to a keyboard shortcut

NM=`ps -e | grep NetworkManager | sed 's/ \([0-9]*\).*/\1/g'` ; sudo kill $NM

When run in the terminal, it asks for my password, of course, but it will not work at all as a keyboard shortcut.  Is there anyway to feed my password to the prompt or any other way around this?

---

### Post by scragar on 2009-10-03
```
gksu killall NetworkManager
```:p

---

### Post by Dr Belka on 2009-10-03
wow, that works perfectly, but still asks for a password.  I will use this if nothing else works.  Thank you.

Still, is there any way I could add my password to the script to feed it into the password prompt?

---

### Post by pickarooney on 2009-10-03
If you edit the **/etc/sudoers** file with the command **visudo** there's a way of allowing normal users to run specific commands without requiring the **su** password. I don't know the syntax off-hand but it shouldn't be too hard to figured out.

---

### Post by scragar on 2009-10-03
> **Dr Belka said:**
> wow, that works perfectly, but still asks for a password.  I will use this if nothing else works.  Thank you.

Still, is there any way I could add my password to the script to feed it into the password prompt?

Probably not the best idea, but you can edit the sudoers file in /etc to give yourself perms to do this without needing the password, although I recommend against it for security reasons.
```
sudo -i
echo "$USER           ALL = NOPASSWD: /usr/bin/killall" >> /etc/sudoers
exit
```

---

### Post by scragar on 2009-10-03
> **pickarooney said:**
> If you edit the **/etc/sudoers** file with the command **visudo** there's a way of allowing normal users to run specific commands without requiring the **su** password. I don't know the syntax off-hand but it shouldn't be too hard to figured out.

The sudoers file is actually rather hard to figure out at first, there are examples that make it easier, but without a guiding hand you are still pretty likely to mess up what goes where.

---

### Post by Dr Belka on 2009-10-04
> **scragar said:**
> Probably not the best idea, but you can edit the sudoers file in /etc to give yourself perms to do this without needing the password, although I recommend against it for security reasons.
```
sudo -i
echo "$USER           ALL = NOPASSWD: /usr/bin/killall" >> /etc/sudoers
exit
```

This addition to the sudoers file did not enable me to use the killall command without a password

I also tried these edits:

```
# Cmnd alias specification (this is an existing line)
Cmnd_Alias KILL_CMDS = /bin/kill, /usr/bin/killall

....

# Members of the admin group may gain root privileges (also an existing line)
%admin ALL=(ALL) ALL

william ALL=(ALL) NOPASSWD: KILL_CMDS
```

---

### Post by Dr Belka on 2009-10-04
bump

---

