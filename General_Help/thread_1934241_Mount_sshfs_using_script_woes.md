---
title: "Mount sshfs using script woes"
date: 2012-03-01
forum: General Help
---

### Post by cryptotheslow on 2012-03-01
Hi,

No doubt I have missed something obvious here but I can't see what :(

Just trying to remove the need to type a mount command by having it in a script on my desktop.

Client: Ubuntu 12.04 Desktop 64bit
Server: Ubuntu 10.04 Server 64bit

On the client I have created a directory ~/ubuserver_shared

This command:
```
sshfs -o idmap=user $USER@ubuserver:/home/crypto/shared ~/ubuserver_shared
```works fine from the command line. The remote directory gets mounted as expected.

So I created a simple script:
```
#!/bin/bash
sshfs -o idmap=user $USER@ubuserver:/home/crypto/shared ~/ubuserver_shared
```Again this works fine from the command line.

However, when executed from the desktop using "Run in Terminal" the terminal window opens and prompts for the password (as expected) - enter the password and Terminal disappears and a GUI OpenSSH popup prompt appears asking for the password again - enter the password again and that popup disappears but nothing is mounted to ~/ubuserver_shared.

What am I doing wrong here? It seems like the OpenSSH GUI is unnecessarily intervening somehow.

Thanks
crypto

---

### Post by Habitual on 2012-03-02
Make a new launcher with this command property

```
gnome-terminal -e "/path/to/your.sh"
```

your.sh includes:
```

#!/bin/bash
sshfs -o idmap=user $USER@ubuserver:/home/crypto/shared ~/ubuserver_shared

```

HTH.
Others may have a more elegant solution.

---

### Post by matt_symes on 2012-03-02
Hi

What is the value of $USER when run from the script requiring elevated privileges ?

Is it the user you are expecting ?

Use full paths as well (including sshfs).

Kind regards

---

### Post by cryptotheslow on 2012-03-03
OK - still banging my head on this one, but have made minor progress.

As for creating a launcher - that seems nigh on if not actually impossible in 12.04

@matt_symes
The user is being returned correctly and the usernames and UIDs match between systems. The password being prompted for is the SSH password for the server not a sudo / elevation password. I've added full paths in as suggested - but still the same result. However, I added:
```
read -p "Press any key to continue... " -n1 -s
```as the last line of the script so it pauses before finishing. And I find that until I press the any key :D the remote directory is actually mounted and functions fine. As soon as I hit a key, the script finishes and the Terminal window exits - and the remote dir is no longer mounted.

When run from command line I end up with two processes running:
```
 4705 ?        S      0:00 ssh -x -a -oClearAllForwardings=yes -2 crypto@ubuserver -s sftp
 4707 ?        Ssl    0:00 /usr/bin/sshfs -o idmap=user crypto@ubuserver:/home/crypto/shared /home/crypto/ubuserver_shared
```When run from the desktop or Nautilus I end up with four processes until a key is pressed to complete the script:
```
4912 pts/2    Ss+    0:00 /bin/sh -c '/home/crypto/mount_ubuserver_shared.sh'
 4914 pts/2    S+     0:00 /bin/bash /home/crypto/mount_ubuserver_shared.sh
 4921 pts/2    S+     0:00 ssh -x -a -oClearAllForwardings=yes -2 crypto@ubuserver -s sftp
 4925 ?        Ssl    0:00 /usr/bin/sshfs -o idmap=user crypto@ubuserver:/home/crypto/shared /home/crypto/ubuserver_shared
```So it seems the ssh process belongs to the pts/X - so when the Terminal exits it takes the ssh process out with it killing the mount. I'm thinking I need to change my script to background the command - time for some more meddling :D

---

### Post by kevdog on 2012-03-03
I found a page that might help you:

[http://askubuntu.com/questions/5363/how-to-start-a-terminal-with-certain-text-already-input-on-the-command-line](http://askubuntu.com/questions/5363/how-to-start-a-terminal-with-certain-text-already-input-on-the-command-line)

Your problem is definitely one of one the terminal closes, your running processes within the terminal are closed as well.  You need to keep the terminal open if you want the running processes to remain (remember running processes within a terminal are local to the terminal -- not global to the OS -- this means when the terminal is killed, everything running inside the terminal is killed as well).

---

### Post by cryptotheslow on 2012-03-03
Thanks kevdog

I have given up with that approach now (tried backgrounding the command in the script - but of course that means I don't see the password prompt!) and added it to the fstab instead.

Useful refs:
SSH Mount In fstab: [http://ubuntuforums.org/showthread.php?t=1173714](http://ubuntuforums.org/showthread.php?t=1173714)
Make umount work with sshfs: [http://www.unicom.com/blog/entry/651](http://www.unicom.com/blog/entry/651)

Now it is mountable / umountable from both Nautilus and command line - good enough for me :D

---

